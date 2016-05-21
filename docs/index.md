---
layout: default
title: Documentation
---
#  xwax Community Wiki

xwax is an open source [[http://en.wikipedia.org/wiki/Vinyl_emulation_software|vinyl emulation software]] project under the [[http://en.wikipedia.org/wiki/Gpl|GPL]] for GNU\Linux

Please feel free to contribute to the documentation. You can also chat with or ask advice from the xwax community live in the IRC channel #xwax on [[http://freenode.net/using_the_network.shtml|irc.freenode.net]]

# User Guides & Documentation

## Getting Started with xwax

### Installing xwax

  * [[Build xwax from Source|Building xwax from Source]]
  * [[Debian Installation|Debian Repository Installation]]
  * [[Ubuntu Installation|Ubuntu Repository Installation]]
  * xwax is also avalible in the Arch Linux Community repository


### Configuring xwax

  * [[Connecting your hardware]]
  * [[Setting up real time audio priority for xwax]]
  * [[Writing your start-up command]] FIXME

### Using xwax

  * [[Keyboard Control]]
  * [[Novation Dicer Control]]
## Hardware & xwax

  * [[List of soundcards|Tested Soundcards]]
  * [[Timecode Records and CDs]]


## Non-Standard Usages and Modifications

### Non-Standard Usages

  * [[One deck setup]] - Controlling several virtual decks with only one turntable
  * [[Four-deck rigging]] - Breaking xwax's 3 deck barrier

### Patches

  * [[https://github.com/oligau/xwax-1.5-xwaxed-cues| Cues saving and display]] - Port of xwaxed cues features. Save and load from .cue file and cue display.
  * [[https://github.com/oligau/xwax-1.5-timecode|xwax Timecode]] - Version of xwax that contains Mark's timecode definitions for 4khz, 2khz and 1khz versions. [[http://oscille.ca/tracker/xwax-timecode-0.1.zip.torrent|Timecode 1khz 0.1 FLAC and MP3 torrent]]
  * [[https://github.com/oligau/xwax-1.5-osc|OSC Server]] - Evolution of cmd branch. Permits to send commands with xwax-client command line or by OSC messages.
  * [[https://github.com/oligau/ympd-xwax|ympd web client]] - xwax remote control branch of ympd mpd client
  * [[relative timecode|Relative Timecode]] - Togglable prevention of record skipping and needle dropping
  * [[http://pastebin.fr/pastebin.php?dl=24065|"Vertical side-by-side waveforms" patch]] for xwax 1.3-beta2 (see [[http://twitpic.com/6suvkn|screenshot]])
  * [[http://confusedbits.net/coding/playedtracks-patch-for-xwax-0-7/|"playedtracks" patch]] for xwax 0.7
  * [[http://confusedbits.net/coding/cue-points-patch-for-xwax-0-7/|"cue points" patch]] for xwax 0.7


### Outdated Hacks

  * [[changing the font size in xwax|Changing the font size in xwax]]
  * [[http://pastebin.fr/pastebin.php?dl=22474|"Vertical side-by-side waveforms" patch]] for xwax 1.0
  * [[45RPM Mode]] for 0.7 and earlier


## External Tools and Scripts

### Import Scripts

[[Default Import Script]]

  * [[Modified Script For Live Mic Input | Scan + Import Script for Scratching a Live Input]]
  * [[setting up the cd audio importer | cd audio instructions]]

### Scan Scripts

[[Default Scan Script]]

  * [[Modified Script For Live Mic Input |Scan + Import Script for Scratching a Live Input]]
  * [[iggy's Scan Script]] - Uses playlists to speed up xwax's startup time and gets BPM info from file metadata
  * [[oligau's Scan Script]] - Uses playlists to speed up xwax's startup time and gets BPM info from file metadata or from filename if no tag present

### External Tools

  * [[xwax Playlist Exporter]] - An Amarok 2 script
  * [[bpm-tools]] - BPM detection
  * [[http://www.pogo.org.uk/~mark/key-tools/|key-tools]]- Key detection

## Misc

  * [[xwax_changelog|xwax Version History]]

# Common Issues & Troubleshooting

  * Virtual decks playing in reverse? Switch the left and right RCA plugs over.
  * Getting pops, clicks and xruns? Try increasing your buffer size.
  * xwax not working with your CD players? Turn off key lock/master tempo.
  * [[http://serato.com/articles/scratchlive/2781/diagnosing-the-scope-views|Diagnosing the Scope Views]] - A useful article from Serato on using the scope display. Helpful if your timecode's performance is less than optimal.
  * [[TTF DejaVu fonts not found]]

# xwax Community

xwax is not only a project, but also a lively community!

  * Check out [[ourworks|our works]] and list your creations too!
  * Get in touch with the developers with your feedback and bug reports via the [[https://lists.sourceforge.net/lists/listinfo/xwax-devel|xwax-devel mailing list.]]
  * You can also chat with or ask advice from the xwax community live in the IRC channel #xwax on [[http://freenode.net/using_the_network.shtml|irc.freenode.net]]. Best practice is to ask your question and then leave your IRC client running while you do something else as it may be some time before someone replies.
