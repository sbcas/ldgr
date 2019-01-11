---
title: "State of the Kitchen: 4th Edition"
date: 2018-05-27T09:31:43-07:00
description: ""
tags:
- chef
- openstack
categories: ["openstack"]
cover: /img/os_chef_logo.jpg
draft: false
---
This is the fourth installment of what is going on with Chef OpenStack. The aim
is to give a quick overview to see our progress and what is on the menu.
Feedback is always welcome on the efficacy of the content.

This edition will take a slightly different direction, as I am now cross-posting
this to my personal website. The upshot is that, going forward, these posts are
now in Markdown format.

### Announcements

* Queens release is nearing. Summit week slowed things down a little, but we're
  looking to be in good shape.
* Kitchen scenarios are now pinned to Chef 14. While Chef 13 is supported until
  Chef 15 release, master is not currently testing against it. All changes are
  currently still gated against Chef 13.
* ChefDK 3 has been released. Testing has not commenced with it, but patches are
  always welcome if you're impatient.

### Documentation

* Basic contributor and install guides have been written to replace the
  ever-aging documentation in openstack-chef-repo.
* A more comprehensive deploy guide is beginning to take shape.

### Integration

* The mass deprecation of Rakefiles is still looking to be possible. The
  functionality from openstack-chef-repo/Rakefile will have to be retrofitted
  into Zuul jobs to get gating jobs for the supported platforms.
* Chef Delivery support has made it to the cookbooks. It is currently used in
  local testing, but will be making it to the gate soon.

### Containers

* Dokken works-ish. Yes, ish. Though, not for lack of trying. RDO has issues in
  networking due to iptables.
* All-in-one is the current focus, with clean builds using UCA packages.

### Upgrades

* No updates this month.

### On The Menu

*Chicken Cordon Bleu Casserole* (makes 8-10 portions)

* 1500g chicken, cubed in 1" pieces
* 300g ham steak, cubed in 0.5" pieces
* 300g Swiss cheese
* 230ml Heavy Whipping Cream
* 230ml cream cheese / Neufchatel
* To taste: salt, pepper, garlic powder

#### Instructions

1. Cook chicken most of the way through so it isn't tough and rubbery. A little
   pink here is a good thing - it will finish in the oven.
1. Line the bottom of the pan with chicken cubes
1. Sprinkle salt, pepper and garlic powder (sorry non-US folks) over the chicken
1. Sprinkle ham cubes on top of the chicken
1. Shred Swiss cheese and spread over the mixture
1. Heat the cream cheese in the microwave, add the cream and mix. Pour mixture
   over the casserole.
1. Mix ingredients until incorporated. Overmixing will give a more pate-like
   texture.
1. Bake @ 350F / 176C for 40 minutes.
