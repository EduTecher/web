```
$FDISK $MKFS $MOUNT
#mount overlay work -t overlay -o lowerdir=sfs,upperdir=space,workdir=work
timedatectl set-time "yyyy-MM-dd hh:mm:ss"
wpa_supplicant -B -i wlan0 -c <(wpa_passphrase SSID PASSWORD)
dhcpcd

/etc/pacman.d/gnupg/gpg.conf
/etc/pacman.d/mirrorlist
pacman -Sy archlinux-keyring
pacman-key --init
pacman-key --refresh-keys
pacman-key --populate
pacstrap /mnt PACKAGE

genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt
EDITOR=nano
/etc/locale.gen
/etc/locale.conf
/etc/vconsole.conf
/etc/hostname
/etc/hosts
visudo
useradd -m -G wheel USER
passwd
passwd USER

grub-install --target=x86_64-efi --efi-directory=/boot/ --bootloader-id=GRUB
/etc/default/grub
grub-mkconfig -o /boot/grub/grub.cfg
```

|                                                       |                                                           |                                                              |                                 |                                    |
| ----------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------- | ---------------------------------- |
| base{,-devel}                                         | linux-zen                                                 | grub                                                         | efibootmgr                      |                                    |
| xorg{,-xinit}                                         | noto-fonts{,-cjk,-emoji,-extra}                           | firefox                                                      | code                            |                                    |
| libxss                                                |                                                           |                                                              |                                 |                                    |
| electron                                              | ffmpeg                                                    |                                                              |                                 |                                    |
| [python](#python)                                     | [git](#git)                                               | [nano](#nano)                                                |                                 |                                    |
| [dhcpcd](#dhcpcd)                                     | [wpa_supplicant](#wpa_supplicant)                         | [blfs-systemd-units](#blfs-systemd-units)                    | openssh                         |                                    |
| [linux-firmware](#linux-firmware)                     |                                                           |                                                              |                                 |                                    |
| [dwm](git://git.suckless.org/dwm)                     | [dmenu](git://git.suckless.org/dmenu)                     | [slock](git://git.suckless.org/slock)                        |                                 |                                    |
| [alacritty](git://github.com/alacritty/alacritty.git) | [st](git://git.suckless.org/st)                           |                                                              |                                 |                                    |
| [fcitx](https://download.fcitx-im.org/fcitx/)         | [typora](https://typora.io/linux/Typora-linux-x64.tar.gz) | [zoom](https://cdn.zoom.us/prod/5.6.20278.0524/zoom_x86_64.tar.xz) |                                 |                                    |
|                                                       |                                                           |                                                              | git://github.com/tuxera/ntfs-3g | git://github.com/neovim/neovim.git |
|                                                       |                                                           |                                                              |                                 |                                    |
| ranger-fm                                             | virtualenv                                                | cmake ninja                                                  |                                 |                                    |
| pylint                                                | requests                                                  | torch                                                        |                                 |                                    |



# [python](https://www.python.org/ftp/python/3.8.10/Python-3.8.10.tar.xz)

```sh
./configure --prefix=/usr/local/ --enable-optimizations --enable-shared --with-system-expat --with-system-ffi --with-ensurepip=yes
```

# [git](https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.30.1.tar.xz)

```sh
./configure --prefix=/usr/local/ --with-gitconfig=/etc/gitconfig --with-python=python3
make perllibdir=/usr/lib/perl5/5.32/site_perl install
```

# [nano](https://www.nano-editor.org/dist/v5/nano-5.6.tar.xz)

```sh
./configure --prefix=/usr/local/ --sysconfdir=/etc --enable-utf8
```

# [dhcpcd](https://roy.marples.name/downloads/dhcpcd/dhcpcd-9.4.0.tar.xz)

```sh
install -v -m700 -d /var/lib/dhcpcd
groupadd -g 52 dhcpcd
useradd -c 'dhcpcd PrivSep' -d /var/lib/dhcpcd/ -g dhcpcd -s /bin/false -u 52 dhcpcd
chown -v dhcpcd:dhcpcd /var/lib/dhcpcd
./configure --libexecdir=/lib/dhcpcd --dbdir=/var/lib/dhcpcd --privsepuser=dhcpcd
make install-dhcpcd
```

# [wpa_supplicant](https://w1.fi/releases/wpa_supplicant-2.9.tar.gz)

```sh
cd wpa_supplicant
cp defconfig .config
make BINDIR=/sbin LIBDIR=/lib
install -v -m755 wpa_{cli,passphrase,supplicant} /sbin/
install -v -m644 systemd/*.service /lib/systemd/system/
```

# [blfs-systemd-units](https://www.linuxfromscratch.org/blfs/downloads/10.1-systemd/blfs-systemd-units-20210122.tar.xz)

# [linux-firmware](git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git)

```sh
rm -rf ./.git/ && sudo mv ./ /lib/firmware/
```
