---
title: Meet my new blerg
author: Chris
date: 2015-11-01T08:45:11+00:00
categories:
  - Uncategorized

---
Welp, everybody, here&#8217;s the new blergh! Isn&#8217;t it swell? Oh, exploitable!
<!-- more -->  
Well, I donned my fursona name on Freenode for Halloween, and that wasn&#8217;t really met with any question, as everybody already knows I&#8217;m a gigantic furry [expletive deleted]. I can say that word because it&#8217;s another true aspect of my character.

&#8212;

Well, how about an update for the world of the Real?

I finally got off my ass and got my new development VPS set up! For the low low price of $54/mo, I get a Windows VPS, and for just $30/mo on top of that, I get to use any version of Visual Studio on that machine. I would use Community for free, but I like to continue to support my poor Windows XP users, and since Peter has not seen fit to drop support for XP, neither will I.

Visual Studio 2015 had lovely errors when attempting to build \`foo\_midi\` with the \`v140\_xp\` SDK. The resulting code would \_appear\_ to work, only when anyone running Windows XP attempted to play or convert any files using the MUNT MT-32 emulator, either automatically or through the Super MUNT GM mode, would crash the player. No such problem on Windows Vista or higher.

Debugging this is probably out of the question, since I cannot run Visual Studio 2015 on a Windows XP VM, nor can I use remote debugging with VS 2015. I probably could try using Windbg, but I don&#8217;t really feel like that.

One downgrade later, fully updated Visual Studio 2010 Professional, a rebuild of the source and project tree for \`foo_midi\`, and it runs flawlessly on Windows XP systems.

Next up on the agenda, I need to update my copy of residfp to the latest SVN source, which will apparently fix a number of playback bugs, such as some files that fail completely, and others that may have rendering errors.
