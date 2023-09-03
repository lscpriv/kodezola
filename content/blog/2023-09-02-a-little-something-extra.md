---
title: "A little something extra."
date: 2023-09-02T23:40:00-07:00
---

I finished my dev work for the day, and a little extra. But not without a little bit of sidetracking.

<!-- more -->

I started on my work on the composer columns for Cog, but then got sidetracked. Into a game of Pikmin 4.

Pikmin 4 apparently runs quite well in Ryujinx 1.1.1005 on macOS on the base M1 processor and GPU. Minor shader compilation hitches here and there, but otherwise, quite swell.

EuroGamer would seem to indicate in [this article about Pikmin 4 switching engines to Unreal Engine](https://www.eurogamer.net/digitalfoundry-2023-pikmin-4-tested-on-switch-nintendos-series-moves-to-unreal-engine#:~:text=Hot%20off%20the%20heels%20of,seen%20on%20Switch%20to%20date.) that the switch was specifically to Unreal Engine 4. The game's resources tell another story, however.

The game contains only the bank files in its ROM file system, and it contains the telltale .UTOC / .UCAS bank files, which indicate it's using the Zen Loader. Which means that Pikmin 4 is using Unreal Engine 5, or possibly a beta of it at least. Guess that could explain the marvelous graphics to go with the excellent gameplay.

I wish I could do better at the challenges, though. And didn't have the anxiety over the day time limits in the levels. Well, except for the underground sections, where time doesn't seem to progress on the overworld, or at least not as quickly.

Now where was I?

Oh yeah, I finished my work on the Composer column and tag reading. It's hidden by default, but it can be turned on easily with the context menu. Also, unmentioned in the change log, but I reordered all the dialog objects on the Info Inspector to their display order, which may or may not help with Screen Reader support.

I did a little something extra, too. I updated VGMStream, and I also changed several parts of the Playback Controller class to use background invocation for starting the actual playback and seeking within files. This should alleviate the UI being unresponsive when starting playback of files that take a significant amount of time to open. Pausing, resuming, stopping, and setting the volume level are all kept synchronous, since they should be quick actions. Also, making stop asynchronous was interfering with manual track changes.