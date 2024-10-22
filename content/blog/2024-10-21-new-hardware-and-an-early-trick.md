---
title: "New hardware, and an early trick... or treat?"
date: 2024-10-21T19:21:38-07:00
---

I have acquired some new hardware again, over a few weeks, and also have a trick for tailscale to make life easier, which should benefit everyone who has had this little problem with DNS.

<!-- more -->

Continuing to use Linux as my daily driver, though I did run into a hitch with running bcachefs as my daily driver data partition format. The bugs that I experienced were related to snapshots, and I had Snapper making hourly snapshots, but not actually cleaning them up. The bug has been fixed, but I couldn't wait a whole two weeks for Kent to get back from Vienna to fix my filesystem, so I blew it away and restarted mostly fresh.

I still had a backup from the beginning of the month when this happened, but rather than restore that, I started with a new Arch install. I went with btrfs this time, and haven't really had any major issues, other than the new motherboard's SATA controller kicking off one of my hard drives and causing a RAID desync, but that was rather easily fixed by a scrub operation.

Yeah, last year, I had upgraded from a Ryzen 7 2700 to a Ryzen 7 5700X, and also some 64GB of DDR4 3200 MT/s, so I was fairly set on that machine being its final iteration. Now I've got a Ryzen 7 7700X, 64GB of DDR5 5200 MT/s, and just installed a shiny new Radeon RX 7700 XT a couple of days ago. I'm living in relative style once again.

Which brings me to the trick part of the article: Have you ever used Tailscale, and set up a Tailnet on your hardware and such, and found DNS stopped working, at least on the Arch machines? Well, it may just do that if you install with NetworkManager and don't enable any other network related units.

Here's the trick: You need to enable systemd-networkd for Tailscale to play nice with the DNS settings. Otherwise, it will clobber your /etc/resolv.conf every time it restarts, and it won't work nicely that way unless you have forced DNS servers set up in the Tailscale Admin panel.

Simply run:

```
# systemctl enable --now systemd-networkd
# rm /etc/resolv.conf
# ln -sf ../run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
```

And you're set. Feel free to restart `tailscaled` and/or `NetworkManager` at this point, just to be sure they play nice with this. Otherwise, Tailscale plays nice with the systemd-networkd daemon, and resolv.conf only contains a search domain for your Tailnet, and no overriding DNS server. NetworkManager also cooperates with this setup.

Hope this was helpful to someone.