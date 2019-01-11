---
title: "Kubernetes 1.10 on Raspberry Pi"
date: 2018-08-08T21:48:34-07:00
description: ""
category: blog
tags:
- kubernetes
categories:
- kubernetes
cover: /img/kubernetes_logo.jpg
draft: false
---
All your friends are talking about it, all the recruiters are wanting
it. Kubernetes is definitely taking the tech world by storm, and
dragging everyone along for the ride. This post serves to show what
worked for me, while reusing methods from other people's efforts.<!--more-->

### Pre-Fetching

Before you dive right in, you want to read some posts from some of other
efforts where they built their clusters:
* [Kubernetes 1.9 on a Raspberry Pi Cluster](https://harthoover.com/kubernetes-1.9-on-a-raspberry-pi-cluster/) by Hart Hoover
* [OpenFaaS on Kubernetes on Raspberry-Pi](http://blog.codybunch.com/2018/01/05/OpenFaaS-on-Kubernetes-on-Raspberry-Pi/) by Cody Bunch
* [My Raspberry Pi Kubernetes Cluster](https://chrisshort.net/my-raspberry-pi-kubernetes-cluster/) by Chris Short
* [How to Build a Kubernetes Cluster with ARM Raspberry Pi then run .NET Core on OpenFaas](https://www.hanselman.com/blog/HowToBuildAKubernetesClusterWithARMRaspberryPiThenRunNETCoreOnOpenFaas.aspx) by Scott Hanselman

These links will help plan out the hardware purchase, to get an idea of
how much you want to spend on a totally new build. If you have a stack
of RPi boards with nothing to do, this isn't the worst project.

> Forget everything you think you know.

Okay, that's a stretch. What you just read most definitely will not work
out of the box. And that's okay! Kubernetes is moving at such a speed
that even this post will likely be out of date by the next minor
release. When that happens, this post won't be replicable 100%, and
that's the fun of working in a fast moving area.

The challenge I took upon myself was to attempt to replicate Hart's
configuration, but use wireless for the whole thing. I wanted to keep
the stack on my desk, without running cable just for this exercise.

### Customizing the image

First of all, Raspberry Pis have this fun quirk where the uart and the
wireless use the same pin. The fun here is that your pistack will
randomly drop wireless because... hashtag random.

The files I used for customizing my image are
[here](https://gist.github.com/scassiba/677625f5714142d8c9f3d229850031df).
Place them in the copy of the `packer-builder-arm-image` you cloned
earlier. This is shared to `/vagrant/` within the VM by default.

### Doing the thing

On my haggard, 2012 vintage MacBook, I used Packer to create the ARM64
image and wrote to the SD cards using a `for` loop. After some trial and
error with Hypriot's `flash` utility, I was able to get a working image
written.

My method was slightly different, because I'm using the wireless module.

```
for i in {1..6};do flash --hostname node-0$i --userdata ./user-data.yml \
--bootconf ./config.txt ./raspbian-stretch-modified.img;done
```

### Automating the stack

Much like Hart, and Chris before him, I opted to use Ansible. Sure I
could futz around with chef-client for arm64 and probably get somewhere,
too. This was my excuse to actually hack around with Ansible for more
than orchestration and OpenStack integration jobs.

Unsurprising, I used [rak8s](https://github.com/rak8s/rak8s) as my basis
for automating the pistack. Also, without surprise, running it out of
the box did not work. At the velocity Kubernetes' ecosystem moves,
related blog posts are the new tech manuals, outdated by the time they
reach the masses.

### What changed?

First, we need to align Kubernetes with a version of Docker that does
not complain about being used. Kubernetes will complain about docker
18.06, which is the latest, but is quite happy with 17.09. This is the
case from 1.9 to 1.10, though I'm sure someone more cavalier can
shoehorn it into working.

Since I'm using Ansible 2.6, things are a bit different than what you'll
find upstream. The `when` guard only worked in the abbreviated syntax.
For populating `/etc/hosts`, rather than relying on it being configured
at the image, we'll make Ansible do that work.

The common role is where most of that effort revolved:

```
diff --git a/roles/common/tasks/main.yml b/roles/common/tasks/main.yml
index 35e53c7..150010d 100644
--- a/roles/common/tasks/main.yml
+++ b/roles/common/tasks/main.yml
@@ -1,18 +1,34 @@
 ---
+- name: Wait for automatic system updates
+  shell: while sudo fuser /var/lib/dpkg/lock >/dev/null 2>&1; do sleep; done;
+
 - name: Ensure hostname set
   hostname: name={{ inventory_hostname }}
   when: not inventory_hostname is match('(\d{1,3}\.){3}\d{1,3}')
   register: hostname
   tags: hostname

-- name: Ensure hostname is in /etc/hosts
+- name: Build hosts file
   lineinfile:
     dest=/etc/hosts
-    regexp="^{{ ansible_default_ipv4.address }}.+$"
-    line="{{ ansible_default_ipv4.address }} {{ ansible_fqdn }} {{ ansible_hostname }}"
+    regexp='.*{{ item }}$'
+    line='{{ hostvars[item].ansible_default_ipv4.address }} {{item}}'
+    state=present
+  when: hostvars[item].ansible_default_ipv4.address is defined
+  with_items: "{{ groups['all'] }}"
   register: hostname
   tags: hostname

+- name: Add an apt key-1
+  apt_key:
+    keyserver: keyserver.ubuntu.com
+    id: 8B48AD6246925553
+
+- name: Add an apt key-2
+  apt_key:
+    keyserver: keyserver.ubuntu.com
+    id: 9D6D8F6BC857C906
+
 - name: Enabling cgroup options at boot
   copy:
     src: cmdline.txt
@@ -24,6 +40,11 @@
   tags:
     - boot

+- name: Enable br_netfilter
+  modprobe:
+    name: br_netfilter
+    state: present
+
 - name: apt-get update
   apt:
     update_cache=yes
@@ -36,24 +57,23 @@
     upgrade=full

 - name: Reboot
-  shell: sleep 2 && shutdown -r now "Ansible Reboot for /boot/cmdline.txt Change"
+  shell: "sleep 2 && shutdown -r now"
   async: 1
   poll: 0
   ignore_errors: True
-  when: cmdline or hostname is changed
+  when: cmdline.changed
   tags:
     - boot
     - shutdown

 - name: Wait for Reboot
-  local_action: wait_for
-  args:
-    host: "{{ inventory_hostname }}"
-    port: 22
-    delay: 20
-    timeout: 180
+  wait_for_connection:
+    connect_timeout: 20
+    sleep: 5
+    delay: 5
+    timeout: 300
   become: False
-  when: cmdline or hostname is changed
+  when: cmdline.changed
   tags:
     - boot
     - shutdown
```

I have made a fork with my own modifications and published it
[here](https://github.com/scassiba/rak8s). If you just want to skip
ahead and get cracking, start there.

Once I made these changes, Ansible was all happy, and we have a cluster.

### What happens now?

Now that I have an initial installation of Kubernetes out of the way, it's time to run
stretch the legs on this thing to run some services. Chances are it will
be broken most of the time, and that's perfectly fine.
