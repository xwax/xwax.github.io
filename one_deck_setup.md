---
layout: default
title: Using xwax with only one turntable or CDJ
---

Using xwax with only one turntable or CDJ is possible if you use an Y-adapter cable to send your preamp's output to two pairs of inputs of your soundcard, your ALSA setup allows you to read twice from the same source or you are using the JACK audio server.

The following example assumes the use of JACK. See [[Build xwax from source]] for details.

Start xwax from your terminal of choice, specifying two virtual decks:

```sh
xwax -j deck1 -j deck2 -l <your musicfiles>
```

Next use e.g. Qjackctl to connect your soundcard's input to all xwax decks at the same time. If you start your timecode vinyl, you'll notice that they will play simultaneously.

Use the F3 (F7 for second deck, F11 for third) key to disable the timecode input to the deck(s) you don't want to control. To reenable, use F4 (F8, F12 respectively).

You can reset the timecode/file position using F2 (F6, F10).

A typical session would look like this:

  *  Start up xwax using the parameters above
  *  Connect inputs with QJackctl
  *  Press F3, F7 and F11 to disable all decks
  *  You want to start deck1: Press F4 (enables vinyl control), select a track to play, load it with F1 and start your turntable.
  *  Track on deck1 is playing
  *  You want to cue and mix in deck2: Disable vinyl control for the currently playing deck1 with F3 while the record is still spinning (note that the deck1 will play on happily). Enable for deck2 with F8. Load track (F5), place needle at the start of the record and reset control for deck2 with F6. Cue, mix...
  *  and so on.
