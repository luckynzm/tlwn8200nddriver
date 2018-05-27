# TP-Link WN8200ND V2 driver for Linux

This is the Linux drivers for TP-LINK WN8200ND V2.  After many tries i finally managed to get it working

# Explanation

The V2 model of the Wifi adapter uses **RTL8192EU** (unlike the original which uses RTL8192CU). However the drivers that can be found on TP-LINK's site won't compile under Ubuntu 18.04 (or any newer Linux kernel for that matter) But the [rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver) doesn't recognized the usbid of this card (**2357:0126**) so what i did is i copied **osdep/linux/usb_intf.c** to rtl8192eu-linux-driver and suddenly everything worked

# Installation

You will need build-essentials (or base-devel if you are on Arch) or kernel headers, compiler...
   ```shell
   $ git clone https://github.com/luckynzm/tlwn8200nddriver.git
   $ cd tlwn8200nddriver
   $ sudo dkms add .
   $ sudo dkms install rtl8192eu/1.0
   
   This will take some time
   
   # nano /etc/modules
   Put the 8192eu on the end of the file
   # reboot (if you want to).

```

# Bugs
The activity LED on the usb adapter doesn't turn on
The kernel spams alot of messages during startup about the driver

# Copyright
I don't really know who has the copyright to this driver but i would like to thank the contributors of [rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver) for fixing the driver for newer kernels
I felt the need to share this driver because i've seen a lot of people can't get this adapter working on Linux
