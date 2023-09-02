---
title: Regarding foo_openmpt fork and the new foo_openmpt54
author: Chris
date: 2018-01-29T01:55:26+00:00
categories:
  - Uncategorized
tags:
  - foobar2000

---
It was never my intention to force users of the official libopenmpt component for foobar2000 to update to development state code. My intention was to bring a working product to users, and contribute any changes I may have to the OpenMPT library, or its components, back upstream as is possible.
<!-- more -->

  
I am not used to having to ask developers for permission to use their libraries, and the license for this particular library is MIT/BSD compatible, one of my favorite licenses to use for my own code, so it was not necessary for me to immediately publish my work, especially as I was not yet ready to push my own repository changes to the public eye.
  
Currently, my entire work tree is somewhat of a mess. It&#8217;s unpublished code everywhere, changes made to update everything to building with MSVC 2017 targeting Windows XP, with workarounds for bugs in the optimizer of the new compiler. I still haven&#8217;t finished updating all of my components to the new SDK, which involves little more than a rebuild for some of them, while all input components need at the very least to derive from the input_stubs class, and gain new name, GUID, and optionally preferences page GUID. For convenience, I have been naming the input after the preferences page, then changing the preferences page to retrieve its name and GUID from the input&#8217;s static functions.
  
Know this: I will make the Git repository of my foo_openmpt fork much easier to access, as a real repository, and will be sidegrading to the latest stable release of libopenmpt, and force deprecating all 0.40-pre.* versions. I will still maintain a &#8220;+N&#8221; moniker for any subsequent updates against a particular version of the OpenMPT library, to denote incremental changes against a previous component release.
  
I wish to apologize to the developers of the OpenMPT project, whose very active development has been carefully controlled over the years to bring their users the very best possible work, without releasing code that wasn&#8217;t ready for general consumption. I hurt their image by releasing unfinished code, and also made the entire foobar2000 component reservation process look bad.
  
I will be granting their developers an account on the foobar2000 components site, with which they may do whatever they want to publish their own component on the site, as they see fit. I will continue to publish my own component, with the very latest changes to the component interface, that will hopefully filter down into their official work tree as they also see fit, since some things may not be considered stable enough for mass consumption.
  
My only reason for using the development version of libopenmpt was to collect a single obscure change which seemed important to me: The removal of the J2B format&#8217;s minimum and maximum period clamping from the format reader, which fixes at least one of the modules in my Jazz Jackrabbit 2 collection. This minor change is probably not really that important to most users, in the grand scheme of things. I assume the latest stable release, as of today, also contains this fix, so I do not need to cherry-pick it from the development source.
  
Also, in the grand scheme of things, it may or may not be the best idea for a component to derive its main version number from the library it uses, considering the component itself may be updated with newer features or bug fixes in finer granularity than the frequency of stable releases of the library. The &#8220;+N&#8221; notation will still be used for differentiating component-only updates.
  
I hope this clears the air a bit, and paves the way to a more cooperative future for all of the developers involved, and all of the users who enjoy our various works.
