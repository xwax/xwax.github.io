---
layout: default
title: Adding Togglable Relative Timecode Control
---

## Relative Timecode?

Relative timecode is where a DVS such as xwax only responds to the speed and direction the record is spinning and not the position of the needle. This means that you can no longer skip the record or needle drop to a new part of the song, this may be useful if you're scratching!

You can sort-of achieve this by flipping to the other side of the record so you have the incorrect timecode definition in xwax, however there is a small chance of xwax misinterpreting the timecode and repositioning the record. The following patch will add new timecode definitions that are relative only.

## The Patch

In order to add these to xwax you have to slightly edit the source code before [compiling xwax from this modified code](build_xwax_from_source). The file you need to edit is timecoder.c.

Open timecoder.c with a text editor find your preferred timecodes definition. Here we are using the Serato 2nd edition definition:

```c
{
    .name = "serato_2a",
    .desc = "Serato 2nd Ed., side A",
    .resolution = 1000,
    .flags = 0,
    .bits = 20,
    .seed = 0x59017,
    .taps = 0x361e4,
    .length = 712000,
    .safe = 707000,
    .lookup = false
},
```

Make a copy of this section and change the copy's `.name` value to `serato_rel`, change the `.length` value to `0` and change the `.desc` value to something descriptive.

Once done your code should look like this:

```c
{
    .name = "serato_2a",
    .desc = "Serato 2nd Ed., side A",
    .resolution = 1000,
    .flags = 0,
    .bits = 20,
    .seed = 0x59017,
    .taps = 0x361e4,
    .length = 712000,
    .safe = 707000,
    .lookup = false
},
{
    .name = "serato_rel",
    .desc = "Serato 2nd Ed., relative version,"
    .resolution = 1000,
    .flags = 0,
    .bits = 20,
    .seed = 0x59017,
    .taps = 0x361e4,
    .length = 0,
    .safe = 707000,
    .lookup = false
},
```

Now [compile xwax from this modified code](build_xwax_from_source). Once you have done this the new relative timecode definition will be available to select using the `-t` [start up flag](writing_your_start-up_command) as you would with any of the default timecodes. i.e. `-t serato_rel`

If you specify more that one timecode with the `-t` flag then can switch between the specified timecodes by pressing `Ctrl-F3` for deck A, `Ctrl-F7` for deck B or `Ctrl-F11` for deck C.

i.e.  ` $ xwax -t serato_2b -t serato_rel` etc
