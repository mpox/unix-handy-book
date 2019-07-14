# RPi on qemu

1. apt install `qemu-system-arm`
2. checkout repository
        &nbsp;

        git clone https://github.com/dhruvvyas90/qemu-rpi-kernel.git


3. Convert raw image to Qemu format
        &nbsp;

        qemu-img convert -f raw -O qcow2 2017-08-16-raspbian-stretch-lite.img raspbian-stretch-lite.qcow

4. Resize image
        &nbsp;

        qemu-img resize raspbian-stretch-lite.qcow +6G

    qemu-img info <img>

4. Run

	qemu-system-arm -kernel /data/qemu-rpi-kernel//kernel-qemu-4.14.50-stretch -append "root=/dev/sda2 panic=1 rootfstype=ext4 rw" -hda litianpi.qcow -cpu arm1176 -m 256 -M versatilepb -nographic -dtb versatilepb.dtb -redir tcp:5022::22 -no-reboot

another example
```
qemu-system-arm -kernel /data/qemu-rpi-kernel//kernel-qemu-4.14.50-stretch -append "root=/dev/sda2 panic=1 rootfstype=ext4 rw"	
  -hda litianpi.qcow
  -cpu arm1176 -m 256 -M versatilepb -dtb versatilepb.dtb
  -nographic -no-reboot -redir tcp:5022::22
```

