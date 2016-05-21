---
layout: default
title: Oligau's Scan Script
---
This script is based on iggy's scan script. It's modified to fallback to classic filename parsing if no artist/trackname is found in the tag.

```bash
#!/bin/bash
#
# Take a pathname as an argument and output a playlist to standard
# output and errors to standard error.
#
# The output format is repeated sequences of:
#
#   <pathname>\t<artist>\t<title>[\t<bpm>]\n
#   <pathname>\t<artist>\t<title>[\t<bpm>]\t<genre>\t<date>\t<album>\n
#
# If the tab (\t) or newline (\n) characters appear in a filename,
# unexpected things will happen.

# DEBUG
#set -x

PATHNAME="$1"

oIFS=$IFS
IFS="
"

if [ `echo "$PATHNAME" | grep -q '.xwaxpls' ; echo $?` -eq 0 ] ; then
	cat "$PATHNAME"
	exit 0
fi

if [ "$(echo \"$*\" | grep -q -- '--find' ; echo $?)" == 0 ] ; then
	# support generating playlists based on finding for terms
	# must be specified like
	# $ xwax-scan /path/to/music/dir --find search_term1 search_term2...

	# build find args
	fargs=""
	pathname=$1
	shift # pop off the music path that we are searching
	while [ $# -gt 0 ] ; do
		case "$1" in
		--find)
			;; # skip --find
		*)
			# assume everything else is a word to search for
			fargs="$fargs|$1"
			;;
		esac
		shift
	done
	fargs="$(echo $fargs | sed 's:^|::')"
	files=`find -L "$pathname" -type f -regextype posix-extended -iregex .*\($fargs\).*.\(ogg\|oga\|aac\|cdaudio\|mp3\|flac\|wav\|aif\|aiff\|m4a\|wma\)$`
elif [	"$(echo \"$*\" | grep -q -- '--locate' ; echo $?)" == 0 ] ; then
	# xwax-scan --locate lavice
	# xwax-scan --locate '\(lavice\|cyantific\)'
	files=`locate -i --regexp "$2.*\(ogg\|oga\|aac\|cdaudio\|mp3\|flac\|wav\|aif\|aiff\|m4a\|wma\)$"`
elif [ -d "$PATHNAME" ] ; then
	# arg is a directory, they probably want all the music files below it
	files=`find -L "$PATHNAME" -type f | grep -iE '\.(ogg|oga|aac|cdaudio|mp3|flac|wav|aif|aiff|m4a|wma)$'`
else
	files=$PATHNAME
fi


if [ -x `which mediainfo` ] ; then
       for f in $files ; do
		#echo mediainfo --Inform=\"General\;%CompleteName%\t%Performer%\t%Track%\n\" \"$f\" >&2
		#echo mediainfo --Inform=\"General\;%BPM%\t%Genre%\t%Recorded_Date%\t%Album%\n\" \"$f\" >&2
                echo -e $f >&2
                title=`mediainfo --Inform="General;%Performer%\t%Track%" "$f"`
                bpm=`mediainfo --Inform="General;%BPM%" "$f"`
		extra=`mediainfo --Inform="General;%Genre%\t%Recorded_Date%\t%Album%\n" "$f"`
		if [[ $title != "\t" ]]
                then echo -e $f"\t"$title"\t"$bpm"\t"$extra
                else echo -e $f |
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
                fi
	done

	exit 0
fi


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

```
