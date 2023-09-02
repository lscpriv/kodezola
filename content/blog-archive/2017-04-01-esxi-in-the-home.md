---
title: ESXi in the home
author: Chris
date: 2017-04-02T04:47:45+00:00
categories:
  - Uncategorized

---
On the 10th of March or so, I set about installing VMware ESXi 6.5 on my PC tower, and using the divided resources to replace my previous bare metal Windows installation. <!-- more -->  The [machine][1] is now divided up into:

Four CPU cores in two sockets, with 16GB of the RAM, 120GB of the SSD space, and with my RX 480 8GB and two internal USB 2.0 adapters via PCIe passthrough, to my primary Windows 10 Pro installation, which hosts Steam, some games, and is purposed for regular use.

Four CPU cores in two sockets, 4GB of the RAM, and 86GB of disk space, to another Windows 10 Pro VM purposed for development and debugging. I use a VM for this due to debugging issues when running bare metal that result in deadlocks that can only be escaped by stabbing the three finger salute and logging out.

Two CPU cores (yes, I over provisioned) and 8GB of RAM, 16GB of disk space, and the three (previously four, need to buy a replacement and let it resilver) hard drives (2x4TB WD Red, 1x6TB Toshiba) passed directly into a NAS4Free VM, which is hosting a ZFS array, RAID10 style: The 6TB drives were in a mirror, and the 4TB drives in another mirror, and the two mirrors were joined. I now need to replace the 6TB drive with another, and wait while it resilvers, before my data will be slightly more secure again.

Back to the primary VM: Since I sent my iMac into the shop, I&#8217;ve been running it as my primary desktop. With the video card passed in, and enough USB ports to plug in my usual array of input and accessory devices, I can use a VM in a hypervisor as my primary desktop. Living the dream, or at least it&#8217;s flying like a dream after the initial nightmare was over, getting it to work in the first place.

 [1]: http://valid.x86.fr/afukyx
