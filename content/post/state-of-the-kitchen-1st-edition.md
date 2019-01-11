---
title: "State of the Kitchen: 1st Edition"
date: 2018-02-16T13:10:16-08:00
tags: 
- chef
- openstack
categories: ["openstack"]
cover: /img/os_chef_logo.jpg
draft: false
---
This is the first edition of what is going on in Chef OpenStack. The
goal is to give a quick overview to see our progress and what is on
the menu.<!--more-->

### Appetizers
* Focus is on branching stable/pike and releasing Pike to Supermarket
before the end of February if possible.
* Tempest will continue to focus on deploying from git instead of
packages. This provides a more consistent outcome.
* Designate cookbook works with Pike and Queens in Ubuntu. CentOS is WIP.
* A deploy guide on using Chef OpenStack in various scenarios is
being formulated. Any help here is welcome, even a rubber duck.

### Entrees
* Chef 13 has landed in master (encompassing a staggering 2+ years of
deprecations)  https://review.openstack.org/#/q/topic:bp/modern-chef
* Test Kitchen is in openstack-chef, with allinone, basic
multinode and container-based scenarios.
* https://git.openstack.org/cgit/openstack/openstack-chef/
* MariaDB is being sourced from mariadb.org for consistency in outcome.

### Desserts
* Rakefiles are going away in favor of delivery local in Queens.
* https://docs.chef.io/delivery_cli.html
* Test Kitchen will become the focal point of CI, once we get the
right power adapter for Ansible.
* Upgrades! Upgr... you get the idea. :-)

### What's Cooking?
*A Bowl of Red*
measurements are geared for Americans, metric is approximate. adjust
where appropriate.
* 4 lbs (1800 g) coarse ground beef
* 1/4 cup (60 ml) beef stock for added flavor and moisture
* 1 oz (28 g) chili powder (without salt, to control salinity)
* 4 or 5 chipotle chiles, minced, with adobo sauce, to taste
* 1 29 oz can (857 ml) of tomato sauce
* 1 tsp (4.7 g) each: kosher salt, ground black and white peppercorns
* 1 tbsp (14.3 g) each:
* onion powder
* paprika
* ground cumin
* ground cayenne
* ground jalapeño
* 1 box baby wipes, any brand

1. Add ingredients to slowcooker, breaking up the meat as you add it.
1. Cook on high for 4 hours, or until the aroma of cumin takes you.
1. Serve straight up, or with shredded cheese and sour cream to tame the heat.
1. Apply baby wipes when appropriate.

*Gets hotter overnight.*
