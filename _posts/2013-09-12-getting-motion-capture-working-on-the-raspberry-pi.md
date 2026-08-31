---
layout: post
title: "Getting Motion Capture working on the Raspberry Pi"
date: 2013-09-12 08:47:40 +0000
permalink: /2013/09/12/getting-motion-capture-working-on-the-raspberry-pi/
author: "sven"
categories: ["Uncategorized"]
---

My collection of notes around the Internet. I'm using a Model B with a Raspberry Pi camera and an up-to-date Raspbian.  
First, install motion:

```
$ sudo apt-get install -y motion
```

[Install motion-mmal](http://www.raspberrypi.org/phpBB3/viewtopic.php?t=44966&p=379561#p374790) as follows:

```
$ sudo apt-get install -y libjpeg62 libjpeg62-dev libavformat53 libavformat-dev libavcodec53 libavcodec-dev libavutil51 libavutil-dev libc6-dev zlib1g-dev libmysqlclient18 libmysqlclient-dev libpq5 libpq-dev

$ wget https://www.dropbox.com/s/xdfcxm5hu71s97d/motion-mmal.tar.gz

$ tar -zxvf motion-mmal.tar.gz

$ ./motion -n -c motion-mmalcam.conf
```

Then I made the following changes to motion-mmalcam.conf:

event\_gap from 60 to 20 to reduce the amount of captures stored post-event

threshold from 1500 to 2500 to reduce the sensitivity (number of changed pixels)

 minimum\_motion\_frames from 1 to 4 to reduce the sensitivity (number of frames with motion detected)

ffmpeg\_output\_movies from on to off because I don't want movies

target\_dir from /home/pi to /var/www/archive to suit my web installation

picture\_filename from %v-%Y%m%d%H%M%S-%q to %Y-%m/%Y-%m-%d/%v-%Y%m%d%H%M%S-%q to save putting too many images in a single folder.
