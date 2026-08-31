---
layout: post
title: "Installing TAUCP on Total Annihilation from Steam"
date: 2017-01-02 14:39:26 +0000
permalink: /2017/01/02/installing-taucp-on-total-annihilation-from-steam/
author: "sven"
categories: ["Uncategorized"]
---

[TAUCP](http://taucp.tauniverse.com/taucp.htm) is a mod for Total Annihilation (great, vintage top-down fighting game). [Total Annihilation is now available on Steam](http://store.steampowered.com/app/298030/) for a decent price and runs well on modern Windows 10 PCs.![](https://www.yetanotherblog.com/wp-content/uploads/2017/01/ta-300x222.png)
TAUCP comes as an executable installer. Run the installer and let it install to the default location (probably c:\cavedog\totala).
Next, open Windows Explorer and go to that location. Copy all the installed files (which will include a whole bunch of folders, ai, gamedata, maps, etc.)
Go to C:\Program files (x86)\Steam\steamapps\common\Total Annihilation\ and copy the files into there.
I got one prompt, which was to overwrite rev31.gp3, andÂ allowed this to overwrite. This file enables theÂ mod.
Now, when you launch Total Annihilation, the new mod kit should be active with new units in various factories.
**Notes:**

* It also creates a file prefrontend.exe in the install directory which allows you to configure the mods and AIs.
* rev31.gp3Â is theÂ patch file that enables TAUCP. If you don't copy, it won't work. The prefrontend.exe file swaps the original and modified rev31.gp3 file as you enable theÂ mod.
