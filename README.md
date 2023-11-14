# tether

tether is a multi-call shell script that combines many applets/functions into a single executable.

Think busybox or toybox, except as a shell script, you can create symbolic links to tether for each defined function and it will behave/act like whatever it was invoked as.

## Currently defined functions

. benchmark
. chroot-backup
. dotfiles
. extract
. ll
. mkcp
. mkmv
. mktouch
. omaps-backup
. opencamera-backup
. setup
. tfetch
. tether
. touchzip
. viw
. void-backup
. void-deploy
. void-install
. void-mount
. void-umount
. whatsapp-backup

<br>

**Function** | **Dependencies** | **Platform** | **Details**
--- | --- | --- | ---
**benchmark** | bc | Device Agnostic | Usage: ` benchmark [OPTION] [NUMBER] ` <p> This is a simple single core performance benchmark tool. It can be used to quickly compare system performance since it has no external dependencies for `--iterations` <= 62. Run `benchmark --help` for more details.
**chroot-backup** | 7z, mkdir, cp, losetup | Android (root) | Usage: ` chroot-backup [OPTION] [FOLDER] ` <p> This tool creates an encrypted/unencrypted backup of chroot container image in the user specified folder. It was created for, and will only work for chroot images created using `void-install`. Run `chroot-backup --help` for more details.
**dotfiles** | vim, tmux, urxvt, termux | Device Agnostic (depending on the option flag) | Usage: ` dotfiles [OPTION] ` <p> Installs custom dotfiles for the specified program. It overwrites existing dotfiles and as such it is recommended to backup existing dotfiles beforehand. Run `dotfiles --help` for more details.
**extract** | 7z, bsdtar | Device Agnostic | Usage: ` extract [FILE...] ` <p> This is a wrapper for `7z` and `bsdtar` for extracting archive files. It extracts the archive file into a folder using the archive name. Run `extract --help` for more details.
**ll** | ls | Device Agnostic | Usage: ` ll [OPTION] [NUMBER] [FOLDER/FILE...] ` <p> This is a wrapper for `ls`, it supports all `ls` arguments and option flags, while simplifying path operations, for example `ls ../..` --> `ll 2`. Run `ll --help` for more details. 
**mkcp** | cp, find, ls, mkdir | Device Agnostic | Usage: ` mkcp [FOLDER] [FILE...] ` <p> This tool copies files/folders to the specified folder. It will create the folder if it doesn't already exist. Run `mkcp --help` for more details.
**mkmv** | cp, find, ls, mkdir, rm | Device Agnostic | Usage: ` mkmv [FOLDER] [FILE...] ` <p> This tool moves files/folders to the specified folder. It will create the folder if it doesn't already exist. Run `mkmv --help` for more details.
**mktouch** | ls, mkdir, touch | Device Agnostic | Usage: ` mktouch [FOLDER] [FILE...] ` <p> This tool creates specified empty file(s) in the specified folder. It will create the folder if it doesn't already exist. Run `mktouch --help` for more details.
**omaps-backup** | 7z, date, ls, mkdir, pm | Android (root) | Usage: ` omaps-backup [OPTION] ` <p> This tool creates and restores encrypted/unencrypted backups of `Organic Maps` downloaded mapfiles in external storage (SD card, USB OTG, etc), It will fallback to using internal storage if no external storage device is available. Run `omaps-backup --help` for more details.
**opencamera-backup** | 7z, date, ls, mkdir, pm | Android (root) | Usage: ` opencamera-backup [OPTION] ` <p> This tool creates and restores encrypted/unencrypted backups of `Open Camera` config files in external storage (SD card, USB OTG, etc), It will fallback to using internal storage if no external storage device is available. Run `opencamera-backup --help` for more details.
**setup** | ping, xbps | Voidlinux | Usage: ` setup [OPTION] ` <p> Post-installation setup tool for Voidlinux. Run `setup --help` for more details.
**tfetch** |  | Device Agnostic | Usage: ` tfetch [OPTION] ` <p> System resource information tool, has no external dependencies. Run `tfetch --help` for more details.
**touchzip** | 7z, rm, touch | Device Agnostic (requires root on Android) | Usage: ` touchzip [OPTION] [FILENAME] [FILE...] ` <p> This tool creates an encrypted/unencrypted 7z archive of the specified files. Run `touchzip --help` for more details.
**viw** | vim | Device Agnostic | Usage: ` viw [FOLDER] ` <p> Terminal filemanager using Vim Netrw. Run `viw --help` for more details.
**void-backup** | cp, ls, mkdir, xbps | Android (voidlinux chroot) | Usage: ` void-backup [OPTION] ` <p> Creates backup of XBPS package cache in external storage. Run `void-backup --help` for more details.
**void-deploy** | cp, ls, mkdir, xbps | Android (voidlinux chroot) | Usage: ` void-deploy [OPTION] ` <p> Post-install and post-mount setup tool for Voidlinux chroot running on Android. It was created for, and will only work for chroot images created using `void-install`. Run `void-deploy --help` for more details.
**void-install** | busybox, fallocate, losetup, lsof, mke2fs, mount | Android (root) | Usage: ` void-install [OPTION] ` <p> Installation tool for Voidlinux chroot on Android. Run `void-install --help` for more details.
**void-mount** | losetup, mkdir, mount | Android (root) | Usage: ` void-mount [OPTION] ` <p> Mount tool for Voidlinux chroot on Android. It was created for, and will only work for chroot images created using `void-install`. Run `void-mount --help` for more details.
**void-umount** | losetup, lsof, mkdir, rm, umount, wc | Android (root) | Usage: ` void-umount [OPTION] ` <p> Unmount tool for Voidlinux chroot on Android. It was created for, and will only work for chroot images created using `void-install`. Run `void-umount --help` for more details.
**whatsapp-backup** | 7z, date, ls, mkdir, pm | Android (root) | Usage: ` whatsapp-backup [OPTION] ` <p> This tool creates and restores encrypted/unencrypted backups of `Whatsapp` (media, chats, etc) in external storage (SD card, USB OTG, etc), It will fallback to using internal storage if no external storage device is available. Run `whatsapp-backup --help` for more details.

## Installation

```
$ wget https://raw.githubusercontent.com/teth3r/tether/master/tether
$ chmod +x tether
$ tether --install <desired-folder>
```
Ensure that `<desired-folder>` is included in PATH

## LICENSE

Copyrights (c) 2023, Kolade Ayomide Olanrewaju <<koladeolanrewaju@tutanota.com>>

Distributed under the [GPL-3.0-or-later](../master/LICENSE).
