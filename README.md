# tether

tether is a multi-call shell script that combines many applets/functions into a single executable.

Think busybox or toybox, except as a shell script, you can create symbolic links to tether for each defined function and it will behave/act like whatever it was invoked as.

## Currently defined functions

. benchmark
. dotfiles
. extract
. lyrics
. mkcp
. mkmv
. mktouch
. package
. replace-su
. setup
. swapfile
. terp-deploy
. terp-install
. terp-mount
. terp-umount
. tfetch
. tether
. touchzip
. whatsapp-backup

<br>

| Function | Dependencies | Platform | Details |
| --- | --- | --- | --- |
**benchmark** | bc | Device Agnostic | Usage: ` benchmark [OPTION] [NUMBER] ` <p> This is a simple single core performance benchmark tool. It can be used to quickly compare system performance since it has no external dependencies for `--iterations` <= 62. Run `benchmark --help` for more details. |
**dotfiles** | vim, tmux, urxvt, termux | Device Agnostic (depending on the option flag) | Usage: ` dotfiles [OPTION] ` <p> Installs custom dotfiles for the specified program. It overwrites existing dotfiles and as such it is recommended to backup existing dotfiles beforehand. Run `dotfiles --help` for more details. |
**extract** | 7z, bsdtar | Device Agnostic (requires root on Android) | Usage: ` extract [FILE...] ` <p> This is a wrapper for `7z` and `bsdtar` for extracting archive files. It extracts the archive file into a folder using the archive name. Run `extract --help` for more details. |
**lyrics** | curl, find, iconv, lltag, ping | Device Agnostic | Usage: ` lyrics [FILENAME] ` <p> Lyrics file `.lrc` downloader. Run `lyrics --help` for more details. |
**mkcp** | cp, find, mkdir | Device Agnostic | Usage: ` mkcp [FOLDER] [FILE...] ` <p> This tool copies files/folders to the specified folder. It will create the folder if it doesn't already exist. Run `mkcp --help` for more details. |
**mkmv** | cp, find, mkdir, rm | Device Agnostic | Usage: ` mkmv [FOLDER] [FILE...] ` <p> This tool moves files/folders to the specified folder. It will create the folder if it doesn't already exist. Run `mkmv --help` for more details. |
**mktouch** | mkdir, touch | Device Agnostic | Usage: ` mktouch [FOLDER] [FILE...] ` <p> This tool creates specified empty file(s) in the specified folder. It will create the folder if it doesn't already exist. Run `mktouch --help` for more details. |
**package** | ping, magisk, sed | Android (root) | Usage: ` package [OPTION] ` <p> Magisk module packaging tool. Run `package --help` for more details. |
**replace-su** | mount, unmount | Android (root) | Usage: ` replace-su [OPTION] ` <p> Removes phh-su from AOSP GSI releases >= 12, allowing the use of custom root solutions like `magisk`. Run `replace-su --help` for more details. |
**setup** | ping, xbps-install | Voidlinux | Usage: ` setup [OPTION] ` <p> Post-installation setup tool for Voidlinux. Run `setup --help` for more details. |
**swapfile** | awk, dd, df, mkswap, pgrep, swapoff, swapon | Device Agnostic | Usage: ` swapfile [OPTION] [FILSIZE] [FILENAME] ` <p> Swapfile management tool, create and disable swapfiles on the go. Run `swapfile --help` for more details. |
**terp-deploy** | cp, mkdir | Android (voidlinux chroot) | Usage: ` terp-deploy [OPTION] ` <p> Post-install and post-mount setup tool for chroot running on Android. It was created for, and will only work for chroot images created using `terp-install`. Run `terp-deploy --help` for more details. |
**terp-install** | busybox, fallocate, losetup, lsof, mke2fs, mount | Android (root) | Usage: ` terp-install [OPTION] ` <p> Installation tool for chroot on Android. Run `terp-install --help` for more details. |
**terp-mount** | losetup, mkdir, mount | Android (root) | Usage: ` terp-mount [OPTION] ` <p> Mount tool for chroot on Android. It was created for, and will only work for chroot images created using `terp-install`. Run `terp-mount --help` for more details. |
**terp-umount** | losetup, lsof, mkdir, rm, umount, wc | Android (root) | Usage: ` terp-umount [OPTION] ` <p> Unmount tool for chroot on Android. It was created for, and will only work for chroot images created using `terp-install`. Run `terp-umount --help` for more details. |
**tfetch** |  | Device Agnostic | Usage: ` tfetch [OPTION] ` <p> System resource information tool, has no external dependencies. Run `tfetch --help` for more details. |
**touchzip** | 7z, rm, touch | Device Agnostic (requires root on Android) | Usage: ` touchzip [OPTION] [FILENAME] [FILE...] ` <p> This tool creates an encrypted/unencrypted 7z archive of the specified files. Run `touchzip --help` for more details. |
**whatsapp-backup** | 7z, mkdir, pm | Android (root) | Usage: ` whatsapp-backup [OPTION] ` <p> This tool creates and restores encrypted/unencrypted backups of `Whatsapp` (media, chats, etc) in external storage (SD card, USB OTG, etc), It will fallback to using internal storage if no external storage device is available. Run `whatsapp-backup --help` for more details. |

## Installation

```
$ wget https://raw.githubusercontent.com/teth3r/tether/master/tether
$ chmod +x tether
$ ./tether --install <desired-folder>
```
Ensure that `<desired-folder>` is included in PATH

## LICENSE

Copyrights (c) 2023, Kolade Ayomide Olanrewaju <<koladeolanrewaju@tutanota.com>>

Distributed under [GPL-3.0-or-later](../master/LICENSE).
