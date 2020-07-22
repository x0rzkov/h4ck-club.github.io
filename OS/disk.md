# Disk Management
```bash
# Device details
# get device info as normal user
lsblk -o NAME,MOUNTPOINT,SIZE,MODEL
udisksctl dump
udisksctl info -b [device]
udisks --dump | less
# list drives and partitions for block devices (hard disks, USB sticks)
sudo lsblk
# list all partitions: UUID, Label and filesystem
sudo blkid
# list drives, partition table type and partitions with filesystem plus sector size
sudo parted -l
# list drives, partition table type and partitions with filesystem (plus sectors and block sizes)
sudo fdisk -l
# show currently mounted drives
sudo cat /proc/mounts | sed "/^\/dev/!d;s: .*::" | sort -u
# show drives mounted on startup
sudo cat /etc/fstab
# show useful symbolic links to devices
sudo tree /dev/disk
# Mounting / unmounting
# Regular user
# mounting a device as normal user (on desktop)
udisksctl mount -b [device]
udisks --mount [device]
# unmounting a device as normal user (on desktop)
udisksctl unmount -b [device]
# eject drive
udisksctl power-off -b [device]
# Root
# create mount point
sudo mkdir -p [path to mount]
# mounting a device as root
sudo mount [device] [path to mount]
# mounting a device as root using the UUID
sudo mount /dev/disk/by-uuid/[UUID] [path to mount]
unmount a device as root
sudo umount -v [device or mount path]
spin down drive
sudo hdparm -y [device]
# Partition Labels
# FAT32
# change label of FAT32 drive without format
# sudo dosfslabel /dev/sdc1 USB64
# NTFS
# fix problems with NTFS partition
sudo ntfsfix [partition]
# change the label of an NTFS drive without format
sudo ntfslabel /dev/sdb1 E6000
# change the label of an NTFS drive without format (force)
sudo ntfslabel -f /dev/sdb1 E6000
# Disk Usage
# show child directory sizes of in current directory in bytes
du
# show human readable directory sizes
du -h
# show child directory sizes of in current directory in MB
du -BM
# show child directory sizes of the specified directory in bytes
du /path/to/directory
# show sizes of direct child directories only
du -d 1 .
sort directories by size
du -BM -d 1 . | sort -n
du / | sort -nr | less
# Monitoring
log io at regular intervals
sar -b 1 > io.log
# fixing bad blocks
# fix bad blocks on ext2/ext3/ext4 partition
sudo e2fsck -cfpv /dev/[device]
# fix common NTFS partition problems
ntfsfix /dev/[device]
# required dependency
sudo apt-get install ntfs-3g
disk rescue
# cloning a partition / drive
ddrescue -f -n /dev/[from] /dev/[to] rescue.log
# check filesystem for corruption
fsck -f /dev/[device]
# fix partition table
testdisk
# disk recue manual
# https://wiki.archlinux.org/index.php/Disk_cloning
# disk erasure
# completely erase data on drive
sudo dd if=/dev/zero of=/dev/[sd?]
```
