```
## Using live USB
## /dev/sda1 is the device (bootable USB)
sudo mount /dev/sda1 /mnt/somefolder
sudo mount --bind /dev /mnt/somefolder/dev
sudo mount --bind /sys /mnt/somefolder/sys
sudo mount --bind /proc /mnt/somefolder/proc
sudo mount --bind /run /mnt/somefolder/run
sudo chroot /mnt/somefolder
```

```
## Edit boot config and append 'rw init=/bin/bash' to line starting with linux
## When recovery mode mount / as ro (readonly)
sudo mount -o remount,rw /
```
