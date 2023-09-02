---
title: Now that I’ve migrated, let’s document a setup process
author: Chris
date: 2015-11-02T04:19:48+00:00
categories:
  - Uncategorized

---
I&#8217;ve been setting up these servers numerous times, and I&#8217;ve had to install the same crap repeatedly. The fun part is building it into a regular process. <!-- more -->   For starters:

I start with an Ubuntu LTS VPS. Currently 14.04.

Then I log into its root account, and \`adduser kode54\` and create my user account, then \`adduser kode54 sudo\` to grant it administrator privileges. Then I log out.

Then I log back in as my user account.

The first thing I install, as a habit I picked up from a friend, is the package tool, \`wajig\`.

Then I use wajig to install \`update-notifier-common\` and \`landscape-common\` for the motd properties.

Then I install the stuff I need to run a given server.

For my main VPS, I install \`nginx\`, and add the official \`weechat\` repository for its latest stable version. I also installed \`php5-fpm\`, for a few minor web page things, and also \`python3-pip\` to install \`beautifulsoup4\` for a \[notifier script\](https://gist.github.com/Treeki/006a30d2f6e07213aa51) that a friend wrote for checking \_things\_.

For my GitLab server, it was similar, only instead of the last paragraph, I add the GitLab Omnibus repository, and install \`gitlab-ce\`. Then, since I&#8217;ve got an existing configuration, I migrated over the \`/etc/gitlab\` files, and also migrated over a full backup.

Oh, crap, I forgot to run wajig daily-upgrade on them.

That&#8217;s the Linux servers.

The Windows server was a completely different game.

For starters, I installed the Windows Server 2012 R2, and waited about 12 minutes for it to provision. Then I connected into it, and used the Server Manager to install .NET Framework 3.5. Then I downloaded the Visual Studio 2010 Professional .iso from my old server, along with the 2010 SP1 .iso, and the disk image of my source code work tree. This source tree is not 100% necessary, but speeds up migration, as it contains everything already pre-cloned, and also contains a lot of older builds, and debugging information.

Installing Visual Studio 2010 only takes about 45 minutes on an SSD, and then installing the Service Pack takes another half an hour. Then it&#8217;s off to Windows Update to configure it to fetch updates for other Microsoft products, then fetch the latest updates. There were about 150 when I last ran it on a fresh machine with all that crap installed.

Welp, that&#8217;s about it. Three servers, all provisioned to make my life easier, or perhaps more complicated.
