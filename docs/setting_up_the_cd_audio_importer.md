---
layout: default
title: Setting Up the CD Audio Importer
---
xwax's standard import script allows importing tracks directly from an audio cd

on the xwax command line specify `-l /path/to/cdimportfolder/`

you must then create cdimportfolder.

in this folder create a series of files with names like this track1.cdaudio, track2.cdaudio etc
the file track1.cdaudio must contain the number 1
the file track2.cdaudio must contain the number 2
...
the file track99 must contain the number 99

(the maximum number of tracks on an audio cd is 99)

the importer works like this:

the dummy files in the folder allow the importer script to list the files in the library,
 the importer then calls cdparanoia with the contents of the file as the track number to extract.
the output from cdparanoia is then piped to xwax.

a premade folder of dummy files is avalable in the early binary releases of xwax.
