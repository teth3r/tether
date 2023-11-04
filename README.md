# tether

(This documentation is currently a work in progress)

<p>tether is a multi-call shell script that combines many applets/functions into a single executable.</p>

<p>Think busybox or toybox, except as a shell script, you can create symbolic links to tether for each defined function and it will behave/act like whatever it was invoked as.<p>

# Currently defined functions

. [benchmark](#benchmark)
. [chroot-backup](#chroot-backup)
. [dotfiles](#dotfiles)
. [extract](#extract)
. [install-module](#install-module)
. [ll](#ll)
. [misc](#misc)
. [mkcp](#mkcp)
. [mkmv](mkmv)
. [mktouch](#mktouch)
. [omaps-backup](omaps-backup)
. [opencamera-backup](opencamera-backup)
. [parity](parity)
. [replace-su](replace-su)
. [setup](#setup)
. [tfetch](#tfetch)
. [tether](#tether)
. [touchzip](#touchzip)
. [viw](#touchzip)
. [void-backup](#void-backup)
. [void-deploy](#void-deploy)
. [void-install](void-install)
. [void-mount](void-mount)
. [void-umount](void-umount)
. [whatsapp-backup](whatsapp-backup)
. [zip-module](zip-module)

## benchmark
This is a simple single core performance benchmark tool, that uses the Mersenne primality test.

Usage: benchmark \[OPTION] \[NUMBER]
```
$ benchmark --help

benchmark (C) 2023, Kolade Ayomide Olanrewaju (tether)
benchmark is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    benchmark [OPTION]
          benchmark [OPTION] [NUMBER]

Examples: benchmark --help
          benchmark --iteration 20

Options: -h,  --help       Print out this message
         -it, --iteration  Number of iterations to perform
         -V,  --version    Show version information

Single core performance benchmark using Mersenne primality test
```

Example:
```
$ benchmark --iteration 30

M(2) = 3
M(3) = 7
M(5) = 31
M(7) = 127
M(13) = 8191
M(17) = 131071
M(19) = 524287
[+] Total Mersenne primes found = 7
 
[+] Largest Mersenne prime found M(19) = 524287
 
[+] Total time taken = 7 seconds
```

## chroot-backup
Creates an encrpyted/unencrypted backup of chroot container image (created with void-install) in user specified folder.

Usage: chroot-backup \[OPTION] \[FOLDER]
```
$ chroot-backup --help

chroot-backup (C) 2023, Kolade Ayomide Olanrewaju (tether)
chroot-backup is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    chroot-backup [OPTION]
          chroot-backup [OPTION] [FOLDER]

Examples: chroot-backup --help
          chroot-backup --encrypt /sdcard/newfolder

Options: -en, --encrypt    Create an encrypted backup
         -h,  --help       Print out this message
         -un, --unencrypt  Create an unencrypted backup
         -V,  --version    Show version information

Create chroot image backup in specifed folder
```

Example:
```
$ chroot-backup --unencrypt /mnt/sdcard/newfolder

[-] Chroot image is currently mounted
    Run 'void-umount' before proceeding

$ void-umount

[+] Unmounted chroot

$ chroot-backup --unencrypt /mnt/sdcard/newfolder

[*] Creating chroot image backup

[*] This may take a while

[+] Created 'void.img' backup in '/mnt/sdcard/newfolder'
```

## dotfiles
Installs custom dotfiles for the specified program.

Usage: dotfiles \[OPTION]
```
$ dotfiles --help

dotfiles (C) 2023, Kolade Ayomide Olanrewaju (tether)
dotfiles is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    dotfiles [OPTION]

Examples: dotfiles --vim
          dotfiles --bash-desktop

Options: -ba, --bash-android  Update .bashrc for android
         -bc, --bash-chroot   Update .bashrc for android chroot
         -bd, --bash-desktop  Update .bashrc for linux
         -h,  --help          Print out this message
         -ma, --mksh-android  Update mkshrc for android
         -te, --termux        Update *.properties and profile
         -tm, --tmux          Update .tmux.conf
         -u,  --urxvt         Update .Xresources
         -v,  --vim           Update .vimrc and tether.vim
         -V,  --version       Show version information

Install/Update dotfiles
```

Example:
```
$ dotfiles --vim

[+] Finished updating '~/.vimrc'
[+] Finished updating '/usr/share/vim/vim90/colors/tether.vim'
```

## extract

This is a wrapper for 7z and bsdtar for extracting archive files.

Usage:
```
$ extract --help

extract (C) 2023, Kolade Ayomide Olanrewaju (tether)
extract is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    extract [OPTION]
          extract [FILE...]

Examples: extract --help
          extract /sdcard/*
          extract file1.zip file2.zip

Options: -h, --help     Print out this message
         -V, --version  Show version information

Extract archive into archive-name folder
```

Example:
```
$ extract android-14-system-td-arm64-ab-vndklite-vanilla.img.xz

7-Zip (z) 23.01 (x64) : Copyright (c) 1999-2023 Igor Pavlov : 2023-06-20
 64-bit locale=en_US.UTF-8 Threads:16 OPEN_MAX:1024

Scanning the drive for archives:
1 file, 735459536 bytes (702 MiB)

Extracting archive: android-14-system-td-arm64-ab-vndklite-vanilla.img.xz
--
Path = android-14-system-td-arm64-ab-vndklite-vanilla.img.xz
Type = xz
Physical Size = 735459536
Method = LZMA2:23 CRC64
Streams = 1
Blocks = 88
Cluster Size = 25165824
Characteristics = BlockPackSize BlockUnpackSize

Everything is Ok

Size:       2211467264
Compressed: 735459536
[+] Extracted 'android-14-system-td-arm64-ab-vndklite-vanilla.img.xz' to 'android-14-system-td-arm64-ab-vndklite-vanilla'
```

## tether

This is the main script.

Usage: tether \[FUNCTION] \[ARGUMENTS...]

```
$ tether --help

tether 23.11.03.1833-x86_64 (C) 2023, Kolade Ayomide Olanrewaju (tether)
tether is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    tether [FUNCTION] [ARGUMENTS...]
          tether [OPTION] [FOLDER]

Examples: tether --install /usr/bin
          tether touchzip --encrypt dotfiles.7z .bashrc
          tether extract dotfiles.7z

Options: -h, --help     Print out this message
         -i, --install  Create symbolic links in the specified folder
         -l, --list     List all available functions
         -s, --silent   '-i/--install' with hidden output
         -V, --version  Show version information

tether is a multi-call shell script that combines many applets into a single executable.
Create symbolic links to tether for each function and tether will act like whatever it was invoked as

Currently defined functions (25)
benchmark, chroot-backup, dotfiles, extract, install-module, ll, misc, mkcp, mkmv, mktouch, omaps-backup, opencamera-backup, parity, replace-su, setup, tfetch, touchzip, viw, void-backup, void-deploy, void-install, void-mount, void-umount, whatsapp-backup, zip-module
```
