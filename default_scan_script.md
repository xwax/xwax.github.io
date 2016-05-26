---
layout: default
title: Default xwax Scan Script
---
# Default xwax Scan Script

## xwax 1.3 - Current

This version added the ability to extract BPM metadata from a correctly formatted filename. e.g. "`Jo - R Type (165 BPM).mp3`"
It also fixed the bug in the previous version where only lower-case file formats would be shown in the library.

<code bash scan>
#!/bin/sh
#
# Take a pathname as an argument and output a playlist to standard
# output and errors to standard error.
#
# The output format is repeated sequences of:
#
#   <pathname>\t<artist>\t<title>[\t<bpm>]\n
#
# If the tab (\t) or newline (\n) characters appear in a filename,
# unexpected things will happen.

PATHNAME="$1"

if [ -d "$PATHNAME" ]; then
	find -L "$PATHNAME" -type f |
		grep -iE '\.(ogg|oga|aac|cdaudio|mp3|flac|wav|aif|aiff|m4a|wma)$'
else
	cat "$PATHNAME"
fi |

# Parse artist and title information from matching filenames

sed -n '
{
# /[<ABnum>[.]] <artist> - <title>.ext
s:/\([A-H]\?[A0-9]\?[0-9].\? \+\)\?\([^/]*\) \+- \+\([^/]*\)\.[A-Z0-9]*$:\0\t\2\t\3:pi
t

# /<artist> - <album>[/(Disc|Side) <name>]/[<ABnum>[.]] <title>.ext
s:/\([^/]*\) \+- \+\([^/]*\)\(/\(disc\|side\) [0-9A-Z][^/]*\)\?/\([A-H]\?[A0-9]\?[0-9].\? \+\)\?\([^/]*\)\.[A-Z0-9]*$:\0\t\1\t\6:pi
t

# /[<ABnum>[.]] <name>.ext
s:/\([A-H]\?[A0-9]\?[0-9].\? \+\)\?\([^/]*\)\.[A-Z0-9]*$:\0\t\t\2:pi
}' |

# Extract BPM metadata from title (eg. "Ghostbusters (115.6 BPM)")

sed '
{
# BPM
s:\(.*\) *(\([0-9]\+\.\?[0-9]\+\) *BPM)$:\1\t\2:
}'
</code>

## xwax 1.2

This version of the xwax script only adds known file formats to the library. There is a known bug where only lower case file extensions are added to the library.

<code bash scan>
#!/bin/sh
#
# Take a pathname as an argument and output a playlist to standard
# output and errors to standard error.
#
# The output format is repeated sequences of:
#
#   <pathname>\t<artist>\t<title>\n
#
# If the tab (\t) or newline (\n) characters appear in a filename,
# unexpected things will happen.

PATHNAME="$1"

if [ -d "$PATHNAME" ]; then
	find -L "$PATHNAME" -type f |
		grep -E '\.(ogg|oga|aac|cdaudio|mp3|flac|wav|aif|aiff|m4a|wma)$'
else
	cat "$PATHNAME"
fi | sed -n '
{
# /[<num>[.]] <artist> - <title>.ext
s:/\([0-9]\+.\? \+\)\?\([^/]*\) \+- \+\([^/]*\)\.[A-Z0-9]*$:\0\t\2\t\3:pi
t

# /<artist> - <album>[/(Disc|Side) <name>]/[<ABnum>[.]] <title>.ext
s:/\([^/]*\) \+- \+\([^/]*\)\(/\(disc\|side\) [0-9A-Z][^/]*\)\?/\([A-H]\?[A0-9]\?[0-9].\? \+\)\?\([^/]*\)\.[A-Z0-9]*$:\0\t\1\t\6:pi
t

# /[<ABnum>[.]] <name>.ext
s:/\([A-H]\?[A0-9]\?[0-9].\? \+\)\?\([^/]*\)\.[A-Z0-9]*$:\0\t\t\2:pi
}
'
</code>


## xwax ? - 1.1

<code bash scan>
#!/bin/sh
#
# Take a pathname as an argument and output a playlist to standard
# output and errors to standard error.
#
# The output format is repeated sequences of:
#
#   <pathname>\t<artist>\t<title>\n
#
# If the tab (\t) or newline (\n) characters appear in a filename,
# unexpected things will happen.

PATHNAME="$1"

if [ -d "$PATHNAME" ]; then
	find -L "$PATHNAME" -type f
else
	cat "$PATHNAME"
fi | sed -n '
{
# /[<num>[.]] <artist> - <title>.ext
s:/\([0-9]\+.\? \+\)\?\([^/]*\) \+- \+\([^/]*\)\.[A-Z0-9]*$:\0\t\2\t\3:pi
t

# /<artist> - <album>[/(Disc|Side) <name>]/[<ABnum>[.]] <title>.ext
s:/\([^/]*\) \+- \+\([^/]*\)\(/\(disc\|side\) [0-9A-Z][^/]*\)\?/\([A-H]\?[A0-9]\?[0-9].\? \+\)\?\([^/]*\)\.[A-Z0-9]*$:\0\t\1\t\6:pi
t

# /[<ABnum>[.]] <name>.ext
s:/\([A-H]\?[A0-9]\?[0-9].\? \+\)\?\([^/]*\)\.[A-Z0-9]*$:\0\t\t\2:pi
}
'</code>
