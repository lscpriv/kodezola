---
title: "A New Year, A New Testing Process"
date: 2025-01-15T18:59:31-08:00
---

It's a new year already, and I already got bitten by an old bug that failed to appear before. It's time for more serious testing.

<!-- more -->

Welp. Looks like I should have found this sooner. A bug reared its ugly head, and it turns out it's because memory was being zero initialized instead of left with garbage data. Which means the bug was already happening, but not crashing like it did. Possibly using weirdly high amounts of memory.

Anyway, found the bug. Fixed it. But I would have found it sooner if I regularly first launch tested Cog on a fresh machine. So now, I'll be using [VirtualBuddy](https://github.com/insidegui/VirtualBuddy) to test my app in a fresh VM each time, and only alter the VM regularly to run updates, then spin off a duplicate to do the install and actual testing.

This should help me regularly find any weird first launch issues. I can install Xcode and the source code in the VM if I need to debug it on a fresh install as well. Sure beats interrupting my own personal use of the app directly on my machine to run the tests, which could prove inconclusive, and also mess up my relax time usage.