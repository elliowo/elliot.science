+++
title = "Migrating/copying Linux system to a new drive"
date = 2022-01-27
[extra]
math = false
[taxonomies]
categories = ["misc"]
tags = ["gentoo","linux"]
+++

# Preface
Getting a new drive, computer or even switching filesystem can be a pain when having to install
an operating system to the drive, but is not required when running Linux. A properly configured Linux
system should not require reinstalling and reconfiguring the system to it's previous state is time
consuming.

It is also useful for when encrypting a drive with LUKS, which to my 
knowledge will wipe the data on the drive. This post is also a future note for myself since I have had 
to perform this a few time.

### Copying the data
**Make sure your new drive has been prepared properly, I recommend [Gentoo Handbook](https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Disks) and please 
use your knowledge of your system because there will be changes depending on system.**

For this you require rsync to be installed on your system and is common on most.
```sh
rsync -aAXv /source/directory /destination/directory
```
breakdown: 
- a - archive mode
- A - preserve ACLs
- X - preserve extended attributes
- v - verbose

### After clone
You will have to do a few thing to get the system working, which is normal during Arch and Gentoo 
installs.

To get the system to boot you will want to get you /etc/fstab correct, this file contains the mount points 
of the partitions you created earlier. To get the drive names and partitions do `fdisk -l`, you want to 
use these retrospectively to to your fstab. I also recommend using `noatime` on drives to get a bit more 
speed out of them. Mine are below.

```sh
/dev/nvme0n1p1          /boot           vfat            noauto,noatime  1 2
/dev/nvme0n1p3          /               ext4            noatime         0 1
/dev/nvme0n1p2          none            swap            sw              0 0
```

Once you have done this you should just need your bootloader setup. I personally would delete the old grub from
the /boot directory and then run when using UEFI

UEFI
```sh
mount /boot
grub-install --target=x86_64-efi --efi-directory=/boot
grub-mkconfig -o /boot/grub/grub.cfg
```

LEGACY BIOS
```sh
grub-install /dev/sda(whatever partition boot is)
grub-mkconfig -o /boot/grub/grub.cfg
```
