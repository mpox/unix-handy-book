
# Batch file operations

Delete all files which name has prefix `._`

	find /media/INTERNAL/ -type f -name '._*' -delete

Another way to delete files matching given pattern

	find /path/to/directory -type f -name '*[0-9]x[0-9]*[0-9]x[0-9]*.jpg' -exec rm {} +
