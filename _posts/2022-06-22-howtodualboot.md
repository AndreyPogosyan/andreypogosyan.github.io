---
title: How To DualBoot Windows and Linux on the Same Hard Drive
date: 2022-01-22 22:10:00 -400
categories: [aws, security]
tags: [aws,security]      # TAG names should always be lowercase
---

<iframe width="686" height="386" src="https://www.youtube.com/embed/ixsi-Tmaz80" title="How to Dual Boot Linux and Windows on the same hard drive, featuring EndeavourOS and Windows 10." frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

In this video, we go over the installation of EndeavourOS and Windows 10.

Dual Booting Widows 10 and Linux is quite easy but I don’t recommend that you dual boot both Windows and Linux on the same hard drive. It is a better idea to use a dedicated hard drive for each OS, but in the case where you can’t and you want to use Linux while still being able to boot into Windows only on a single hard drive, you can, using the method below:

* Install Windows 10 and allocate only half of the space for the creation of the windows partitions. In our example, we used a 120GB hard drive and split it down the middle, 60GB of Windows and 60GB for Linux. Of course, feel free to chose your own partition size.
* Once Windows 10 is installed, boot with the EndeavourOS and go through the installation until you get to the partitioning. Create three partitions, one of these partitions is optional:
   * EFI Boot partition /boot/efi (if using EFI or create a /boot if you’re on MBR)
     * <b>NOTE:</b> In any case, when we create a /boot/efi, the system will also configure /boot in order to store the kernel and the initramfs. the EFI system partition (ESP) will contain the EFI boot loader.
     * Root (/)
     * Linux Swap (recommended but optional)
* Once the Linux OS is installed, we can safely reboot and we should be presented with a GRUB menu where we can see both the Linux and Windows installations. Using the GRUB menu, we can then pick and chose what OS to boot into.