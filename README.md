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
