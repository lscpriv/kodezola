---
title: "Linux benefits outweighed my Windows experience again"
date: 2024-03-31T15:20:46-07:00
---

Once again, my attempt to switch to Windows was met with annoyances. Sure, I find annoying nitpicks with every OS, but these ones really hit the nail into the coffin again.

<!-- more -->

In using Linux as my daily driver, I had run into BlueZ disconnecting my controller regularly and having reconnect problems. This was a sort of straw that broke the camel's back, as it drove me to switch to Windows.

I spent an hour or two installing Windows, and got everything configured:

* I had to install winbtrfs to read the Linux storage drives, including a RAID1 array containing all my media.
* I needed to install Plex Media Server to host my media to external devices. This involved setting the server up from scratch, and reconfiguring the watch info for stuff we had been viewing recently.
* Steam needed installing, for the games I play together with Kevin, and other games I play by myself.
* Bluetooth needed to be rebound to my devices.

Anyway, I ran into numerous nitpicks, some of which I experienced already in the past:

* Fullscreen or borderless games sometimes filled only part of the screen instead of the whole screen.
* Bluetooth headsets would disconnect regularly, or mute themselves without appearing to disconnect. This drove me to stop using Bluetooth headsets under Windows. I hear this may be getting fixed in Insider builds, but I don't feel like waiting.
* Finally: Plex Media Server can't serve some of my media files properly to an Apple TV 4K. MPEG-2 video, ripped directly from DVDs using MakeMKV, decides to be decoded by the server rather than being passed directly to the Apple TV. Setting Quality on the ATV to "Auto" results in really ugly transcodes, turning this off renders them unplayable.

So I switched back to Linux. Plex actually broke playback until I turned Auto Quality back to Off, but then the MPEG-2 video streamed directly to the Apple TV without a hitch.

Yeah, I lose some things, but gain others. As I've said, I find numerous annoyances with whichever environment I end up in, but I find the Linux annoyances less painful.

The Linux Bluetooth problem I had? All I needed to do to work around it, at least until it's fixed in the future, is turn off Userspace HID support in input.conf.