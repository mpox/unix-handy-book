# Loop devices

List all partitions from given disk image file

	fdisk -lu binary.img
	
or

	parted -s "${IMG_FILE}" unit b print

Register /dev/loopX together with it partitions /dev/loopX1, /dev/loopX2... from given file

	losetup --partscan --show --find archlinux-arm8.img

> Device name (rg /dev/loop1) is printed on stdout

Searches for partition table in given range

	losetup --offset $((512*2048)) --sizelimit $((512*817152)) --show --find binary.img

Unmount loop device

	sudo losetup -d /dev/loop2

Mount partition, looking in file from given offset

	mount -t vfat -o loop,offset=512 "${IMG_FILE}" /mnt/

Allocate 15 NBD devices

	modprobe nbd max_part=15

Mount QCOW (Qemu) image using NBD

	qemu-nbd -c /dev/nbd0 dist/polomagellan-0.4-devarch.qcow
	mount /dev/nbd0p2 root

Unmount QCOW image

	umount root
	qemu-nbd -d /dev/nbd0
