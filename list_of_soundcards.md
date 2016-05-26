---
layout: default
title: Tested Soundcards
---
If you have tried other soundcards with xwax please add your findings here or report it to mailing list.

You can find ALSA device names by entering `cat /proc/asound/cards` or `aplay -l` into the terminal.

This list is avalible as JSON [here](soundcards.json).

# Working Tested Soundcards

<ul class="soundcard-list">
{% for card in site.data.soundcards %}
  <li><a href="#{{ card.name | slugify }}">{{ card.name }}</a></li>
{% endfor %}
</ul>

{% for card in site.data.soundcards %}
<div class="soundcard">
  <a href="#{{ card.name | slugify }}">
    <h2 id="{{ card.name | slugify }}">{{ card.name }}</h2>
  </a>

  <h3>Tested On:</h3>
  <ul>
{% for platform in card.tested_on %}
    <li>{{ platform }}</li>
{% endfor %}
  </ul>

  <h3>ALSA Device Names:</h3>
  <ul>
  {% for name in card.alsa_device_names %}
  <li><code>{{ name }}</code><br></li>
  {% endfor %}
  </ul>

  <h3>Notes:</h3>
  {{ card.comments | markdownify }}

  <h3>See also:</h3>
  <ul>
{% for link in card.links %}
    <li><a href="{{ link }}" target="_blank">{{ link }}</a></li>
{% endfor %}
  </ul>
</div>
{% endfor %}
<br>

# Broken Soundcards

Soundcard           | Status | Tested with... | Comment
---                 | ---    | ---            | ---
American Audio VMS4 | Buggy  | Debian Squeeze | Distortion on phono preamps, supposedly fixed in later VMS4.1 model. Spinbacks don't work in xwax (related to input distortion?). Poor JACK performance, xruns even at large buffer sizes.


# Other Soundcard Resources

Mark's [Soundcard resources for Linux DJs](http://www.pogo.org.uk/~mark/linuxdj/) page contains some useful information.
