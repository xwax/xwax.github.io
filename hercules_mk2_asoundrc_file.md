---
layout: default
title: Hercules Mk2 .asoundrc
---


Copy and paste into a file called ~/.asoundrc (a hidden file in your home directory).

```
#
# Hercules Mk2
#
      
pcm.Mk2_capture {
                type dsnoop
                ipc_key 1648
                slave {
                        pcm "hw:1"
                        period_time 3
                        period_size 128
                        buffer_size 16384
                        rate 48000
                        channels 4
                }
        }

pcm.Mk2_playback {
                type dmix
                ipc_key 1648
                slave {
                        pcm "hw:1"
                        period_time 3
                        period_size 128
                        buffer_size 32768
                        rate 48000
                        channels 4
                }
        }

pcm.Mk2_duplex {
                type asym
                playback.pcm Mk2_playback
                capture.pcm Mk2_capture
        }

pcm.Mk2_pair1 {
                type plug
                ttable.0.0 1.0
                ttable.1.1 1.0
                slave.pcm Mk2_duplex
        }

pcm.Mk2_pair2 {
                type plug
                ttable.0.2 1.0
                ttable.1.3 1.0
                slave.pcm Mk2_duplex
        }
```
