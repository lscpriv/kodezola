---
title: "Cog updates"
date: 2023-10-04T16:32:00-07:00
---

I've been working heavily on Cog again lately, and finally pushed out an update with these major changes. But then I needed to quickly release another bug fix afterward, because I forgot something.

<!-- more -->

I restored the original Core Audio output a month ago or so, but in the process, I also rewrote a lot of it to match the newer core playback system. This took time then, and then it took more time this month when I resumed the process.

The result is that the sound output once again has incredibly low latency to its actions, because Core Audio, or AUAudioUnit interface, has minimal latency to the operating system itself.

This presented some challenges along the way, however. First, I needed to fix up the interface code to work with this older system, and this included removing some redundant checks from the code that were causing race conditions to stop continuous playback in its tracks.

I also needed to implement a different head tracked positional audio system. I think it works quite nicely, though, and you may enjoy it as much as the older system, if you used it.

The last minute bug I had to fix, however, was a missing function implementation for setting the output format on the background converter threads, which would cause a missing function crash if your sound output device changed format or device for whatever reason.

All should be well once again.