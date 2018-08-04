---
layout: default
title: American Audio Versaport .asoundrc
---


Copy and paste into a file called ~/.asoundrc (a hidden file in your home directory).

```
#
# American Audio Versaport
#

pcm.versaport_capture {
	type dsnoop
	ipc_key 1646
	slave {
		pcm "hw:VersaPort"
		period_size 0
		buffer_size 65536
		rate 48000
		channels 4
	}
}

pcm.versaport_playback {
	type dmix
	ipc_key 1646
	slave {
		pcm "hw:VersaPort"
		period_size 0
		buffer_size 65536
		rate 48000
		channels 4
	}
}

pcm.versaport_duplex {
	type asym
	playback.pcm versaport_playback
	capture.pcm versaport_capture
}

pcm.versaport_pair1 {
	type plug
	ttable.0.0 1.0
	ttable.1.1 1.0
	slave.pcm versaport_duplex
}

pcm.versaport_pair2 {
	type plug
	ttable.0.2 1.0
	ttable.1.3 1.0
	slave.pcm versaport_duplex
}
```
