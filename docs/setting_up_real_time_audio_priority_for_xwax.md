---
layout: default
title: Documentation
---
# Setting Up Real Time Priority

To achieve low-latency audio you need to increase the scheduling priority of the playback thread, xwax will perform poorly or not boot at all without it.

This normally requires a modification to ''rtprio'' in the ''limits.conf'' file. 80 is the recommended value. On Ubuntu this file is located in /etc/security/

## Guide for doing this on Ubuntu


  - Open the file with a text editor such as nano by executing the following
    in the terminal `$ sudo nano /etc/security/limits.conf`
  - Append the following to the end of the file `YOURUSERNAME - rtprio 80`
  - Close the file by pressing ctrl+X, ensuring you save the changes
  - Log out and log back in for the changes to take effect

