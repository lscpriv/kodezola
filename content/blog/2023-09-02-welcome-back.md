---
title: "Welcome back, everybody."
date: 2023-09-02T16:16:00-07:00
---

Well, I've returned to some semblance of blogging again. I'm attempting to document things as I work on my projects now.

<!-- more -->

Thanks to Kevin, my site has been remade with a new site generator, [Zola](https://www.getzola.org/), while maintaining the existing look and feel, including using Bootstrap for the site template.

I keep switching between my computers regularly, and I switch between my slightly aging (but new to any blogging) Ryzen 7 2700 system, and the M1 Mac mini I got in March of 2021, not long after they originally launched.

I got an Intel Arc A770 video card in January of 2023, and it's been a mixed bag. The drivers on Windows are quite good now, even with their problems persisting for some apps, especially Switch emulation, but for a lot of games, especially the ones I do care about, they're a positive experience.

The Linux experience on Arc isn't as hot, but sometimes more stable all around. But since the game I'm trying to play now, [The Spirit And The Mouse](https://thespiritandthemouse.com/), has some graphical bugs on Arc, and major ones when using the Xe kernel driver, I'm more in the mood to play it on my Mac instead.

Now, on to dev. I'm working on adding Composer tag support to the player. This requires adding a new column to the display code, a new field to the metadata interface class to speed access, and adding reading to various tag readers. As it stands now, most likely the key/value based tag readers already read this field into the key/value store in the player, but the TagLib based readers for other tag formats at least need explicit support.

More on this later.