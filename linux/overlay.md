# Overlayed filesystems

Example 1

    mount -t overlay -o lowerdir=./lower,upperdir=./upper,./work overlay ./mount

Example 2

    mount -t overlay -o lowerdir=/var,upperdir=/writable/var,workdir=/writable overlay /var


