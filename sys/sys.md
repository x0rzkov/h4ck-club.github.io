#### Operating Systems
* [nix](nix.md)
* [win](win.md)
* [droid](droid.md)
* [iOS](ios.md)

#### rsp4
```bash
sudo fdisk /dev/mmcblk0
# At the fdisk prompt, delete old partitions and create a new one
o # This will clear out any partitions on the drive.
p # list partitions. There should be no partitions left.
n # new partition
p # for primary,
1 # for the first partition on the drive, press ENTER to accept the default first sector, then type 
+100M # for the last sector.
t # 
c # to set the first partition to type W95 FAT32 (LBA).
n # new partition 
p # primary
2 # for the second partition on the drive, and then press ENTER 
+80G
w # Write the partition table and exit by typing w.

cd /mnt 
sudo mkdir /mnt/boot /mnt/root 
sudo mount /dev/mmcblk0p1 /mnt/boot 
sudo mount /dev/mmcblk0p2 /mnt/root
sudo bsdtar -xpf ArchLinuxARM-rpi-4-latest.tar.gz -C /mnt/root 
sudo mv /mnt/root/boot/* /mnt/boot/ 
sync
sudo umount /mnt/boot /mnt/root
reboot with sd card
pacman-key --init
pacman-key --populate archlinuxarm
useradd -m -g users -G wheel,storage,power -s /bin/bash edge
pacman -S sudo
visudo
# uncomment -->  %wheel ALL=(ALL) ALL
reboot
```

#### protocols
* [tcp_ip](ip.md)
* [http](http.md)

#### dns
* [dns](dns.md)
