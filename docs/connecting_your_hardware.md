---
layout: default
title: Documentation
---
# Connecting Your Hardware

## Setup Diagram

{{:hardware_diagram.png |}}

 Connect the output from your first turntable or CD player to the first stereo input on your audio interface. You may need to do this via an external preamp- see the section below if you are unsure if you require a preamp. It is important that you always ensure that the RCA plugs the correct way round when connecting your turntable to your audio interface, if you mix up the left and right plugs the track will play backwards within xwax.

Connect the corresponding stereo output on your audio interface to the desired channel on your DJ mixer. You should be plugging your interface into the input labelled "line" or "CD". Do not connect it to a phono input. To avoid unwanted pops being broadcast through your sound system completely lower the fader for that channel while connecting equipment or powering up your audio interface.\\ \\ Connect your audio interface to your computer as per usual. When possible connect it directly to the computer rather than via a USB hub or splitter. Note that xwax is not locked to any specific audio interface, you can use any card you want, providing you can get it working nicely with your linux computer. You can also use more than one interface with xwax at the same time.

Some DJ audio interfaces have a "thru" connection which allows you to play regular vinyl without having to rewire your setup, connect these to the phono inputs on your DJ mixer. 

## Compatible Interfaces

Any audio interface with 1 stereo input and output for turntable that you can get working with your Linux computer through ALSA, JACK or OSS is suitable for use with xwax. See our list of [[list_of_soundcards|tested soundcards]] for more info.

It is possible to use more than one audio interface at once with xwax, it may be more economical to buy multiple soundcards rather than one large one if you wish to use a larger number of turntables at once.
## Do I need a preamp?

A preamp is a small amplifier that makes the phono output of a turntable loud enough for use with xwax.

  * CD players, turntables with a built in preamp and other line level devices **do not** require a preamp.
  * Turntables when used with a DJ audio interface with a built in preamp (such as the NI Audio 4) **do not** require an additional preamp.
  * Turntables when used with an audio interface without a built in preamp **do** require an external preamp.

### Software preamps?

Since v1.4 xwax has a 'software preamp' feature (see the --phono option) to use an unamplified phono signal connected to a line-level interface. Using these methods may lead to a reduction in responsiveness which may (or may not) be noticeable when scratching.

There are other options for setting up a similar amplification with greater control:

#### Using a modified .asoundrc

Here is an example of a modified .asoundrc file that amplifies the signal before it reaches xwax. Draw elements of it and modify the .asoundrc for your card accordingly. While fiddly, this may be the best method.

<code c>#
# asoundrc to apply a "software preamp"
#

pcm.deck0 {
        type asym
        playback.pcm deck0_playback
        capture.pcm deck0_timecode
}

pcm.deck0_timecode {
        type plug
        # Apply 36dB gain, roughly equivalent to line/phono level
        ttable.0.0 63.0
        ttable.1.1 63.0
        slave.pcm "hw:Audio8DJ,0,0"
}

pcm.deck0_playback {
        type plug
        slave.pcm "hw:Audio8DJ,0,0"</code>

#### JACK Amplification

Any JACK application capable of amplifying a signal can be placed in the signal path between the audio interface and xwax. If you know a suitable application let us know!

#### Oliver's Timecode Gain Patch

There is a patch for xwax 1.3 which allows you to use xwax with quieter signals. See [[http://sourceforge.net/mailarchive/forum.php?thread_name=5150C184.40900%40oscille.ca&forum_name=xwax-devel|here]]. But really you should update to xwax 1.4 or later.