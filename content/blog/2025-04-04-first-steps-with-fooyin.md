---
title: "First steps with Fooyin"
date: 2025-04-04T23:13:08-07:00
---

I have made my first steps with [Fooyin](https://github.com/fooyin/fooyin) and drafted an input plugin for MIDI files.

<!-- more -->

It was somewhat of a trial, but I got it working. It's mostly functional, though I would have liked if the player had supported global settings for certain things, like loop counts and fade times and whether to loop a file forever. Alas.

I'll work on packaging it for the AUR tomorrow. For now, you can find the source code [here](https://github.com/kode54/fooyin-kode54-plugins).

To build it, you'll need to install Fooyin to get the SDK in your system, and you'll need libbass, libbassmidi, libbassflac, libbasswv, libbassopus, and libbass_mpc. I provide AUR packages for the BASS plugins, and the Fooyin author provides an AUR package for the player.

From the project directory:

```
cd midiplugin
mkdir build
cd build
cmake ..
make -j$(nproc)
sudo make install
```