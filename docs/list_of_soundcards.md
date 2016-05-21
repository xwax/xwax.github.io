---
layout: default
title: Documentation
---
# Tested Soundcards

If you have tried other soundcards with xwax please add your findings here or report it to mailing list. 

You can find ALSA device names by entering ''cat /proc/asound/cards'' or ''aplay -l'' into the terminal.
## USB Soundcards


### Working USB Soundcards

^ Soundcard ^ Status ^ Tested with ^ Comment ^ ALSA Device Name ^
|[[http://www.behringer.com/EN/Products/UCA222.aspx|Behringer UCA222]]  | Working\\ (No Preamp)  | Ubuntu 11.04  | Ensure monitor switch is set to "off"  |  default  |
|[[http://www.behringer.com/EN/Products/UFO202.aspx|Behringer UFO202]]  | Working\\ (Requires Modification)  |  ?  | Requires [[http://mixxx.org/forums/viewtopic.php?f=6&t=2438|modification]] to work |  ?  |
| [[http://www.esi-audio.com/products/maya44usb/|ESI Maya44 USB]]  | Working\\ (No Preamp)  | Ubuntu 10.10  | May require a high -m value (15 or higher worked in testing) |  maya44_pair1 \\ maya44_pair2   |
| ::: | ::: | ::: | [[http://www.pogo.org.uk/~mark/linuxdj/maya44.asoundrc|.asoundrc file]] to provide stereo pairs | ::: |
| ::: | ::: | ::: | This card has no internal phono preamp and thus it is unsuitable for use with most turntables without an additional preamp. This is not an issue with CD players or other line level devices.  | ::: |
| [[http://www.hercules.com/uk/legacy/bdd/p/12/dj-console-mk2-virtualdj-djc-ed/|Hercules DJ Console Mk2]] | Working | Debian Squeeze | Requires a high output cartridge such as Shure M44-7 (9.5mV) to work well, Pickering 625-DJ (3mV) was not loud enough. Set Headphones Selection knob to Deck B to isolate output for second deck on phono outputs 3 and 4. | |
|Native Instruments Audio 4 DJ  | Working  | Ubuntu 10.10 \\  ->  \\ Ubuntu 12.10   | Set inputs to Phono: $ amixer -c [cardnumber] cset numid=1 1\\ Set inputs to Line: $ amixer -c [cardnumber] cset numid=1 0   |  plughw:Audio4DJ,0,0((Use of 'plughw:' is required))\\ plughw:Audio4DJ,0,1((Use of 'plughw:' is required))  |
|Native Instruments Audio 8 DJ  | Working  | Ubuntu 10.10  | |  plughw:Audio8DJ,0,0((Use of 'plughw:' is required))\\ plughw:Audio8DJ,0,1((Use of 'plughw:' is required))\\ plughw:Audio8DJ,0,2((Use of 'plughw:' is required))\\  plughw:Audio8DJ,0,3((Use of 'plughw:' is required))  |
|Native Instruments Traktor Audio 6  | Working  | Ubuntu 10.04\\  ->  \\  Ubuntu 11.10  |PASSTHRU on channel A: $ amixer -c T6 cset numid=1 on/(off)\\ PASSTHRU on channel B: $ amixer -c T6 cset numid=2 on/(off) |  T6_pair1 (Main) \\ T6_pair2 (Ch. A) \\ T6_pair3 (Ch. B)    |
|  :::  |  :::  |  :::  | switch PHONO/LINE on channel A: $ amixer -c T6 cset numid=3 on/(off)\\ switch PHONO/LINE on channel B: $ amixer -c T6 cset numid=4 on/(off) |  :::  |
|  :::  |  :::  |  :::  | [[http://www.pogo.org.uk/~mark/linuxdj/t6.asoundrc|.asoundrc file]] to provide stereo pairs |  :::  |
|Rane SL-1  | Working\\ (No working preamp under linux)  | Fedora (version?) ~2011  | Phono input does not work making it unsuitable for use with most turntables without an additional preamp. This is not an issue with CD players or other line level devices.  |  ?  |
| ::: | ::: | ::: | There are ALSA patches to enable the preamp. [[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-January/013856.html|1]] [[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-August/020784.html|2]] | ::: |
| [[http://www.adjaudio.com/ProductDetails.aspx?ItemNumber=1374|American Audio Versaport]]  | Working\\ (Only one preamp)  | Debian Squeeze 2012/09  | Needs a [[americanaudio_versaport_asoundrc_file|.asoundrc file]] to provide stereo pairs. |  versaport_pair1  \\ versaport_pair2   |
| ::: | ::: | ::: | It only have a preamp on Input 2, so you need external preamps to use both decks with standard turntables. | ::: |
| ::: | ::: | ::: | Volume is always turned down, use this command to turn the volume up before launching xwax : \\ $ amixer set -c [cardnumber] Speaker,0 100%,100% unmute | ::: |
| ::: | ::: | ::: | Available as OEM variants (MixVibes U-MIX44, Reloop Spin!, iScratch Mixlive, Omnitronix DDI, ...) | ::: |
|[[http://www.mixvibes.com/content/products/u-mix44|mixvibes umix44]]  | Working\\ (No Preamp)  | avlinux 6.0  | Available as OEM variants (American Audio Versaport Reloop Spin!, iScratch Mixlive, Omnitronix DDI, ...) |  umix44_pair1  \\ umix44_pair2   |
| ::: | ::: | ::: | Needs a [[mixvibes_umix44_asoundrc_file|.asoundrc file]] to provide stereo pairs | ::: |


### Broken USB Soundcards

^ Soundcard ^ Status ^ Tested with... ^ Comment^
| American Audio VMS4 | Buggy | Debian Squeeze | Distortion on phono preamps, supposedly fixed in later VMS4.1 model. Spinbacks don't work in xwax (related to input distortion?). Poor JACK performance, xruns even at large buffer sizes. |

## Firewire Soundcards

### Working Firewire Soundcards ##

Info on using firewire cards here. FIXME

^ Soundcard ^ Status ^ Tested with ^ Comment ^


# Other Soundcard Resources

Mark's [[http://www.pogo.org.uk/~mark/linuxdj/|Soundcard resources for Linux DJs]] page contains some useful information.