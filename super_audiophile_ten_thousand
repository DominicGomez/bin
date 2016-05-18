#!/usr/bin/bash

# Copyright (c) 2015 Dominic Gomez
#
# SUPER AUDIOPHILE TEN THOUSAND
#
# A simple script to convert* anything** to a lossless audio file.
#
# * To 'convert' a file 'a' to a lossless audio file is to create a copy of 'a'
# with its extension replaced by '.flac'. If 'a' does not have an extension,
# '.flac' is appended to its name.
#
# ** Like files and stuff.

# The file extension given to the converted file.
# AUDIOPHILE_APPROVED_EXTENSION=".wav"
AUDIOPHILE_APPROVED_EXTENSION=".flac"

# Command line flags.
verbose=false
recursive=false

# convert infile outfile
# Copy infile and give it outfile's name.
function convert {
    if [[ $verbose == true ]]; then
        echo "Converting \"$1\" to \"$2\"..."
    fi
    cp "$infile" "$outfile" 2>/dev/null
}

# Process arguments in order. Single pass.
for i in "$@"; do
    if [[ -e $i ]]; then # Is this a file?
        infile="$i"
        outfile="${infile%.*}""$AUDIOPHILE_APPROVED_EXTENSION" # New extension.
        if [[ -r $infile ]]; then # Can I read it?
            if [[ -f $infile ]]; then # Is it a regular file?
                convert "$infile" "$outfile"
            elif [[ -d $infile ]]; then # Or is it a directory?
                if [[ ! -z $recursive ]]; then # Should we recurse?
                    echo ">>> Recursion not yet implemented."
                else
                    echo "ERROR: \"$i\" is a directory. Try running with -r"
                    exit 1
                fi
            fi
        else
            echo "ERROR: Cannot open \"$i\" for reading."
            exit 1
        fi
    else
        echo "ERROR: \"$i\" does not exist."
        exit 1
    fi
done
