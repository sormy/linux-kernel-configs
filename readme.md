Linux Kernel Config Database
============================

Kernel configs below could be used for Gentoo Linux installation to speedup initial kernel configuration.

Amazon Linux AMI 2015.09.1
--------------------------

This original kernel config provided by Amazon.

Supports: HVM and PVM
Config: config-4.1.10-17.31.amzn1.x86_64

Boot loader for PVM is not required. Just put it in /boot/grub/menu.lst:
```
# created by imagebuilder
default=0
fallback=1
timeout=1
hiddenmenu

title Amazon Linux 2015.09 (4.1.10-17.31.amzn1.x86_64)
root (hd0)
kernel /boot/vmlinuz-4.1.10-17.31.amzn1.x86_64 root=LABEL=/ console=hvc0 
initrd /boot/initramfs-4.1.10-17.31.amzn1.x86_64.img
```

For Amazon Enhanced Networking (10Gbps) you need additionally to enable:
```
CONFIG_IXGBEVF=y
```

For fresh udev it could be required to unset `CONFIG_FW_LOADER_USER_HELPER` kernel option which is set by default.

```
sed 's/^CONFIG_FW_LOADER_USER_HELPER/#\0/' -i path_to_config_file
``
