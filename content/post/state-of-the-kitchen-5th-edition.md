---
title: "State of the Kitchen: 5th Edition"
date: 2018-07-03T11:10:37-0700
tags:
- chef
- openstack
categories: ["openstack"]
cover: /img/os_chef_logo.jpg
draft: false
---
This is the fifth installment of what is going on with Chef OpenStack. The aim
is to give a quick overview to see our progress and what is on the menu.
Feedback is always welcome on the content and what you'd like to see.

<!--more-->

Last month's edition was rather delayed due to an emergency surgery on one of
my cats (he's doing fine) but other things took priority. Going forward, I'm
going to stick as close to to the beginning of the month as I can.

This will be a thin installment, as there were only a few things of note.

### Notable Changes
* Nova APIs are now WSGI services handled by Apache.
  <https://review.openstack.org/575785>
* Keystone has been reduced down to a single 'public' endpoint.
  <https://review.openstack.org/#/q/topic:bp/simplify-identity-endpoint>

### Integration
* Dokken works on both platforms with an ugly workaround. Presently, this
  results in allinone scenarios converging and testing inside a container.
  <https://review.openstack.org/577814>

### Upcoming
* Testing against RDO Rocky packages works. More to come, probably in a blog
  post.
* Ubuntu 18.04 results in a mostly functional OpenStack instance, but it bumps
  into Python 3 problems along the way.
* The mariadb cookbook has undergone a significant refactor resulting in a
  2.0.0, but might not be updated until the focus switches to Rocky.

### On The Menu
*Not Really "Instant" Roast Beast* (makes 4 servings, 2 if you're hungry)

* 3 lbs / 1.3 kg bottom round beef roast, frozen to aid tenderizing
* 3 cups / 700ml beef stock
* 1 medium onion, sliced
* 1 tsp / 4.2g minced garlic
* Ground cayenne, granulated onion and garlic to taste.

1. Add a layer of sliced onions to the bottom of your electric pressure cooker
   (you DO have one, right?)
1. Add frozen(!) meat on top of the onions.
1. Add garlic, remaining onion pieces and powdered spices to the cooker.
   Do NOT add salt at this stage, as tempting as it may be.
1. Cook at medium pressure for 90 minutes. Allow for the pressure to reduce
   naturally. It can take an additional 30 minutes or more. Patience is
   rewarded.
1. Remove roast to a large dish, shred until it's to your preferred consistency.
   Optionally, remove the onion pieces, they've given their all.
1. Add xanthan gum or your preferred choice of thickener. Use cornstarch or flour
   if you're not super carb-conscious. Hit it with the immersion blender.
1. Return shredded meat to what could be misconstrued as gravy. Salt to taste
   and dig in. It gets better if you leave it overnight in the fridge to
   allow the flavors to redistribute.

