```bash
## for non ideapad lenovo laptops, to get Wifi working from live USB
sudo rmmod ideapad_laptop
## during install, select install 3rd party tools
## if graphics don't work (nvidia geforce gtx 1050)
ubuntu-drivers devices ## list
sudo ubuntu-drivers autoinstall ## install

## if this doesn't still fix GUI
rm -rf  /lib/modprobe.d/blacklist_nvidia.conf
sudo update-initramfs -u
sudo reboot

## Others
## load module
sudo modprobe -v <module>
sudo gpu-manager

## Brightness fix
## add
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro K1000M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection

## to /usr/share/X11/xorg.conf.d/10-nvidia-brightness.conf

## don't disturb /etc/X11/xorg.conf, if the file is not present.
## If done already, boot with live USB and delete that file, cause GUI isn't showing up.
```
