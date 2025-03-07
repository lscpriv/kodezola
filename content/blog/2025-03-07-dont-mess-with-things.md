---
title: "Don't mess with things you don't understand"
date: 2025-03-07T05:46:06-08:00
---

Another month, and more bugs to squash. This time with MASShortcut interaction.

<!-- more -->

The MASShortcut, or Mac App Store (compatible) Shortcut key binding framework, which used to live [here](https://github.com/cocoabits/MASShortcut), but is now permanently archived, has rendered [my copy of MASShortcut](https://github.com/kode54/MASShortcut) the only living copy still being maintained. I have changed it a few times to mess with the header paths for framework including, and now have been instructed on the ways of the __has_include() macro definition, which allows you to test #include directives before actually #import ing them. This allows for conditionally including headers using angle braces for Framework headers, but also including them using different paths and double quotes for internal use when actually building the framework.

But that's not the real problem I experienced. The real problem stems from the original MASShortcut code I was given, which set up the hotkey defaults with [NSUserDefaultsController initWithDefaults:initialValues:](https://developer.apple.com/documentation/appkit/nsuserdefaultscontroller/init(defaults:initialvalues:)?changes=l_1&language=objc), which is supposed to set you up a copy of the shared defaults controller that can reset only a select portion of the user settings. The problem? It apparently completely reinitializes the shared instance used by the whole app. This plays havoc with the existing registered defaults for every setting, and also can cause problems with registered listeners.

This mess was causing crashes on macOS Big Sur, but only when the Preferences dialog was opened and the MASShortcut hotkey binding controls were instantiated and the first one was assigned its configuration item name by the awakeFromNib function for the hotkey pane. It also managed to cause a conflict with the Equalizer dialog and controls, causing Key-Value Observing functions to crash in mysterious ways.

Hopefully changing this to a simpler setup has fixed all the problems users were experiencing with these two key features. Now it retains a NSDictionary of the NSData objects of the serialized shortcuts, and re-assigns them to [NSUserDefaults standardUserDefaults] on pressing the reset button.

Sheesh. Don't try to act like you know some clever way to implement a preferences reset and do stupid things like this. It will bite you in the end.