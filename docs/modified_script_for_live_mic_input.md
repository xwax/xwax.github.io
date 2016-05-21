---
layout: default
title: Ewan's Scan + Import Scripts for Recording and Scratching a Live Input
---
# Ewan's Scan + Import Scripts for Recording and Scratching a Live Input

## Usage

The following change to your scan script will make xwax record a live into one of the decks whenever you load a dummy track with the ''".live"'' file extension into that deck.

## Implementation

This script requires you to have the program ''sox'' installed as well as a free audio input for you to record from. This example uses the microphone input on a laptop!

### Import Script

For live mic scratching craziness append the folowing to your import script:

```sh
*.live)
    echo "Starting live capture..." >&2
    exec sox --show-progress -2 -t alsa hw:Intel  -t raw --channels 2 --rate "$RATE" - trim 0 0:59
    ;;
```

You will almost certainly need to change this to use the correct ALSA device name for the soundcard you want to record from.  //(Is it possible to use JACK?)// You may also wish to change the trim or edit the length of time ''sox'' records for.

You probably don't need --show-progress but it helps for debugging.

### Scan Script

In the scan script you will need to add "''.live''" to the list of valid file extensions so that the dummy files show up in xwax's library. Here is an example of what that portion of your scan script may look like after you have done this:

```sh
PATHNAME="$1"

if [ -d "$PATHNAME" ]; then
	find -L "$PATHNAME" -type f |
		grep -iE '\.(ogg|oga|aac|cdaudio|mp3|flac|wav|aif|aiff|m4a|wma|live)$'
else
	cat "$PATHNAME"
fi |
```

(Note how ''live'' has been appended to the list of file extensions in the 5th line)
### Dummy Tracks

The dummy tracks don't need to be actual tracks, they can be anything so long as they have the file extension ''".live"''. Just save two blank text documents as "''micinput1.live''" and "''micinput2.live''"" or something similar and then put them in a directory with your music that xwax is set to scan.

To activate mic input, just load one of these files. xwax won't load a track that's already loaded into a deck so you need to alternate between the two dummy tracks in order to record twice in a row.


If you have a solution that works better than sox, or anything else to add, please post it here.




- ewan.
