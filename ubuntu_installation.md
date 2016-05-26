---
layout: default
title: Ubuntu Installation
---
# Ubuntu Repository Installation

xwax has been packaged for Ubuntu and Debian and is available from the universe package repositories.

## Stable release

```
$ sudo apt-get install xwax
```

You can see which version is available in which release here: https://launchpad.net/ubuntu/+source/xwax

## Bleeding edge
To stay bleeding edge, you can do the following:

```
$ sudo add-apt-repository ppa:dholbach/ppa
$ sudo apt-get update
$ sudo apt-get install xwax
```

*Note: the xwax_scan and xwax_import scripts are located under /usr/lib/xwax should you wish to replace them with customized versions.*
