###### system maintenance
```
journalctl --vacuum-size=500M
paccache -rvk 1
```
###### system management

```bash
inxi -Fxz
ps aux, ps axjf, ps -au phonexicum, ps aux --sort pmem
df -hT, du -hd 1, fdisk -l, free -h
ulimit - get and set user limits in linux
netstat, htop, top, dstat, free, vmstat, ncdu, iftop, hethogs
lsblk, lscpu, lshw, lsus, lspci, lsusb
lsof -nPi - list opened files - very flexible utility, can be used for network analylsis
# SEToolkit (v3.5.1 - 2013) - a collection of scripts for performance analysis and gives advice on performance improvement (it has been a standard in system performance monitoring for the Solaris platform over the last 10 years)
# inotify or man fanotify (can block actions) - Linux kernel subsystem that acts to extend filesystems to notice changes to the filesystem, and report those changes to applications.


# To get a list of last installed packages, you can run:
grep -i installed /var/log/pacman.log
# To get a list of last upgraded packages, you can run:
grep -i upgraded /var/log/pacman.log
# To get a list of last installed or upgraded packages, you can run:
grep -iE 'installed|upgraded' /var/log/pacman.log
#ist of top processes ordered by RAM and CPU
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head
# disk usage
du -h --max-depth=1 | sort -hr | head -n 15 2>&1 < /dev/null
du -hs * | sort -rh | head -5
find -type f -exec du -Sh {} + | sort -rh | head -n 5
```
