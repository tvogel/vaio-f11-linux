# Introduction #

It is essential to build the sony-laptop module with our patches for full hardware support. This includes:
  * ambient light sensor
  * backlight
  * special keys
  * g-sensor
  * keyboard backlight
  * battery meter

It interfaces with Sony's custom hardware interface.

# Details #

You need to patch your kernel with the latest patch, the latest of which are currently [here](http://www.absence.it/vaio-acpi/source/patches/?C=M;O=D), and occasionally mirrored to the downloads section on this site.

```
cd /usr/src/linux
curl http://vaio-f11-linux.googlecode.com/files/vaio-2.6.38.patch | patch -p1
```
_note: change .38 to .39 if you're on 2.6.39_
```
make menuconfig
```
be sure you have
```
CONFIG_SONY_LAPTOP=y
```
and then build and install your kernel
```
mount /boot
make && make install && make modules && make modules_install
```

Reboot and you should be all set.

**Report any issues to [this tracker](http://code.google.com/p/vaio-f11-linux/issues/detail?id=6).**