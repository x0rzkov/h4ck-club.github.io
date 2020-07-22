###### reset pwd
*Reset Lost Root Password from the Grub Menu*
```
1. Restart the Linux host
2. Once the GRUB page appears, quickly select the “*Advanced options for GNU/Linux” option by pressing the down arrow key and Enter button.
3. Now press e to edit the commands.
   modify it or change it from "read-only" mode to "read-write" mode. 
   Find the line beginning with “Linux.” After, look for “ro,” and change it “rw.” 
   Add init=/bin/bash at the end of the line.
4. Press F10. This will display a screen with a prompt.
5. Mount your root filesystem in read-write mode:
   mount -n -o remount,rw /
6. You can now reset your lost root password by using the following command:
   passwd root
   Alternatively, you can change the password of the super user with the command:
   passwd username
   Once you are done, type:
   exec /sbin/init
   to exit the prompt and reboot the computer.
```
*Reset Lost Root Password Using Live CD*
```
1. Download the latest version of Ubuntu, and create a bootable Live CD/USB from it. Boot your system from it.
2. On the display screen select “Try Ubuntu.” This will bring you to the Live CD desktop.
   ubuntu-live-cd-try-ubuntu
3. Open the terminal, and type the following command to become root:
   sudo su
4. Next, we need to find out the location of the hard disk partition. Use the following command:
   fdisk -l
   In most cases it will be “/dev/sda1,” though it can differ depending on how your hard disk is partitioned.
5. Mount the hard disk partition of the system to be recovered using the following command:
   mkdir  /mnt/recover
   mount  /dev/sda1  /mnt/recover
   ubuntu-livecd-mount-partition
6. At this point we need to jail ourselves in the “mnt/recovery” directory. 
   What this means is that we are pretending to be on the regular Linux filesystem. This is simply known as chrooting.
   chroot  /mnt/recover
7. Use the following command to reset your root password:
   passwd root
   or us:
   passwd username
   to reset the password of a superuser.
8. Once completed, exit from the chroot shell:
   exit
9. Unmount the root partition:
   umount /mnt/recover
   and exit your root:
   exit
```
