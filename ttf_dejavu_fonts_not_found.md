---
layout: default
title: ttf-dejavu fonts not found
---
## Cause
GNU/Linux distributions vary their file system in different ways. As such, the code paths in the xwax install file may or may not reflect the path on your GNU/Linux system.

## Fix
Correct the path in your system to fit the script.

## Methods

  - Notify your distro's xwax packager about the mispathing.
  - Create the directories that the script is searching and make [symbolic links](http://en.wikipedia.org/wiki/Symbolic_link) in them to the actual fonts. For example:

```
 mkdir /usr/share/fonts/ttf-dejavu && find / -type f -iname "DejaVuSans*.ttf" -exec ln -s {} /usr/share/fonts/ttf-dejavu \\;
```
