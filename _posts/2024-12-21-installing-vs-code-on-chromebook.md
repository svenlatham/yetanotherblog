---
layout: post
title: "Installing VS Code on Chromebook"
date: 2024-12-21 20:25:49 +0000
permalink: /2024/12/21/installing-vs-code-on-chromebook/
author: "sven"
---

1. First, [enable Linux on your Chromebook](https://support.google.com/chromebook/answer/9145439?hl=en-GB).  
2. Download the latest .deb installation from <https://code.visualstudio.com/download>  
3. Move this file to the Linux shared files (should be visible in the file manager, and is probably empty). This folder is your home directory in Linux.  
4. Open a Linux terminal and type  
   `sudo apt install ./{downloaded file}.deb`  
5. You will likely be prompted to add the Microsoft apt repo to your installation. Select YES.  
6. Once installed, you should now have VS Code in your Launcher.



Remember that you're running VS Code from inside a Linux container, so your other Chromebook files won't be available.
