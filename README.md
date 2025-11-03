# Zakiyahm1.gihub.io
#Installation Process

Install arch from torrent

Created a new VM on workstation to host Arch Linux; from there I followed the recommended initial setup instructions that were provided

Made sure was connected to internet with ping archlinux.org command,
Set the date/time
Started to partition the disks

I used the default name setting for my disks and wanted a more accurate naming system. I googled the commands used to rename disk partitions because I had forgotten on how to do that
**mkswap -L swap /dev/sda2** (This for my swap partition)

Mounted the file systems, following that, install the base Linux kernel.
I ran into a problem when installing the kernel; I got a "Failed to install packages to new root" error.
I re-pinged archlinux.org to make sure I had a connection and tried to reinstall using a different command: **pacstrap /mnt base linux linux-firmware vim**. This command worked better than the one provided through the wiki.

I followed the commands for the Fstab, chroot, set time, localization, created a hostname and password for my new VM. 

After hearing a classmate express problems whilst downloading a boot loader from the Arch wiki, I looked up if there was a way to get the same results without downloading anything and potentially running into the same issue. 
1. Install GRUB package: pacman -S grub
2. Install grub onto the disk: grub-intsall  /dev/sda
3. Generate config: grub-mkconfig -o /boot/grub/grub.cfg

Follow the same exit and rebooting instructions.

I am having issues with installing packages within Arch, i.e. my preferred DE, so I am going to try to redo the  **pacstrap /mnt base linux linux-firmware vim** command. I couldn't figure out how to install packages after the initial set up. I am unable to change sudo permissions and 
