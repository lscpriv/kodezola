---
title: "Circular bind loops are no joke"
date: 2025-03-09T18:53:49-07:00
---

Wow, it looks like MASShortcut had some circular binding loops going on! And a stupid dictionary/array mixup in my tag reading code resulted in some crashes.

<!-- more -->

Yeah, both the shortcut binder that listens for the hotkey events and sends them to their event handlers, and the preferences dialog controls that configured them, bound to the preference items, and the dialog control would "propagate" the value back onto the NSUserDefaultsController every time it was called. Which could result in a loop and a crash.

Apparently, macOS 15.0 closes this problem? Maybe? Not really sure about this one. Either way, the circular loop is closed now. The MASShortcutView only propagates values to the NSUserDefaultsController if they're assigned by its main setter. The observer that listens for changes to the setting doesn't instigate a loop, by intentionally only filling out the View settings and not passing it on again.

Meanwhile, I also stupidly treated a NSDictionary like an NSArray in a release I fired off at the Sparkle updates feed for direct download. That would crash the player any time files are added to the playlist, or any time the tags are forcibly reloaded for some tracks. Sorry about that. I've quickly fixed the responsible code and pushed an update along with this Hotkeys fix.