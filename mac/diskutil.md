# Diskutils on Mac

List entire disks structure

	diskutil list

Extend CoreStorage partition size to max available 

	diskutil coreStorage resizeVolume /dev/disk3 0

Create CD-ISO image file

	hdiutil makehybrid -o ~/Desktop/image.iso ~/path/to/folder/to/be/converted -iso -joliet

Create virtual disk in memory
Tworzenie wirtualnego dysku w pamięci (500 MB)

	hdiutil attach -nomount ram://1024000

> 102400 = 500 MB, disk is unformatted
> device name is printed on stdout, example:  /dev/disk3

Formatting a disk

	diskutil erasevolume HFS+ 'Ram Disk' /dev/disk3

Disconnecting device (eject)

	hdiutil detach /dev/disk
