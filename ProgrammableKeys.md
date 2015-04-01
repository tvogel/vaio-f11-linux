# Introduction #

The keys on the upper right of the keyboard either do not work or are mapped incorrectly. You need [KernelSupport](KernelSupport.md) as well as the following udev instructions.

# Details #

We need to add a key remapper for udev so that X gets codes it can deal with. Download the module-sony keymap into /lib/udev/keymaps:

```
$ sudo -s
# cd /lib/udev/keymaps
# rm -f module-sony
# wget http://vaio-f11-linux.googlecode.com/files/module-sony
```

You then need to tell udev to load the keymap:

```
# echo 'ENV{DMI_VENDOR}=="Sony*", KERNELS=="input*", ATTRS{name}=="Sony Vaio Keys", RUN+="keymap $name module-sony"' >> /lib64/udev/rules.d/95-keymap.rules
# exit
$
```

You should then be all set.

Note that this maps Assist to mute, S1 to back, and Vaio to next. You can change these at your will in the module-sony file.