---
title: "Sorry about the Cog bugs!"
date: 2025-02-14T20:12:39-08:00
---

Happy Valentines Day to those who celebrate it, and sorry about all the
recent crashes you've been experiencing with Cog!

<!-- more -->

Sorry about the buggy code. Apparently, I don't know a whole lot about
using the Rubber Band library, and didn't observe a bunch of functions
which return signed types, and simply tossed them into unsigned variables.

Specifically, the functions to request how many samples Rubber Band wants
to process, and how many samples are available to read out. I've changed
the respective code significantly, as you can see [here](https://codeberg.org/losnoco/Cog/commit/923179c4ebb208c4e37fee97ed7ff3183398e746).

So now, when the Rubber Band library wants input, it gets input. When it
doesn't, input stage is skipped. When it wants to provide output, output
is requested and returned. If the output overflows the output buffer, it
will wait until the next chunk is to be processed.

Hopefully, this will fix the tons of crashes people have been experiencing
lately as a result of the Rubber Band code being enabled by default in
existing installs, which limited the crashes to only long time users updating to the new version. Sorry about that!