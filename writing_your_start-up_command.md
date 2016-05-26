---
layout: default
title: Writing  Your Startup Command
---

# Writing Your Startup Command

xwax is launched from the terminal by entering a command consisting of `xwax` followed by a series of flags that tell xwax what settings to use, where to scan for you music, etc. This page will walk you though the various flags and help you decide which ones you ought to use.

## An Explanation of the Flags

Here's a explanation of all the flags for xwax. Don't worry if it seems a bit much- you won't need all of these and further down there is a section selecting the flags you need.

The ordering of options is important. Most options apply to subsequent music libraries or decks, which can be given multiple times. See the xwax man page (enter `man xwax` into the terminal) for examples.

| Runtime Flag | Flag Function |
| ------------ | ------------- |
| `-l` __path__                  | Scan the music directory or playlist at the given path. \\ The directory/playlist specified here will show up in the list of "crate" to the left of the xwax interface. See below for a script you may find useful for passing music directories to xwax                                                                                                                                         |
| `-t` __name__                  | Use the named timecode for subsequent decks. Multiple timecodes can be specified for a deck or decks as can be switched between live using the `shift` + `F3`/`F7`/`F11` key combo for decks 0, 1 and 2 respectively. \\ The available timecodes are: `serato_2a` (the default if no timecode is specified), `serato_2b`, `serato_cd`, `traktor_a`, `traktor_b`, `mixvibes_v2`, `mixvibes_7inch` |
| `-33`                          | Set the reference playback speed for subsequent decks to 33 and one third revolutions per minute. This is the default which xwax will use for decks with neither `-33` or `-45` set.                                                                                                                                                                                                             |
| `-45`                          | Set the reference playback speed for subsequent decks to 45 revolutions per minute.                                                                                                                                                                                                                                                                                                              |
| `-c`                           | Protect subsequent decks against certain operations (such as track loading) during playback. This will stop you from accidentally loading a track onto a playing deck!                                                                                                                                                                                                                           |
| `-u`                           | Allow all operations on a deck during playback. This is the inverse of the -c option, and is the default.                                                                                                                                                                                                                                                                                        |
| `-i` __path__                  | Use the given importer executable for subsequent decks. Not specifying an import executable will cause xwax to use the default import executable.                                                                                                                                                                                                                                                |
| `-s` __path__                  | Use the given scanner executable to scan subsequent music directories or playlists specified with the `-l` flag.                                                                                                                                                                                                                                                                                 |
| `-k`                           | Lock  into RAM any memory required for real-time use.  This includes audio tracks held in memory which can be large.  Use ulimit -l to raise the kernel's memory limit to allow this.                                                                                                                                                                                                            |
| `-q` __n__                     | Change the real-time priority of the process. A priority of 0 gives the process no priority, and is used for testing only. The default value is 80. (?)                                                                                                                                                                                                                                          |
| `-g` **n**x**n**[+**n**+**n**] | Change the geometry of the display. This size and position is passed to SDL, which may use it to set the display mode, or the size of an X window. Typically this will dictate the starting size of the xwax window                                                                                                                                                                              |
| `-h`                           | Display the help message and default values. \\ More info can be found on the xwax man page, excessed by entering `man xwax` into the terminal.                                                                                                                                                                                                                                                  |

### ALSA Device Options

The following options are available only when xwax is compiled with [ALSA](http://www.alsa-project.org/main/index.php/Main_Page) support.

| Runtime Flag | Flag Function |
| ------------ | ------------- |
| `-a` __device__ | Create a deck which uses the given ALSA device (eg. plughw:0). |
| `-r` __n__ | Set the sample rate in hertz for subsequent decks. If left blank xwax will use the default value. |
| `-m` __n__ | Set the ALSA buffer time in milliseconds for subsequent decks. If left blank xwax will use the default value of 8ms. |

### JACK Device Options

The following options are available only when xwax is compiled with [JACK](http://jackaudio.org/) support.

| Runtime Flag | Flag Function |
| ------------ | ------------- |
| `-j` __name__ | Create a deck which connects to JACK and registers under the given name. You need to set up the JACK server before launching xwax with this flag. |

xwax does not set the sample rate for JACK devices; it uses the sample rate given in the global JACK configuration.

### OSS Device Options

The following options are available only when xwax is compiled with [OSS](http://en.wikipedia.org/wiki/Open_Sound_System) support.

| Runtime Flag | Flag Function |
| ------------ | ------------- |
| `-d` __pathname__ | Create a deck which uses the given OSS device (eg. /dev/dsp).|
| `-r` __n__ | Set the sample rate in hertz for subsequent decks. |
| `-b` __n__ | Set the number of OSS buffers for subsequent decks. |
| `-f` __n__ | Set the OSS buffer size (2%%^%%n bytes). |

## Selecting The Flags You Need

Necessities + examples, etc FIXME

## Saving Your Start Up Command For Later use

You could save your start up command to a text document and paste it into the terminal when you want to use it, but here are some other, more practical, options.

### Saving Your Command as a Bash Alias

Explain, save to .bashrc etc. FIXME

### Creating a Bash Script That Launches xwax

Explain. Also explain you can assign an alias to the script itself. FIXME

## A Useful Script For Specifying Music Directories

Each directory within music will show up as a crate inside xwax, etc. FIXME

Should this be it's own page?

```bash
#!/bin/sh

# The loop
# Replace ~/Music/* with the location of the directories you wish to scan FIXME
PLAYLISTS=
for P in ~/Music/*; do
    PLAYLISTS="-l $P $PLAYLISTS"
done

# Replace this start up command with your own, except keeping $PLAYLISTS in place of the -l flag
xwax -a plughw:Audio4DJ,0,0 -a plughw:Audio4DJ,0,1 $PLAYLISTS
```


# Hey! This Isn't Finished!

Fix it then! https://github.com/xwax/xwax.github.io
