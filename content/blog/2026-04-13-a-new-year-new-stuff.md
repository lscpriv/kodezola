---
title: "Has it really been almost a year? New stuff."
date: 2026-04-14T00:28:20-07:00
---

Dang, I actually let 9 whole months slip by without writing any further articles. A lot has happened since the last post.

<!-- more -->

For instance, on the Linux HDR front, wlroots has managed to release version 0.20, with the HDR support mostly okay for basic things. KDE / Plasma are really the more mature solution, but GNOME 50 isn't far behind.

As for my personal projects, I've been experimenting with the Claude Sonnet model, and so has my boyfriend, both for his own uses, and for our group benefit. We were assisted a bit in rewriting the settings dialogs of Cog to a totally new SwiftUI design.

Cog now requires macOS 10.15, after a brief window of moving up from 10.13 to 10.14. A lot has changed.

I also vibe coded my way out of a paper bag to start the skeleton effort of porting [SpessaSynth](https://spessasus.github.io/SpessaSynth/) to C, and after a lot of fighting with the translator, and a lot of manual coding as well, I think I'm satisfied with the base result. I now have a library which meets or exceeds the quality of BASSMIDI, except it's Open Source, under the Apache License, and I can tweak it however it needs. Thus, Cog now has support for SF3 and SFe, as well as DLS, and embedded DLS and SF2 banks in RMIDI files. Awesome. Not bad for five to six days of work.

The resulting code is approximately 12.5k lines, and of that, I messed with a bunch that I haven't tabulated the total count on, but I do know that Claude managed to write exactly 10,504 lines so far. I hope to not make a further habit of doing that, as it's already been somewhat expensive.

I'm ever thankful to [Spessasus](https://spessasus.github.io/) for the original work, and plan to contribute to their projects as well, anything unique I bring to the table.
