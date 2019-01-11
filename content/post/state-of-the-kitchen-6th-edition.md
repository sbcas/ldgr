---
title: "State of the Kitchen: 6th Edition"
date: 2018-08-07T20:46:09-07:00
description: ""
tags:
- chef
- openstack
categories: ["openstack"]
cover: /img/os_chef_logo.jpg
draft: false
---
This is the sixth installment of what is going on with Chef OpenStack.
The goal is to give a quick overview to see our progress and what is on
the menu. Feedback is always welcome on the content and of what you would
like to see more.

<!--more-->

### Notable Changes

* In the past month we released Chef OpenStack 17, which aligns with the
  Queens codename of OpenStack. Stabilization efforts
  centered largely around Chef major version updates and further
  leveraging Kitchen for integration testing. At the time of this
  writing, they are mirrored to GitHub and
  [Supermarket](https://supermarket.chef.io/users/openstack){:target="_blank"}.
* openstack-attic/openstack-chef has been brought back from the aether to
  [openstack/openstack-chef](https://git.openstack.org/cgit/openstack/openstack-chef){:target="_blank"}.
  This is now the starting point for Chef OpenStack integration examples
  and documentation. Many thanks to infra for the smooth de-mothballing.
  A special thanks to fungi for putting on his decoder ring on
  a weekend!
* The openstack-dns (Designate) and overcloud primitives (client)
  cookbooks have been rehomed to the openstack/ namespace, donated by
  jklare, calbers and frickler. (thanks!)
* Support for aodh has been added to the telemetry cookbook. Thanks to
  Seb-Solon for the patches!

### Integration

* Containerization is progressing, but decisions of old are starting to
  need to be revisited. Networking is where the main area of focus needs
  to happen.
* In past releases, Chef OpenStack pared down the integration testing to
  facilitate in landing changes without clogging Zuul. With Zuul v3,
  that allows some of the older methods to be replaced with lighter
  weight playbooks. No doubt, as tests become reimplemented, the impact
  to the build queue times will have to be a consideration again.

### Stabilization

* With Rocky stable packages nearing GA, this means that the cookbooks
  will start focusing on stabilization in earnest. More to come.
* The mariadb 2.0 rewrite has not been released upstream in Sous Chefs.
  We are collaborating to test it in the Chef OpenStack framework and
  make a decision on when to release to Supermarket. The major change
  here is making it a pure set of resources, replacing the now-defunct
  database cookbook.

### On The Menu

*Slow Cooker Pulled Pork*
* 1 pork butt (shoulder cut) -- size matters not here, the same liquid
  measurements go for an average size as well as a large size
* Cookin' Sause (see below)
* 1 cup (240mL) cider vinegar
* 1 cup (240mL) beef stock (water works, too, but we like the flavor)
* 1-2 tsp (5-10mL) liquid smoke

#### Cookin' Sause
* 1 cup (340g) yellow mustard
* 1/4 cup (57g) salt
* 1/4 cup (57g) ground black pepper
* 1/4 cup (57g) granulated garlic
* 1/4 cup (57g) granulated onion
* 1/4 cup (57g) ground cayenne

> Combine the spices and the mustard with a whisk. You can use the fancy
stuff here, but it's kind of a waste. Ol' Yella works just fine.
Your food, your call.

#### Dippin' Sause -- not cookin' sause!

* 1 can tomato paste
* Cider vinegar
* Red pepper flakes

> There are no measurements on this because it's subjective. Trust your
senses and err on the side of needing to add more.

*to business!*

1. Rub pork butt with cookin' sause. Make that swine sublime.
1. Place that yellow mass of meat in your slow cooker
1. Add cider vinegar, stock, liquid smoke
1. Cook for 7.5-8 hours on low, until fork tender
1. Shred with forks until it doesn't look like mustard
1. Serve with dippin' sause, or use it as drownin' sause
1. Enjoy
