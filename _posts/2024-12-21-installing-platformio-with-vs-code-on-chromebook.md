---
layout: post
title: "Installing PlatformIO with VS Code on Chromebook"
date: 2024-12-21 20:33:35 +0000
permalink: /2024/12/21/installing-platformio-with-vs-code-on-chromebook/
author: "sven"
---

Getting there with ESP development on a Chromebook...



1. Make sure you have [VS Code already installed](https://www.yetanotherblog.com/2024/12/21/installing-vs-code-on-chromebook/).
2. In a terminal, `sudo apt install python-is-python3 python3-venv`
3. Open up VS Code, hit *Shift + Ctrl + X* and install *PlatformIO IDE*.



For a while, the PlatformIO installer was complaining about Python3.6+ interpreter not working. it seems it was actually specifically looking for venv. Once I installed that, it worked fine.
