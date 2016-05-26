---
layout: default
title: 45rpm Mode
---

## xwax 0.8 and later

Since xwax 0.8 you can enable the 45rpm mode by passing **-45** as command line argument and as a result this hack is no longer required.


## modify xwax before 0.7 (hack)

xwax (version 0.7 and before) defaults to 33 1/3 rpm for Serato & Traktor vinyls. To allow the use of 45RPM:


###  45RPM Input
In **timecoder.c**, find the line containing ".resolution = X" and multiply X by 1.35 (45 / 33 1/3) - for Traktor this should give 2700, or 1350 for Serato. This will allow the timecode disc to be played at 45, but the Spinner display will not spin at the correct speed.


### 45RPM Spinner on GUI:
In **interface.c** find the line containing "rangle = ...." (there should only be one) and edit to

    rangle = (int)(pl->position * 1024 * **13.63** / 18) % 1024; </code>


###  Notes:
Please note that while the first part does actually work, the latter part may be completely wrong. It is possibly also better to change the "13.63" in that line to a constant, so that both 33 and 45 can be used without having to recompile. But for a single user, you are generally unlikely to switch between to two speeds regularly.
