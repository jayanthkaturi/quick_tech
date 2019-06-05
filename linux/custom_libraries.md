### Debian
```bash
## 1
apt download <package>
dpkg -x package.deb <package_dir> ## (or) ar x <package>.deb
## set $PATH to bin/ sbin/ in <package_dir>/usr/ and $LD_LIBRARY_PATH to lib/ lib64/ there

## 2
apt-get source package
cd package
./configure --prefix=$HOME
make
make install
```

### RHEL
```bash

## Download rpm package
cd <path_to_custom_library_location>
## -i extract, -d create directories whenever necessary
rpm2cpio <path_to_package_rpm> | cpio -id

## add <path_to_custom_library_location>/usr/bin (or)
## <path_to_custom_library_location>/usr/sbin locations to $PATH

## add <path_to_custom_library_location>/usr/lib (or)
## <path_to_custom_library_location>/usr/lib64 locations to $LD_LIBRARY_PATH

which <package_name>
```
