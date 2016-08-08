---
layout: default
title: Building xwax from Source
---

Installing xwax this way may seem daunting if you are new to the terminal but with a little help you should encounter no problems at all.

### Installation Walkthough

See also the [xwax installation video guide](https://www.youtube.com/watch?v=ylG3grTzhpc)

  - Install xwax's dependencies using your system's package manager (such as Synaptic, Aptitude or the Software Centre). If you are using a Debian or Ubuntu based distro you can install the required packages (including the library for ALSA support) by executing the following command in the terminal: `sudo apt-get install build-essential libasound2-dev libasound2 libsdl-ttf2.0-dev libsdl1.2-dev`
  - If you wish to build [JACK](http://jackaudio.org/) support and then run xwax on JACK you will need to install additional packages, which you can do with the command: `sudo apt-get install libjack-dev jackd qjackctl`
  - Ensure you have the desired [audio decoders](http://xwax.org/overview.html#decoder) installed so you can play mp3s and other formats. The default decoders are cdparanoia, mpg123 and ffmpeg. You can obtain these via your regular graphical package manager or by executing the following in the terminal: `sudo apt-get install cdparanoia mpg123 ffmpeg`
  - Download the xwax source from [the xwax download page.](http://xwax.org/download.html) Older versions can be found [in the xwax release archive.](http://xwax.org/releases/)
  - You now need to unpack the .tar.gz file, for this example we will assume you are installing xwax-1.4 and the file is in your ~/Downloads/ directory, *fix the path for the version you are installing*. `tar -xvf ~/Downloads/xwax-1.4.tar.gz` This will extract the contents of the tarball to a directory at `~/xwax-1.4/`
  - Navigate to the unpacked folder and read the contents of the INSTALL file for detailed instructions on how to compile xwax. For a standard installation with ALSA enabled, navigate to the xwax folder and then execute the configuration script: `cd ~/xwax-1.4/
./configure --prefix /usr --enable-alsa` To configure JACK support as well, add the --enable-jack option as follows: `./configure --prefix /usr --enable-alsa --enable-jack`
  - To build and install xwax, use the commands: `make
sudo make install`

**And you're done!**

  * If your build encounterd errors consult the install file for help, and run `make clean` to remove the previous build. The most likely problem is missing dependencies, so check you have them installed before running the configuration or build again. If you still have problems, contact the mailing list, or ask in IRC.

## Now that you have installed xwax...

You can try running xwax with ALSA by executing the following command in the terminal:
`xwax -a plughw:0` There is a good chance that this will not work with xwax >1.0 until you increase the scheduling priority of the audio playback thread. You can find help with this in the [Setting up real time audio priority for xwax](/setting_up_real_time_audio_priority_for_xwax) page of the wiki.

To run xwax with JACK, first run the QjackCtl control panel to configure and start the JACK server. On Debian or Ubuntu, this program should be on the Sound & Video menu. Then run xwax from the terminal with `xwax -j deck1` to start a deck with the JACK name 'deck 1'. You will need to connect the JACK ports in the Connections window for sound to be routed between xwax and your soundcard.

![JACK connection GUI](/images/xwax-jack-connections.png)

To open two decks and specify the path to music files in the /home/myusername/Music directory, you can use the command:

`xwax -j deck1 -j deck2 -l ~/Music/`

*Note it is wise to always run xwax in the terminal so you can read and learn from any error messages!*

#### Now you can move onto the configuration pages!
  * [Connecting your hardware](/connecting_your_hardware)
  * [Setting up real time audio priority for xwax](/setting_up_real_time_audio_priority_for_xwax)
  * [Writing your start-up command](/writing_your_start-up_command)
