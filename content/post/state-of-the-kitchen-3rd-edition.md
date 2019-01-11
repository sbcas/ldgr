---
title: "State of the Kitchen: 3rd Edition"
date: 2018-04-20T08:10:38-07:00
description: ""
tags:
- chef
- openstack
categories: ["openstack"]
cover: /img/os_chef_logo.jpg
draft: false
---
This is the third installment of what is going on in Chef OpenStack. The goal is to give a quick overview to see our progress and what is on the menu. Feedback is always welcome on the usefulness of the content.<!--more-->

### Appetizers
* Chef 14 support has arrived in the cookbooks. Test Kitchen will be updated to 14 Soon(tm). The gate is still testing against 13. The 12 release is considered EOL as of May 1, 2018, so we will not be able to support releases older than 13 at that time. https://blog.chef.io/2018/04/19/whats-new-in-chef-14-and-chefdk-3/
* Numerous community cookbooks received updates, the highest visibility being Poise itself. This resolves issues with installing pip 10 on both platforms, and system Python on RHEL.

### Entrees
* Installing Python has been centralized to the common cookbook, as opposed to multiple attempts to install the same Python instance. This produces a more consistent, repeatable outcome.
* The dokken yaml has been fixed up to allow for testing in containers once more.
* Work has begun on overhauling the aging documentation, in an attempt to align things closer to community standards. Parts are shamelessly inspired from other projects (Puppet OpenStack, OpenStack-Ansible), so it will look a bit familiar in some places.

### Desserts
* Rakefiles are going away! As tooling has matured, and the emergence of the ChefDK, the functionality of what the reliable Rakefiles provide are being replaced with tools such as Test Kitchen and Delivery.

### On The Menu
*Creamy Jalapeno Sauce*
* 1 cup (170g) sour cream / creme fraiche
* 1 cup (170g) mayonnaise
* 5 tbsp (75g) dry Ranch dressing powder
* 2 tbsp (28g) dry Jalapeno powder
* 4-5 pickled jalapeno chiles, with the stem removed (use some of the pickling juice to thin things out if the consistency is too thick)
* 1/2 cup (64g) fresh picked cilantro (dry works here, but... dry)
* 1/2 cup (64g) salsa verde
* 2 tbsp (28g) lime juice
* (Optional) Heavy cream / double cream if the consistency is too thin

1. Add ingredients to a blender or food processor.
1. Blend until desired consistency, or until you do not see pieces of jalapeno.
