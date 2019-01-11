---
title: "State of the Kitchen: 7th Edition"
date: 2018-09-04T19:34:33-07:00
tags:
- chef
- openstack
categories: ["openstack"]
cover: /img/os_chef_logo.jpg
draft: false
---
This is the seventh installment of what is going on with Chef OpenStack.
The goal is to give a quick overview to see our progress and what is on
the menu. Feedback is always welcome on the content and of what you would
like to see more.

<!--more-->

### Notable Changes
* Ironic is returning to
  [active development](https://review.openstack.org/#/q/topic:refactor-ironic-cookbook).
  This is currently targeting Rocky, but it will be backported as much
  as automated testing will allow. The cookbook currently works through
  to Tempest and InSpec, but resource constraints prohibit a more
  comprehensive test.
* Chef OpenStack is on
  [docs.o.o](https://docs.openstack.org/openstack-chef/latest/)! It
  currently covers the Kitchen scenario, and needs more fleshed out. A
  more comprehensive deploy guide is in the making.
* Sous Chefs released v5.2.1 of the
  [apache2](https://supermarket.chef.io/cookbooks/apache2) cookbook
  today. This will alleviate an issue with ports.conf conflicting
  between cookbook and package.
* openstack/openstack-chef-repo has served us for many years, but
  nothing is an unmoving mover. Development has shifted over to
  openstack/openstack-chef and openstack-chef-repo will be ferried to the
  great bit bucket in the cloud.
  [o7](https://review.openstack.org/#/q/topic:retire-openstack-chef-repo)

### Integration
* With the aforementioned repo retirement, integration has shifted to
  openstack/openstack-chef.
* Docker stabilization efforts are looking good to introduce a
  containerized integration job for CentOS. Ubuntu still does not play
  nicely using Docker through Kitchen. This will result in gating jobs
  using both the Zuul-provided machine, as well as Docker. The focus is
  AIO at this time.

### Stabilization
* fog-openstack 0.2 has been released, which makes a major change to
  how Keystone endpoints are handled. This is in anticipation for
  dropping a hard version string for Identity API versions.
  0.2.1 has been released to [rubygems](https://rubygems.org/gems/fog-openstack),
  which will resolve the issues 0.2.0 exposed. For now, however, the
  client cookbook has been constrained to match ChefDK. The target for
  ChefDK to support fog-openstack 0.2 is, at this point, the unreleased
  ChefDK 3.3.0.
  [Further context.](http://lists.openstack.org/pipermail/openstack-dev/2018-September/134185.html)

### On The Menu
*The Perfect (Indoor) Steak*
* Kosher salt
* Black pepper
* 1 tbsp (15 ml) olive oil
* 1 (8 to 12 ounce) boneless tenderloin, ribeye or strip steak

1. Set your immersion cooker to 130F (54.4C) -- y'all have one of these,
   right?
1. Generously season both sides with salt and pepper.
1. Place the steak in a medium zipper, or vacuum seal, bag. Seal with a
   vacuum sealer, or using the water immersion technique.
1. Place the bag in the water bath, and set the timer for 2 hours. This
   comes out to about medium-rare consistency.
1. After 2 hours, remove the steak from the water bath and pat very dry
   with paper towels.
1. Heat oil in a medium cast iron skillet over high heat until it
   shimmers.
1. Add steak and sear until well-browned, about 30 seconds per side.
1. Let rest for 5 minutes.
1. Enjoy.
