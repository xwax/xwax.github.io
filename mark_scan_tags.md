---
layout: default
title: Mark's scan script with BPM tags
---
Scans using the regular script, but adds additional BPM information extracted from file tags. Use bpm-tools to tag files automatically.

```bash
#!/bin/bash
#
# Wrapper around xwax scan script which adds BPM field and sources
# it from the tags present in the file.
#

PATHNAME="$1"

if [ -x /usr/local/libexec/xwax-scan ]; then
	SCAN=/usr/local/libexec/xwax-scan
elif [ -x /usr/libexec/xwax-scan ]; then
	SCAN=/usr/libexec/xwax-scan
else
	SCAN=/usr/share/xwax/xwax-scan
fi

if [ -d "$PATHNAME" ] && [ -w "$PATHNAME" ]; then
	CACHE="$PATHNAME/.xwax-cache"
else
	CACHE=""
fi

# Use the cache if present

if [ -n "$CACHE" ] && [ -f "$CACHE" ]; then
	cat "$CACHE"
	exit 0
fi

# Invalidate the cache on any errors

trap 'rm -f "$CACHE"' 0

IFS=$'\t'
"$SCAN" "$1" | while read FILE ARTIST TITLE; do
	case "$FILE" in
	*.flac)
		BPM=`metaflac --show-tag=BPM "$FILE" | tail -1l | sed -e 's/BPM=//'`
		;;
	*.mp3)
		BPM=`id3v2 -R "$FILE" | sed -n 's/^TBPM.*: \([0-9\.]\+\)/\1/p'`
		;;
	*.ogg)
		BPM=`vorbiscomment "$FILE" | sed -n 's/^BPM=//p' | tail -1l`
		;;
	*.m4a)
		BPM=`AtomicParsley "$FILE" -t 2>/dev/null | sed -n -E 's/Atom "tmpo" contains: *([0-9]+).*/\1/p'`
		;;
	esac

	printf "%s\t%s\t%s" "$FILE" "$ARTIST" "$TITLE"

	if [ -n "$BPM" ]; then
		printf "\t%s" "$BPM"
	fi

	printf "\n"
done | if [ -n "$CACHE" ]; then
	tee "$CACHE"
else
	cat
fi

# Confirm that the cache can be used

trap "" 0
```
