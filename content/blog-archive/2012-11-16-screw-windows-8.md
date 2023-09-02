---
title: Screw Windows 8
author: Chris
date: 2012-11-16T17:19:49+00:00
categories:
  - Uncategorized

---
I&#8217;m finished with Windows 8, at least on my desktop. It can stay on my laptop, at least until it blows up there as well.

So here&#8217;s what happened: I decided I was going to resume my game of Borderlands 2 after so many weeks of letting it languish in the role of SHiFT Code Receptor. So I opened up the display resolution properties to check that the 3D Vision checkbox was enabled, and noticed the checkbox was absent entirely. Huh. That should have been my first clue that something was up.

I went to NVidia&#8217;s site in Chrome, and ran the Java-based driver detection function, which decided that I had 302.something, presumably the drivers that come with Windows 8. Okay, so I checked the latest, and saw that it was the same version I already thought I installed.

I checked the C:\\NVIDIA\\DisplayDriver directory, and lo and behold, there was a subdirectory for that version. So I decided to run the driver from there. It started installing, and then got to the display driver update part. My sound card played the device detach sound, and the screen went blank for a moment. When it came back on, it was displaying nothing but a black picture with a Modern UI (formerly Metro) vertical splitter at about 1/4 from the left of the screen, and my mouse pointer. The mouse pointer moved, but would not click on anything. The splitter would not react to clicking, either. Keyboard did nothing. I waited for a minute, then tried the power button, which also seemed to cause some disk activity, but nothing else.

So I stupidly rebooted the machine. It came back in VGA/VESA mode, with a non-functional NVidia accelerator in the Device Manager. I tried reinstalling the drivers, and that failed. It didn&#8217;t occur to me to try forcing a clean reinstallation, but whatever. I then went into the Device Manager and deleted the device, then refreshed detection, which resulted in a generic VGA device. That too refused to accept any driver installations, even from Windows Update through the driver properties page.

Bah, so now my video subsystem was hosed. I went to Freshen my Windows 8 installation, and it promptly asked for installation media. Of course, I didn&#8217;t burn Windows 8, I used a USB stick, which I had since wiped with the [Arch Linux][1] installer from the adventures with my previous desktop machine, now repurposed as a HTPC or server machine.

Inspiration hit me. I decided right there to blow my SSD away and install Arch Linux to it. That was fun. But it didn&#8217;t stop there. I rediscovered that NTFS-3g is very flaky, and under stresses such as running uTorrent-Server and checking a whole lot of large torrents, it can crash and leave the FUSE driver forever dangling. So I found the [Paragon Universal File System Drivers][2] for Linux, which support full read and write for both NTFS and HFS/+ partitions. Unfortunately, they only support kernel version 2.6. I&#8217;ve since [patched][3] their kernel glue code to support kernel 3.6, but then I ran into a new problem. Wine could not see most of the files or directories on the volumes mounted as ufsd. That would not do.

So now I&#8217;ve converted my 640GB drive from NTFS to ext4, using an external drive to store the files. I ran into a problem with the crappy SATA to USB 3.0 controller in this WD MyBook drive, where it can&#8217;t instruct the drive to remap bad sectors. So I lost one file, and those sectors can&#8217;t be marked bad, and Windows sees the drive and won&#8217;t mark them bad either. So now I just shoved the bad file, which was a completely expendable Visual Studio program database, into a directory on the root of the drive, with instructions to never delete it.

With that done, I&#8217;ve moved the contents of my 1.5TB drive onto the external, and now I await the process of moving them back to complete. Isn&#8217;t life grand?

 [1]: http://www.archlinux.org/
 [2]: http://www.paragon-software.com/technologies/ufsd.html
 [3]: //balde.losno.co/kn/t/paragon-ufsd-3.6.patch
