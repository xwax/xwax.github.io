---
layout: default
title: Ubuntu Installation
---

xwax has been packaged for Ubuntu and is available from the universe package repositories.

## Stable release

```
sudo apt-get install xwax
```

You can see which version is available in which release on [Launchpad](https://launchpad.net/ubuntu/+source/xwax).

## Bleeding edge
To stay bleeding edge, you can do the following:

```
sudo add-apt-repository ppa:dholbach/ppa
sudo apt-get update
sudo apt-get install xwax
```

*Note: the xwax-scan and xwax-import scripts are located under /usr/share/xwax should you wish to replace them with customized versions.*
