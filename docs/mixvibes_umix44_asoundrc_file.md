---
layout: default
title: Mixvibes umix44 .asoundrc
---
# Mixvibes umix44 .asoundrc

Copy and paste into a file called /home/<user>/.asoundrc

```
pcm.umix44_playback {
	type dmix
	ipc_key 1646
	slave {
		pcm "hw:Device"
		period_size 0
		buffer_size 65536
		rate 44100
		channels 4
	}
}

pcm.umix44_duplex {
	type asym
	playback.pcm umix44_playback
	capture.pcm umix44_capture
}

pcm.umix44_pair1 {
	type plug
	ttable.0.0 1.0
	ttable.1.1 1.0
	slave.pcm umix44_duplex
}

pcm.umix44_pair2 {
	type plug
	ttable.0.2 1.0
	ttable.1.3 1.0
	slave.pcm umix44_duplex
}
```
