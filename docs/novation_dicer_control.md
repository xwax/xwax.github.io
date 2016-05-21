---
layout: default
title: Novation Dicer Control
---
# Novation Dicer Control

[The Novation Dicer](http://global.novationmusic.com/digital-dj/dicer) is a novel midi controller designed to sit in the 45 adapter slot of a Technics turntable. It was the first controller to get support within xwax.



## Setting up the Novation Dicers

{{ :dicerpair.jpg?300|}}

Connect the Dicers to your computer via USB and then launch xwax with the `--dicer` flag followed by the Dicer's ALSA device name.

e.g. `--dicer hw:Dicer`

(Note that version 1.3 or older uses the `-dicer` flag, with a single hyphen)

## Using the Novation Dicers



The Dicer has 3 different modes, selected by the three small buttons on the controller. Currently the third mode is unused.

Buttons with a cue point set to them are lit, those without are dimmed.

^  Mode  ^  Button  ^  Function  ^
| Cue | Dice Button | Jump to the specified cue point, or set it if unset. |
| ::: | Dice Button + Mode Button | Unset the specified cue point |
| Punch | Dice Button | "Punch" to the specified cue point, or set it if unset. Returns playback to normal when the button is released, much like slip-mode on Pioneer CDJs. |
| ::: | Dice Button + Mode Button | Unset the specified cue point |
| Unused |  n/a  |  n/a  |


## See also

  * [ Novation's Dicer related downloads page](http://us.novationmusic.com/support/product-downloads?product=Dicer)
  * [ The Dicer Programmer's Reference Document](http://d19ulaff0trnck.cloudfront.net/sites/default/files/downloads/4079/dicer-programmers-reference2.pdf)
