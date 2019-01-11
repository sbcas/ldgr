---
title: "State of the Kitchen: 8th Edition"
date: 2018-12-31T07:53:05-08:00
tags:
 - openstack
 - chef
categories: ["openstack"]
cover: /img/os_chef_logo.jpg
draft: false
---
It has been some time since the last State of the Kitchen. Since the release of
Chef OpenStack 17 (Queens), we have been operating in a minimal churn mode to
give people time to test/upgrade deployments and handle any bugs that came up.

There are three main areas that are still in progress upstream from Chef
OpenStack, but can affect its cadence regardless. As a result, this update
focuses more on those areas. Consider this more of a year-end review.

### Important Happenings

* *fog-openstack*[^1]

  Beginning in August, we started receiving reports of breakage due to changes
  in fog-core. As a reactionary measure, we implemented upper-level constraints
  in the client resource cookbook to maintain a consistent outcome.

  The fog-openstack library has continued to receive changes to further align
  with fog-core, and we are following its progress to find a good time to move
  ChefDK and Chef OpenStack to a post-1.0 release of fog-openstack.

  We are targeting the 18th release of Chef OpenStack, due to Keystone endpoint
  changes that need to happen.

* *Sous Chefs*[^2]

  One of the biggest strengths of Chef and OpenStack is the collective outcome
  of their unique communities. Within the Chef ecosystem, the Sous Chefs group
  was formed in response to a need for the continued existence of cookbooks
  that need a long-term home.

  Across the globe, Sous Chefs work to keep some of the most heavily used
  cookbooks in existence, such as
  [apache2](https://supermarket.chef.io/cookbooks/apache2),
  [mysql](https://supermarket.chef.io/cookbooks/mysql) (and
  [mariadb](https://supermarket.chef.io/cookbooks/mariadb)!),
  [postgresql](https://supermarket.chef.io/cookbooks/postgresql), as well as
  [redisio](https://supermarket.chef.io/cookbooks/redisio), and many more. Chef
  OpenStack depends on MariaDB, Apache, and their related cookbooks, for
  compatibility without operators needing to plumb those resources internally.

* *poise-python*[^3]

  In early October, pip 18.1 was released, which made some additional waves in
  the ecosystem. Workarounds were devised and implemented to limit the fallout.
  Currently, the fix has been merged to poise-python's master, but cannot be
  released safely due to CI changes in the current workflow.
  
  There are limitations on what the Sous Chefs can reasonably maintain. The
  maintenance of poise is rather beyond that boundary, not to discount or
  disparage anyone involved. Anyone interested with spare cycles over the
  holiday season might consider joining the conversation.

### Upcoming Changes

* In Chef OpenStack 18...

  - MariaDB's version will default to 10.3, consistent with the default in the
    2.0 version of the cookbook, so plan accordingly
  - Keystone's endpoint will be changing to drop the hardcoded API version
  - the cloud primitives (client) cookbook is in the process of migrating from
    cookbook-openstackclient to cookbook-openstack-client (named
    openstack_client, to conform with current best practices in the Chef community)
  - Ubuntu will be upgraded from 16.04 to 18.04, and as such we will be gating
    against Bionic at that time -- previous Chef OpenStack releases will not be
    moving to Bionic jobs, and will continue to work at best effort until they
    succumb to the detritus of time.

### Meetings

Since the Summit, a few people have reached out through various means about
Chef OpenStack and how to work together to improve the outcome. As a result, I
would like to propose holding regular meetings for Chef OpenStack once more set
aside a dedicated period where we can come together and talk about food, or
other things.

We have the IRC channel, but IRC has proven less effective for a small group to
dedicate time consistently, so I would something more high bandwidth for
technical conversations, such as video with a publicized method for joining and
viewing. I will follow up with a more expanded proposal outside this update.

### On The Menu

This would not be a State of the Kitchen without something to eat.  My partner
and I try to cook with recipes that are not overly complicated, but can be
infinitely complex with just the right nudge. Sometimes we incorporate our own
opinions into someone else's recipe to make it our own thing, and sometimes
they're great just as they come.

*Dat Dough, Doe*

* 170g / 6oz grated mozzarella or Edam, or another mild cheese with similar
  melting consistency
* 85g / 3oz almond meal/flour
* 28g / 2 tbsp cream cheese or Neufchatel
* 1 egg
* pinch of salt to taste

1. Mix the shredded/grated cheese and the almond meal in a microwaveable bowl,
   then add the cream cheese. Microwave on high for 1 minute. Stir the mixture,
   then microwave on high for another 30 seconds.
1. Add egg, salt, additional spices or flavorings, and mix or fold gently.
1. Shape using parchment paper into the desired outcome, be it flat like a disc
   or rounded like a boule.
1. Create vents to ensure that the finished product cooks evenly.
1. Fry, bake, broil or grill as desired. Lipids can be friends here.

More commonly known as the "Fat Head" dough, out of these few ingredients, one
can make food that can taste every bit like pizza, pasta, bread, even pão de
queijo.

Or, perhaps, cinnamon rolls, or danishes, as one might consider making.

With these basic recommendations, one can apply their own opinions and set of
requirements to create complex pieces of work, which can taste every bit like
an artform and a science.

See you in 2019!

Your humble pastry chef,

-sc

[^1]: https://github.com/fog/fog-openstack/issues/434
[^2]: https://sous-chefs.org/
[^3]: https://github.com/poise/poise-python/issues/133
