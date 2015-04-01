# Introduction #
There are a few necessary changes to get the NVIDIA driver up and running. Make sure you are using version >=195.36.15.

# EDID Configuration #

As of Feb 9, the latest NVIDIA drivers do not support the screen on the Vaio automatically. It is required to explicitly specify the EDID dataset which actually is available via the /proc filesystem.

Add the following two lines to the "Device" section of your `xorg.conf or add a file inside of /etc/X11/xorg.conf.d`:
```
    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
```

Be sure to follow the [KernelSupport](KernelSupport.md) instructions to have backlight control.

### Sample xorg.conf ###
For example, a complete "Device" section might look like this:
```
Section "Device"
        Identifier      "InternalCard"
        Driver          "nvidia"
        Option          "ConnectedMonitor" "DFP-0"
        Option          "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
EndSection
```

# Power Management #

You may want to add this line, as well, so that your Vaio simmers down every once in a while:

```
        Option          "RegistryDwords"          "EnableBrightnessControl=1;PowerMizerEnable=0x1;PerfLevelSrc=0x3333;PowerMizerLevel=0x3;PowerMizerDefault=0x3;PowerMizerDefaultAC=0x3"
```

# Install uvesafb #

  * [Ubuntu directions](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)
  * [Gentoo directions](http://en.gentoo-wiki.com/wiki/Framebuffer)
  * [Arch directions](http://wiki.archlinux.org/index.php/Uvesafb)