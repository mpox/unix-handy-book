# INITRD

Unpack gzip-a i and delete compressed original

	gzip -d initrd.gz

Unpack initrd

	cpio -i --file ../initrd

> initrd is taken from parent directory and is unpacked to current directory

or

	cpio -vid < initramfs-linux.img

PAck all files from current directory to file `new_initrd_file` in parent directory

	find | cpio -H newc -o > ../new_initrd_file

or with `gzip`

	find . | cpio -H newc -o | gzip > ../myinitrd.gz
