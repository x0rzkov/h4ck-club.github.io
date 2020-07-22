###### quickie
```
ping ostechnix -c 4
fdisk -l
cfdisk
...
mount /dev/sda1 /mnt
mkdir /mnt/home
mount /dev/sda5 /mnt/home
pacstrap /mnt base base-devel
genfstab /mnt >> /mnt/etc/fstab
cat /mnt/etc/fstab
arch-chroot /mnt /bin/bash
vi /etc/locale.gen # vi /etc/locale.gen
locale-gen
vi /etc/locale.conf
LANG=en_US.UTF-8
ls /usr/share/zoneinfo/
ln -s /usr/share/zoneinfo/Asia/Kolkata /etc/localtime
hwclock --systohc --utc
passwd # Set ‘root’ user password with command
vi /etc/hostname
systemctl enable dhcpcd
pacman -S grub os-prober
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
exit
umount /mnt
umount /mnt/home
reboot
```
###### Installing Arch:
```

sudo vim /etc/pacman.conf
Update packages list: sudo pacman -Syy
run sudo pacman -Syu  before installing any software (to update the repositories first)

* Timing issue:
    - Change hardware clock to use UTC time:
        sudo timedatectl set-local-rtc 0
    - Set timezone to Asia/Singapore
        sudo timedatectl set-timezone Asia/Singapore
    - Install Network Time Protocol
        sudo pacman -S ntp
    - Synchornize the system clock:
        sudo ntpd -qg
    - After updating the system clock, store the time to the hardware clock so that it is preserved when rebooting
        sudo hwclock -w


* Pacman log file:
    /var/log/pacman.log

* Downgrading package:
    cd /var/cache/pacman/pkg
    1) sudo pacman -Ud nvidia-utils-313.30-2-x86_64.pkg.tar.xz
    2) sudo pacman -Ud nvidia-313.30-5-x86_64.pkg.tar.xz
    3) sudo pacman -Ud virtualbox-host-modules-4.2.12-3-x86_64.pkg.tar.xz
    4) sudo pacman -U linux-3.8.11-1-x86_64.pkg.tar.xz
    5) sudo pacman -U virtualbox-4.2.12-3-x86_64.pkg.tar.xz

* Installing X
    - Choose fastest mirror in /etc/pacman.d/mirrorlist
        + vim /etc/pacman.d/mirrorlist
        + Put the below line at the top:
            Server = http://mirror.nus.edu.sg/archlinux/$repo/os/$arch
    sudo pacman -S xorg
    sudo pacman -S xorg-twm xorg-xclock xterm
    startx
    ##### Take note that: never try to create /etc/xorg.conf file!!! Try to create
          this file will make X not able to start!!!

* Sound:
    Sound is muted by default, so need to unmuted it:
    https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Unmuting_the_channels
    sudo pacman -S alsa-utils

* Set locale:
    sudo vim /etc/local.gen
    sudo locale-gen

* Fixed truecrypt failed to set up a loop device
    https://wiki.archlinux.org/index.php/TrueCrypt
    lsmod | grep loop
    sudo modprobe loop
    sudo tee /etc/modules-load.d/truecrypt.conf <<< "loop"

* WIFI:
    - The wireless here is "wlo1"
        sudo ip link set wlo1 up
        sudo wpa_supplicant -i wlo1 -c /etc/wpa_supplicant.conf &
        sudo dhcpcd wlo1
    - GUI config tool (optinal): sudo pacman -S wpa_supplicant_gui
    - network={
        ssid="Nha06-16-30 co j nhieu I"
        #psk="gaidepnhieuI"
        psk=35a7546f8885820d05a6fdbfa2e388191b977be3ba9d514b46da38623a7e0333
      }
      ap_scan=1
    - Fix issue can't start wpa_supplicant:
        + add no password require for user squallltt when he runs wpa_supplicant
          to /etc/sudoers
    - Connect WEP:
        sudo iwconfig wlo1 essid "NAAEC" key 0050263557
        (if using ASCII key: sudo iwconfig wlo1 essid "MyWiFiID" key s:asciikey)
        sudo dhcpcd wlo1
    - Connect WIFI - to Jurong East house:



* Mount NTFS volume:
    - Install ntfs-3g: sudo pacman -S ntfs-3g
    mount -t ntfs-3g /dev/<device> /mnt/<folder>

* Cannot find the fakeroot binary required for building as non-root user
    https://wiki.archlinux.org/index.php/Arch_User_Repository#Getting_started
    sudo pacman -S base-devel
    - Then can make package for Dropbox like so:
        makepkg -s

* Fine tuning font:
    - sudo pacman -S ttf-dejavu
    - https://wiki.archlinux.org/index.php/Font_Configuration#Patched_packages
    - Download AUR: https://aur.archlinux.org/packages/freetype2-infinality/
    - Download https://aur.archlinux.org/packages/fontconfig-infinality/
    /usr/share/doc/fontconfig/infinality-ultimate/fontconfig
    - Manually install TTF fonts:
        + Copy fonts (Consolas font) to ~/.fonts
        + run command: fc-cache -fv

* Enable thumbnail view in thunar file manager:
    sudo pacman -S tumbler


* Installing Dropbox:
    - http://thinkingeek.com/2011/02/18/installing-dropbox-and-dropbox-nautilus-in-archlinux/
    - Download dropbox: http://aur.archlinux.org/packages.php?ID=23363
    - Download nautilus-dropbox: http://aur.archlinux.org/packages.php?ID=19615
    - Uncompress them using: tar xvfz <filename.tar.gz>
    - Go to dropbox folder and run: makepkg -s
    - Then install the built package: sudo pacman -U <filename.xz>
    - ##### IMPORTANT ##### :
        + never never edit any file in the Dropbox folder before the newly
          installed Dropbox has finished indexing the files; or else it will
          create file conflict!!!!

* Disable beep sound:
    - sudo rmmod pcspkr
    - black list to prevent loading at boot:
        sudo echo "blacklist pcspkr" > /etc/modprobe.d/nobeep.conf


* Check error X:
    https://bbs.archlinux.org/viewtopic.php?id=102401
    cat /var/log/Xorg.0.log | grep EE
    /etc/X11/xorg.conf   : if cannot start X, delete this file! - this evil file


* Fix VLC no start:
    https://bbs.archlinux.org/viewtopic.php?pid=1211362
    pacman -S vlc
    /usr/lib/vlc/vlc-cache-gen -f usr/lib/vlc/plugins
    pacman -S vlc # just to be sure ;)

* Terminal hack (display beautiful Arch Linux logo on terminal):
    https://aur.archlinux.org/packages/alsi/
    - Download the package
    - makepkg
    - Install alsi
    - In terminal, run: alsi
    - config files are in: ~/.config/alsi/

* fix truecrypt Dropbox volume mount as read only
    - See log file: jounrnalctl -xn
    - The error is:
      Unable to monitor entire Dropbox folder hierarchy. Please run "echo 100000 | sudo tee /proc/sys/fs/inotify/max_user_watches" and restart Dropbox to correct the problem.
    - Fix:
      + src: http://paulphilippov.blogspot.sg/2011/02/how-to-solve-dropbox-filesystem.html
      + sudo vi /etc/sysctl.conf
      + add this line at the end:
        fs.inotify.max_user_watches = 100000
      + save the file and reboot. That's it.

* fix XFCE unable to start properly:
    - https://bbs.archlinux.org/viewtopic.php?id=129274
    - rm -R .gconf .gnome2 .config/xfce4 .config/xfce4-session .cache
    - I did pacman -Syu before and after the installation of xfce, but my problem was after the installation there was a file at /etc/profile.d/locale.sh that was causing a conflict and not allowing the system to update at all. I never noticed it and when it went back to the cursor so fast I automatically assumed everything was up to date and it had nothing to do. I removed the locale.sh file, ran pacman -Syu, and everything updated as it should and xfce works flawlessly now.
    - https://www.archlinux.org/news/initscripts-update-manual-intervention-required/
    - Summary: Please manually delete /etc/profile.d/locale.sh before updating. If . /etc/rc.conf fails in your login shell, please read the full announcement.

* mount USB flash drive, thumbdrive
    http://mywaytoarch.tumblr.com/post/13111098534/pmount-safe-removal-of-usb-device
    https://aur.archlinux.org/packages.php?ID=54191
    pmount /dev/sdc1

* Installing teamviewer:
    - Enable multilib: edit file /etc/pacman.conf
        #[multilib]
        Include = /etc/pacman.d/mirrorlist
    - The Teamviewer daemon must be running for Teamviewer 8 to work.
        Execute 'sudo systemctl start teamviewerd' in a terminal.


* Openbox:
    - config auto start file: vim .config/openbox/autostart
    - obconf    : theme configuration
    - Menumaker: sudo pacman -S menumaker
        + mmaker -vf OpenBox3 (this will rescan all the installed application
                                and overwrite the existing menu.xml file)
    - tint2     : taskbar
        + https://wiki.archlinux.org/index.php/Tint2
        + tint2conf : GUI configure tint
        + config file: ~/.config/tint2/tint2rc
    - openbox --restart
    - xcompmgr
        + https://wiki.archlinux.org/index.php/Xcompmgr
        + xcompmgr -c &
    - Wallpaper:
        + https://wiki.archlinux.org/index.php/Feh
        + feh --bg-center ~/wallpapers/ArchLinux01.jpg
    - Suspend: pm-suspend
        + Install: sudo pacman -S pm-utils
        + Locking the screen saver on hibernate or suspend
            https://wiki.archlinux.org/index.php/Pm-utils#Locking_the_screen_saver_on_hibernate_or_suspend
            create file: /etc/pm/sleep.d/00screensaver-lock
            #!/bin/sh
            #
            # lock workstation on hibernate or suspend

            username=squallltt # add username here; i.e.: username=foobar
            userhome=/home/$username
            export XAUTHORITY="$userhome/.Xauthority"
            export DISPLAY=":0"

            case "$1" in
              hibernate|suspend)
                   su $username -c "/usr/bin/slock" & # or any other such as /usr/bin/xscreensaver-command -lock
                   ;;
                thaw|resume)
                   ;;
                *) exit $NA
                   ;;
            esac
            chmod to 755, and make sure it owns by root:root
        + Arch IRC members say don't use pm-*crap, use this instead:
            systemctl suspend
            . How to lock screen when suspend using the above command
            . Create file slock.service and put it in /etc/systemd/system/
                [Unit]
                Description=Lock X session using slock - Tung

                [Service]
                User=squallltt
                Environment=DISPLAY=:0
                ExecStart=/usr/bin/slock

                [Install]
                WantedBy=sleep.target
            . Then run: sudo systemctl enable slock.service
            . Then everytime we suspend by using: systemctl suspend, it will lock
              the screen as well
            . List systemctl service: systemctl -t service -a | grep slock


    - Adjust keyboard delay:
        + https://wiki.archlinux.org/index.php/Adjusting_typematic_delay_and_rate
        + Put this to ~/.config/openbox/autostart
            xset r rate 200 30
    - Theme:
        + sudo pacman -S lxappearance  (this allows us to change gtk application theme)
        + For Qt:
            # https://wiki.archlinux.org/index.php/Uniform_Look_for_QT_and_GTK_Applications#GTK-QT-Engine
            # Install https://wiki.archlinux.org/index.php/Qt
            # add: export GTK2_RC_FILES="$HOME/.gtkrc-2.0" to .xinitrc file
              before start openbox
            # choose GTK+ theme for Qt by: /usr/bin/qtconfig-qt4
        + For transparentcy:
            # https://wiki.archlinux.org/index.php/Per_Application_Transparency
            # devilspie syntax documentation: http://www.foosel.org/linux/devilspie
            # install: sudo pacman -S transset-df
            # transset-df <value>   (where value between 0..1)
            # sudo pacman -S devilspie
            # then start: xcompmgr &
            # then start: devilspie -a &
            # configure opacity: vim ~/.devilspie/opacity.ds
    - Control volume from keyboard:
        + https://wiki.archlinux.org/index.php/Openbox#Keyboard_volume_control


* Graphic driver:
    - Install Bumblebee (for HP laptop - HP Pavilion dm3-1123tx)
        + https://wiki.archlinux.org/index.php/Bumblebee#Installing_Bumblebee_with_Intel_.2F_Nvidia
        + sudo pacman -S intel-dri xf86-video-intel bumblebee nvidia
        + add user to bumblebee group: gpasswd -a squallltt bumblebee
        + start bumblebee automatically at startup: systemctl enable bumblebeed
        + reboot!
        + by doing those previous steps, it fix the error:
            . "EnterVT failed for screen 0"
            . that means: every time a computer is suspended or press Ctrl+Alt+F2
              then the X server is terminated and all other applications are killed
        + The url link also provides a troubleshooting:
          Fatal IO error 11 (Resource temporarily unavailable) on X server
          Change KeepUnusedXServer in /etc/bumblebee/bumblebee.conf from false to true
    - For VirtualBox guest running Arch:
        + if the file ~/.xinitrc has:
            sudo VBoxClient-all &
            sudo systemctl start vboxservice.service
            then need to make sure that we don't need sudo password for
            VBoxClient-all and systemctl (or else, we will receive error
            EnterVT failed for screen 0). Solving by doing this:
            . sudo visudo -f /etc/sudoers
            . add:
                ## Allow sudo for user squallltt and let him run VboxClient-all without requiring a password
                squallltt ALL = PASSWD: ALL, NOPASSWD: /usr/bin/VBoxClient-all, /usr/sbin/ip, /usr/sbin/wpa_supplicant, /usr/sbin/dhcpcd, /usr/bin/truecrypt, /usr/bin/systemctl

* Disable menu in Virtualbox:
    - VBoxManage setextradata global GUI/Customizations noMenuBar,noStatusBar



* Vim: write to root permission file in vim
    - add to .vimrc file: cmap w!! w !sudo tee %
    - run: vim /path/to/file as usual
    - then when we want to save, just issue: w!!
    - then press l

* irssi : IRC
    Source: http://blog.dhampir.no/content/irssi-auto-connect-and-auto-identify
    vim ~/.irssi/config
    There are loads of irssi scripts which do this, but the truth is irssi actually supports these things very well out of the box. Here's how.
    Start up irssi, then:
    /connect irc.freenode.net
    /nick MyIRCNick
    /SERVER ADD -auto -network freenode irc.freenode.net 6667 <password>
    (you may have to shutdown and restart irssi at this point for it to recognize the network name "freenode" in the next step)
    /CHANNEL ADD -auto #ubuntu freenode
    Another method of auto-identifying is seen below. The above is generally preferred.
    /NETWORK ADD -autosendcmd "/^msg NickServ IDENTIFY password;wait 2000" freenode
    Ignore join, part, quit message: add the following to config file:
    ignores = (
      {
        level = "JOINS PARTS QUITS";
        channels = ( "#archlinux", "#vim", "#python" );
        network  = "FreeNode";
      },

      {
        level = "MODES";
        channels = ( "&amp;bitlbee" );
        network  = "BitlBee";
      }
    );


* Screen recording:
    gtk-recordmydesktop

* Mount iso file
    fuseiso -p  testimage.iso testimagemountpoint
    to unmount:
    fusermount -u <mountpoint>

* Fix Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine"
    sudo pacman -S gtk-engines
    sudo pacman -S gtk-engine-murrine


* Some useful commands:
    - Change resolution:
        + xrandr (to see what resolution available)
        + xrandr --output VGA1 --mode 1920x1080
    - See error log:
        + journalctl -xn
    - See which driver X org is using:
        lspci -nnk | grep -i vga -A3 | grep 'in use'
    - To remove a package and its dependencies which are not required by any other installed package
        pacman -Rs package_name
        sudo pacman -Rs nautilus  (remove nautilus)
    - update system
        sudo pacman -Syu
    - list all packages no longer required as dependencies
        sudo pacman -Qdt
    - generate a list of installed packages:
        pacman -Q > pacman.txt
        pacman -Qqe > pacman.txt
        pacman -Qi | sed '/^Name/{ s/  *//; s/^.* //; H;N;d}; /^URL/,/^Build Date/d; /^Install Reason/,/^Description/d; /^  */d;x; s/^.*: ... //; s/Jan/01/;  s/Feb/02/;  s/Mar/03/;  s/Apr/04/;  s/May/05/;  s/Jun/06/;  s/Jul/07/;  s/Aug/08/; s/Sep/09/; s/Oct/10/;  s/Nov/11/;  s/Dec/12/; / [1-9]\{1\} /{ s/[[:digit:]]\{1\}/0&/3 }; s/\(^[[:digit:]][[:digit:]]\) \([[:digit:]][[:digit:]]\) \(.*\) \(....\)/\4-\1-\2 \3/' | sed ' /^[[:alnum:]].*$/ N; s/\n/ /; s/\(^[[:graph:]]*\) \(.*$\)/\2 \1/; /^$/d' > pacman.txt
        pacsysclean > pacman.txt  (display installed packages, sorted by size)
        sudo pacman -Qs gnome (search for keyword "gnome" in the installed package)
    - Turn off laptop screen:
        xrandr --output LVDS1 --off
    - Add new user:
        sudo useradd -m -g [initial_group] -G [additional_groups] -s [login_shell] [username]
        example: sudo useradd -m -g users -s /bin/bash newuser
    - Specify user password:
        sudo passwd [username]
    - Add group squallltt:
        sudo groupadd squallltt
    - Add user squallltt to group squallltt
        sudo gpasswd -a squallltt squallltt
    - List file in tar:
        tar -tvf em-4.0.15-lt.tar.gz  | more
    - List file in .rar:
        unrar l file.rar
    - List file in .zip:
        unzip -l file.zip
    - Get IP address: ip addr
    - SSH service:
        + https://wiki.archlinux.org/index.php/Secure_Shell
        + Start manually: sudo systemctl start sshd
        + Auto start at startup: sudo systemctl enable sshd.service
        + Enable SSH Deamon socket so the deamon is started on the first
          incoming connection:
          sudo systemctl enable sshd.socket
    - Copy default config file:
        /etc/skel/
    - Transfer file via SSH:
        scp /path/to/my.file me@serverB:/path/to/destination/my.file
    - Copy all content inside a directory including sub-directories:
        cp -R * destination_path
    - Disable synaptics mouse / touch pad mouse:
        synclient TouchpadOff=1
    - Check laptop battery status:
        + sudo pacman -S acpi
        + check battery state: acpi
        + check temperature: acpi -t
        + check AC power status: acpi -a
        + check alltogether: acpi -V
    - Delete all ".tmp" files in the current directory
        find . -name "*.tmp" -exec rm -rfv {} +
    - Delete all conflicted files in Dropbox:
        find . -name "*conflict*" -exec rm -rfv {} +
    - Add to ignore list in SVN:
        svn propedit svn:ignore .
    - Ignore .git directory in SVN repo:
        svn propset svn:ignore .git .
    - Global ignore SVN:
        Edit file ~/.subversion/config
        global-ignores = *.o *.lo *.la *.al .libs *.so *.so.[0-9]* *.a *.pyc *.pyo * .stripped
    - See log files:
        dmesg
        sudo journalctl -xb
        sudo cat /proc/kmsg
    - See memory:
        free -m


* Change system wide editor to vim:
    - Add this to .bashrc
        # change system-wide editor
        export VISUAL="/usr/bin/vim -p -X"
        export EDITOR=vim


* VNC:
    - https://wiki.archlinux.org/index.php/Vncserver
    - Install tightvnc:
        sudo pacman -S tightvnc
    - First time setup, run:
        vncserver
    - Edit xstartup file (which functions like an .xinitrc file)
        ~/.vnc/xstartup
    - Start a VNC server:
        vncserver -geometry 1440x900 -alwaysshared -dpi 96 :1
    - Shutdown a vncserver:
        vncserver -kill :1
    - Connect to a vnc server:
        vncviewer 192.168.0.150:1



* Could not open a connection to your authentication agent.
    - Install openssh: sudo pacman -S openssh
    - This error happen when issue command: ssh-add
    - To fix this, run: eval `ssh-agent`
    - Then run: ssh-add without problem
    - To make it autostart for OpenBox:
        + https://wiki.archlinux.org/index.php/Openbox#SSH_agent_no_longer_starting
        + Put below code to file: vim ~/.config/openbox/environment
            SSHAGENT="/usr/bin/ssh-agent"
            SSHAGENTARGS="-s"
            if [ -z "$SSH_AUTH_SOCK" -a -x "$SSHAGENT" ]; then
                    eval `$SSHAGENT $SSHAGENTARGS`
                    trap "kill $SSH_AGENT_PID" 0
            fi


* Show/hide menu in Thunar:
    Ctrl + M

* tool to format USB flash:
    + sudo pacman -S dosfstools

* Kernel driver not installed (rc=-1908) - VirtualBox Error
    sudo modprobe vboxdrv

* Enable shared folder in VirtualBox:
    - Run this command in the guest: sudo mount -t vboxsf
    - Don't copy file with this attribute:
        prw-r--r--  1 squallltt users    0 May  5 12:30 nicklistfifo
        it will hang!
    - (mount -t vboxsf [-o OPTIONS] sharename mountpoint
        (Notes: sharename is optional or same as selected in the VirtualBox-Dialog , mountpoint of the shared directory in the hosts filesystem))

* Installing yaourt:
    - https://wiki.archlinux.org/index.php/Yaourt
    - Download, makepkg and install package-query
        https://aur.archlinux.org/packages/package-query/
    - Download and install yaourt
        https://aur.archlinux.org/packages/yaourt/
    - Update system including AUR packages:
        yaourt -Syua

* Tool to check ethernet (LAN cable)
    sudo pacman -S ethtool
    sudo ethtool enp3s0 | grep MDI-X
    sudo ethtool enp3s0

* Ranger
    Copy default config files when first install
        ranger --copy-config=all

* Map delete key to delete files to trash, enable delete file from CLI to trash
    - yaourt trash-cli
    - edit file: ~/.config/ranger/rc.conf
        map <DELETE>   shell trash-put  %s

* RaspberryPi
    - pacman -S ttf-dejavu
    - resize root partition:
        http://raspberrypi.stackexchange.com/questions/499/how-can-i-resize-my-root-partition
    - WIFI issue:
        + https://github.com/xbianonpi/xbian/issues/217
        + http://raspberrypi.stackexchange.com/questions/1384/how-do-i-disable-suspend-mode/4518#4518
        + while true ; do ./wireless-cron-job.sh ; sleep 15; done
    - Backup:
        sudo dd if=/dev/sdc  of=~/raspberrypi_backup_20130514.img
    - Set IP address:
        sudo ifconfig eth0 192.168.0.137
    - Connect Android to Raspberry Pi
        + http://www.raspberrypi.org/phpBB3/viewtopic.php?t=18916&p=331361
        + Create a file usb0 in /etc/network.d/
            CONNECTION="ethernet"
            DESCRIPTION="IP over USB"

            INTERFACE="usb0"

            IP="static"
            IFOPTS="192.168.42.42 netmask 255.255.255.0 network 192.168.42.0 broadcast 192.168.42.255"

            TIMEOUT=10

            #PRE_UP=
            #POST_UP="iptables -t nat -A POSTROUTING -o eth0 -s 192.168.
        + sudo systemctl enable dhcpcd@usb0
        + sudo systemctl enable netcfg@usb0
        + Then when the Pi is just turn on and booting, quickly enable USB tethering on the android, done!
        + Android IP: 192.168.42.129
        + Raspberry IP: 192.168.42.30
        + Enable access internet to the Pi:
            route add default gw 192.168.42.129 usb0
    - Fix /lib/i386-linux-gnu/libpthread.so.0: could not read symbols: Invalid operation when compiling raspi camera:
        + Add -lX11 -lpthread to the linker script



***** Testing
    https://aur.archlinux.org/packages/nvidia-173xx-utils/
    https://aur.archlinux.org/packages/nvidia-173xx/
    pacman -S intel-dri xf86-video-intel bumblebee nvidia
    https://wiki.archlinux.org/index.php/Bumblebee#Installing_Bumblebee_with_Intel_.2F_Nvidia
    gpasswd -a $USER bumblebee
    systemctl enable bumblebeed

Softwares need to install:
    - sudo pacman -S vlc
    - sudo pacman -S truecrypt
    - sudo pacman -S firefox
    - PDF viewer:
        + sudo pacman -S zathura
        + sudo pacman -S zathura-pdf-poppler
        + sudo pacman -S zathura-djvu
    - Dropbox
    - sudo pacman -S chromium
    - Flash plugin for browser:
        + GNU flash: sudo pacman -S gnash-gtk
        + or Adobe Flash: sudo pacman -S flashplugin
        + sudo pacman -S gstreamer0.10-plugins  (required for GNU flash to play video)
    - Git: sudo pacman -S git
    - image viewer: sudo pacman -S gpicview
    - awesome image viewer: sudo pacman -S sxiv
    - Screenshooter for xfce4: sudo pacman -S xfce4-screenshooter
        + Settings > Keyboard > Application Shortcuts > Add
        + xfce4-screenshooter   assign to PrintScreen key
    - Music player: sudo pacman -S banshee
    - Java Development Kit
        + sudo pacman -S jdk7-openjdk
    - Simple lock screen: sudo pacman -S slock
        + To enable lock screen in XFCE:
            = XFCE Power Manager > Extended > Lock screen when going for suspend/hibernate
            = Session and Startup > Advanced > Lock screen before sleep
    - LaTex:
        sudo pacman -S texlive-most


pacman -Sy       # synchronize repository databases if neccessary
pacman -Syy      # force synchronization of repository databases

pacman -Ss xyz   # search repository database for packages for xyz

pacman -S xyz    # install package xyz
pacman -Sy xyz   # synchronize repo and install xyz
pacman -Syy xyz  # really synchronize repo and install xyz

pacman -R xyz    # remove package xyz but keep its dependencies installed
pacman -Rs xyz   # remove package xyz and all its dependencies (if they are not required by any other package)
pacman -Rsc xyz  # remove package xyz, all its dependencies and packages that depend on the target package

pacman -Ql xyz   # show all files installed by the package xyz
pacman -Qo /path # find the package which installed the file at /pat
```
