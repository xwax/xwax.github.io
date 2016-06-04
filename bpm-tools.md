---
layout: default
title: bpm-tools
---

Mark has written a great bpm scanner:

[http://www.pogo.org.uk/~mark/bpm-tools/](http://www.pogo.org.uk/~mark/bpm-tools/)

```
bpm-tag (C) Copyright 2012 Mark Hills <mark@xwax.org>

    Usage: bpm-tag [options] <file>
    Tag an audio file with tempo (in beats-per-minute, BPM)

      -f   Ignore existing BPM value
      -n   Display BPM only, don't tag
      -m   Minimum detected BPM
      -x   Maximum detected BPM
      -h   Display this help message and exit
```

The bpm-tag script in bpm-tools works on one file at a time.

To batch tag in the current directory do this:

```sh
find ./ -type f -print0 | xargs -0 -n1 bpm-tag
```

If you want to scan annother directory replace `./` with the folder you want to scan.

If you have a multicore machine try this, it will run 4 instances in parallel:

```sh
find ./ -type f -print0 | xargs -0 -n1 -P4 bpm-tag
```
