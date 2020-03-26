---
layout: default
title: xwax Documentation
---

xwax is an open source [vinyl emulation software](http://en.wikipedia.org/wiki/Vinyl_emulation_software) project under the [GPL](http://en.wikipedia.org/wiki/Gpl) for GNU/Linux.

Please feel free to contribute to the documentation. You can also chat with or ask advice from the xwax community live in the IRC channel [#xwax](https://webchat.freenode.net/#xwax) which is hosted on [Freenode](https://freenode.net/)

# User Guides & Documentation

## Getting Started with xwax

### Installing xwax

  * [Building xwax from Source](/build_xwax_from_source)
  * [Debian Repository Installation](/debian_installation)
  * [Ubuntu Repository Installation](/ubuntu_installation)
  * xwax is also available in the Arch Linux Community repository

### Configuring xwax

  * [Connecting your hardware](/connecting_your_hardware)
  * [Setting up real time audio priority for xwax](/setting_up_real_time_audio_priority_for_xwax)
  * [Writing your start-up command](/writing_your_start-up_command)

### Using xwax

  * [Keyboard Control](/keyboard_control)
  * [Novation Dicer Control](/novation_dicer_control)

## Hardware & xwax

  * [Tested Soundcards](/list_of_soundcards)
  * [Timecode Records and CDs](/timecode_records_and_cds)
  * [CDJ Behaviours](/cdj_behaviors)

## Non-Standard Usages and Modifications

### Non-Standard Usages

  * [One deck setup](/one_deck_setup) - Controlling several virtual decks with only one turntable
  * [Four-deck rigging](/four-deck_rigging) - Breaking xwax's 3 deck barrier

### Patches

  * [Cues saving and display](https://github.com/oligau/xwax-1.5-xwaxed-cues) - Port of xwaxed cues features. Save and load from .cue file and cue display.
  * [xwax Timecode](https://github.com/oligau/xwax-1.5-timecode) - Version of xwax that contains Mark's timecode definitions for 4khz, 2khz and 1khz versions. [Timecode 1khz 0.1 FLAC and MP3 torrent](http://oscille.ca/tracker/xwax-timecode-0.1.zip.torrent)
  * [OSC Server](https://github.com/oligau/xwax-1.5-osc) - Evolution of cmd branch. Permits to send commands with xwax-client command line or by OSC messages.
  * [ympd web client](https://github.com/oligau/ympd-xwax) - xwax remote control branch of ympd mpd client
  * [Relative Timecode](/relative_timecode) - Togglable prevention of record skipping and needle dropping
  * ["Vertical side-by-side waveforms" patch](http://pastebin.fr/pastebin.php?dl=24065) for xwax 1.3-beta2 (see [screenshot](http://twitpic.com/6suvkn))

### Outdated Hacks

  * [Changing the font size in xwax](/changing_the_font_size_in_xwax)
  * ["Vertical side-by-side waveforms" patch](http://pastebin.fr/pastebin.php?dl=22474) for xwax 1.0
  * [45RPM Mode](/45rpm_mode) for 0.7 and earlier


## External Tools and Scripts

### Import Scripts

[Default Import Script](/default_import_script)

  * [Scan + Import Script for Scratching a Live Input](/modified_script_for_live_mic_input)
  * [CD audio instructions](/setting_up_the_cd_audio_importer)

### Scan Scripts

[Default Scan Script](/default_scan_script)

  * [Scan + Import Script for Scratching a Live Input](/modified_script_for_live_mic_input)
  * [iggy's Scan Script](/iggy_s_scan_script) - Uses playlists to speed up xwax's startup time and gets BPM info from file metadata
  * [oligau's Scan Script](/oligau_s_scan_script) - Uses playlists to speed up xwax's startup time and gets BPM info from file metadata or from filename if no tag present
  * [Mark's scan script with BPM tags](/mark_scan_tags) - Extract BPM information from file tags on the fly, and cache it

### External Tools

  * [xwax Playlist Exporter](/xwax_playlist_exporter) - An Amarok 2 script
  * [bpm-tools](/bpm-tools) - BPM detection
  * [key-tools](http://www.pogo.org.uk/~mark/key-tools/)- Key detection

## Misc

  * [xwax Changelog](xwax_changelog)

# Common Issues & Troubleshooting

  * Virtual decks playing in reverse? Switch the left and right RCA plugs over.
  * Getting pops, clicks and xruns? Try increasing your buffer size.
  * xwax not working with your CD players? Turn off key lock/master tempo.
  * [Diagnosing the Scope Views](http://serato.com/articles/scratchlive/2781/diagnosing-the-scope-views) - A useful article from Serato on using the scope display. Helpful if your timecode's performance is less than optimal.
  * Scope signal is square? You might have input distortion if your CD player output is too loud for your audio interface input. If the audio interface has a fixed input gain, you can lower the amplitude of the timecode WAV file in a program such as Audacity and burn a new timecode CD.
  * [TTF DejaVu fonts not found](/ttf_dejavu_fonts_not_found)

# xwax Community

xwax is not only a project, but also a lively community!

  * Check out [our works](/our_works) and list your creations too!
  * Get in touch with the developers with your feedback and bug reports via the [xwax-devel mailing list.](https://lists.sourceforge.net/lists/listinfo/xwax-devel)
  * You can also chat with or ask advice from the xwax community live in the IRC channel [#xwax](https://webchat.freenode.net/#xwax) on [freenode.net](https://freenode.net). Please be patient and wait around a while if nobody is around to help straight away.
