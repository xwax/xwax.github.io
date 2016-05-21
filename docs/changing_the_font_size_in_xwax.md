---
layout: default
title: Documentation
---
#  Changing the font size in xwax

**Update:** instead of patching, you can use xwax's scalable UI as of version 1.4. See ''man xwax'' for information and examples.

In order to change the font sizes in xwax you have to slightly edit the source code before [[build_xwax_from_source|compiling xwax from this modified code]]. The file you need to edit is interface.c, within you will find several variable you can tweak to change the size of your fonts.

Open interface.c with a text editor and edit the following section of code:

<code C>
/* Font definitions */

#define FONT "DejaVuSans.ttf"
#define FONT_SIZE 10
#define FONT_SPACE 15

#define EM_FONT "DejaVuSans-Oblique.ttf"

#define BIG_FONT "DejaVuSans-Bold.ttf"
#define BIG_FONT_SIZE 14
#define BIG_FONT_SPACE 19

#define CLOCK_FONT FONT
#define CLOCK_FONT_SIZE 32

#define DECI_FONT FONT
#define DECI_FONT_SIZE 20

#define DETAIL_FONT "DejaVuSansMono.ttf"
#define DETAIL_FONT_SIZE 9
#define DETAIL_FONT_SPACE 12
</code>