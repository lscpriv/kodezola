---
title: "The Year of the HDR Desktop?"
date: 2025-07-29T23:57:09-07:00
---

I have recently acquired an HDR400 IPS monitor, and I like the color reproduction and brightness, where applicable. But is the software there yet?

<!-- more -->

So far, both Windows 11 and macOS are quite capable of handling such a display. Windows 11 has an HDR mode, and blends SDR content somewhat fine in that mode. macOS blends content perfectly, though the brightness tuning kind of sucks. (macOS Tahoe even added better HDR support, including HDR screen shots from the default tools, but they don't even mention this in the release notes.)

How's Linux? Linux is kind of getting there. Plasma has full HDR support, including high precision 16 bits per channel rendering mode as an option, and color tone mapping to fit the display. Unfortunately, when I first set it up, it didn't map the correct SDR white level, so the screen was ultra bright and poppy to start with. It settled down once I figured out how to tune this to 203 nits, and leave the peak brightness as the display detected 486 nits.

GNOME has HDR support as well, and defaults to a reasonable SDR brightness level. Unfortunately, it doesn't seem to expose HDR metadata to capture software, so captured videos don't have display mastering properties set properly.

Among other compositors that support HDR, Sway recently gained HDR support in the Git master tree. And I've written my own [HDR branch for labwc](https://github.com/kode54/labwc/tree/hdr-support), which requires setting a global configuration variable to enable it on all supported displays. Cosmic is supposed to gain HDR support some time in the future, around their stable release.

There are still bugs with the labwc and Sway implementations from wlroots, such as screen and display capture via the compositor being graded for the output, which would be PQ for this setup. The protocols in question only support SDR, so this confuses them and produces dark pictures.

As for software supporting it on Wayland... 

GPU Screen Recorder [\(Flatpak version\)](https://flathub.org/apps/com.dec05eba.gpu_screen_recorder) [\(AUR package\)](https://aur.archlinux.org/packages/gpu-screen-recorder) [\(Gtk UI\)](https://aur.archlinux.org/gpu-screen-recorder-gtk) [\(Fullscreen overlay UI\)](https://aur.archlinux.org/gpu-screen-recorder-ui), is capable of recording HDR video directly from the DRM interfaces, and can log HDR metadata at least from Plasma, but not Gnome or wlroots. You just need to pick a codec with the HDR option, either HEVC HDR or AV1 HDR, depending on your hardware.

Firefox has incredibly poor HDR support, not released yet, so it's disabled by default. And turning it on with the `gfx.wayland.hdr` flag only works for videos, not images or other document content. And there's a bug with it if you have desktop scaling enabled, which causes pixel wide gaps in pages and/or the window itself, aligned with subsurface tile boundaries.

Chromium has an [HDR patch, currently in review](https://chromium-review.googlesource.com/c/chromium/src/+/6771393), which works perfectly well right now, if you don't mind spending a few hours building Chromium 140 with the patch applied. And unlike Firefox, the wider color range is also applied to document contents, including CSS and images, not just videos. Probably the best bet for HDR or even DCI P3 support, and it will hopefully hit in the near future.

As for games, Vulkan supports HDR content, as do DXVK and vkd3d-proton. For Windows games, I recommend [proton-ge-custom](https://github.com/GloriousEggroll/proton-ge-custom), and setting the `PROTON_ENABLE_WAYLAND=1` and `PROTON_ENABLE_HDR=1` environment variables for the game session. More may be required for Nvidia at this point. The ArchWiki has [a nice article on HDR monitors](https://wiki.archlinux.org/title/HDR_monitor_support) that may or may not be relevant to other distributions, depending on how generic the settings may be, or how bleeding edge other distributions' software may be.

Thus far, I've tested Cyberpunk 2077, Death Stranding: Director's Cut, which have their own built-in support, and several games with [renodx](https://github.com/clshortfuse/renodx) patches available that implement some semblance of full HDR, depending on the game. Usually the patches implement unclipped color processing with altered shaders. I tested all of them with GE-Proton, and some with Gamescope. However, Gamescope doesn't work with the wlroots compositors, because it uses a Vulkan renderer to achieve this support, and Gamescope currently doesn't run with a Vulkan renderer over top of it. GE-Proton more than makes up for this, though.

MPV works with HDR and Vulkan, too. I use a particular configuration to achieve color grading on this display, while still supporting software decoding of color information for things like Dolby Vision. My configuration is as follows:

```
hwdec
vo=gpu-next
gpu-api=vulkan
gpu-context=waylandvk
target-colorspace-hint=yes
ytdl-format=bestvideo[vcodec^=av01]+bestaudio/bestvideo[vcodec!^=av01]+bestaudio/best
slang=eng,en
screenshot-format=jxl
```

I hope to see more Linux HDR or at least DCI P3 support in software going forward. Thus far, there are no video editors that support this, other than Blender 5.0 alpha, and most of the image viewers I tested didn't work outside sRGB either. I am currently utilizing mpv as an image viewer and a video viewer. And a self-built Chromium 140 with the above linked patch applied.