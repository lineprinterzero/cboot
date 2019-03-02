# cboot
initramfs-tools scripts for making a very simple kexec-based bootstrap

## how do i use this?
1. create a debian chroot with debootstrap
2. chroot in
3. install kexec-tools
4. move the files files in this repo to /etc/initramfs-tools
5. run mkinitramfs -u
6. /initrd.img should now point to the assembled initramfs
7. boot the initramfs with the root= cmdline parameter pointing to a device with vmlinuz, initrd.img, and cmdline.txt in the root

## ...but why?
devices (such as the nextbook ares 8) that have an android bootloader typically require reflashing the boot partition to update the kernel, initramfs, and cmdline. this is fine if you're running android, but if you want to run something else, it can be cumbersome to have to reflash every time you change something (especially during debugging and development). the intended use of cboot is to be bundled, as a boot image, with an appropriate kernel and cmdline to load the kernel from a different partition on the device.
