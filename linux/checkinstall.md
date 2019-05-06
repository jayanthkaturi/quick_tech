```bash
./configure [OPTIONS]
make
## make install is default, and not required. make [something] should be mentioned
## ftrans=yes -> file system translation so package won't touch your actual filesystem
sudo checkinstall --install=no --fstrans=yes make install
## to create a debian package
sudo checkinstall -D

## using fakeroot
fakeroot checkinstall -D
```
