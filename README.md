# tether

(This documentation is currently a work in progress)

<p>tether is a multi-call shell script that combines many applets/functions into a single executable.</p>

<p>Think busybox or toybox, except as a shell script, you can create symbolic links to tether for each defined function and it will behave/act like whatever it was invoked as.<p>

# Currently defined functions

. [benchmark](#benchmark)
. [chroot-backup](#chroot-backup)
. [dotfiles](#dotfiles)
. [extract](#extract)
. [ll](#ll)
. [mkcp](#mkcp)
. [mkmv](mkmv)
. [mktouch](#mktouch)
. [omaps-backup](omaps-backup)
. [opencamera-backup](opencamera-backup)
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

## benchmark
This is a simple single core performance benchmark tool, that uses the Mersenne primality test.

#### Usage: benchmark \[OPTION] \[NUMBER]
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

#### Example:
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
Creates an encrypted/unencrypted backup of chroot container image (created with void-install) in user specified folder.

#### Usage: chroot-backup \[OPTION] \[FOLDER]
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

Create chroot image backup in specified folder
```

#### Example:
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

#### Usage: dotfiles \[OPTION]
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

#### Example:
```
$ dotfiles --vim

[+] Finished updating '~/.vimrc'
[+] Finished updating '/usr/share/vim/vim90/colors/tether.vim'
```

## extract
This is a wrapper for 7z and bsdtar for extracting archive files.

#### Usage: extract \[FILE...]
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

#### Example:
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

## ll
This is a wrapper for ls

#### Usage: ll \[OPTION] \[NUMBER] [FOLDER/FILE...]
```
$ ll --help

ll (C) 2023, Kolade Ayomide Olanrewaju (tether)
ll is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    ll [OPTION] [NUMBER] [FOLDER/FILE...]

Examples: ll /sdcard/folder
          ll 1
          ll 1 folder
          ll -l folder
          ll -l 1 folder
          ll -l 1 folder folder2
          ll -l 1 folder/folder

Options: -h, --help     Print out this message
         -V, --version  Show version information

All 'ls' options are also available here

Expand 'ls' functionality
```

#### Example:
```
$ ll 3 data/local

../../../data/local:
total 24k
tests  tmp  traces
```

## mkcp
Copies files/folders to the specified folder

#### Usage: mkcp \[FOLDER] \[FILE...] 
```
$ mkcp --help

mkcp (C) 2023, Kolade Ayomide Olanrewaju (tether)
mkcp is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    mkcp [OPTION]
          mkcp [FOLDER] [FILE...]

Examples: mkcp --help
          mkcp newfolder file1 file2
          mkcp newfolder *

Options: -h, --help     Print out this message
         -V, --version  Show version information

Copy file/folder to the specified folder
```

#### Example:
```
$ mkcp newfolder ~/.bash* ~/.vimrc

[+] Copied '/home/user/.bash_history' to 'newfolder
[+] Copied '/home/user/.bashrc' to 'newfolder'
[+] Copied '/home/user/.vimrc' to 'newfolder'

$ ll newfolder

.bash_history .bashrc .vimrc
```

## mkmv
Moves files/folders to the specified folder

#### Usage: mkmv \[FOLDER] \[FILE...] 
```
$ mkmv --help

mkmv (C) 2023, Kolade Ayomide Olanrewaju (tether)
mkmv is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    mkmv [OPTION]
          mkmv [FOLDER] [FILE...]

Examples: mkmv --help
          mkmv newfolder file1 file2
          mkmv newfolder *

Options: -h, --help     Print out this message
         -V, --version  Show version information

Move file/folder to the specified folder
```

#### Example:
```
$ mkmv newfolder ~/.bash* ~/.vimrc

[+] Moved '/home/user/.bash_history' to 'newfolder
[+] Moved '/home/user/.bashrc' to 'newfolder'
[+] moved '/home/user/.vimrc' to 'newfolder'

$ ll newfolder

.bash_history .bashrc .vimrc
```

## mktouch
Creates specified empty file(s) in the specified folder

#### Usage: mktouch \[FOLDER] \[FILE...] 
```
$ mktouch --help

mktouch (C) 2023, Kolade Ayomide Olanrewaju (tether)
mktouch is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    mktouch [OPTION]
          mktouch [FOLDER] [FILE...]

Examples: mktouch --help
          mktouch newfolder file1 file2
          mktouch newfolder *

Options: -h, --help     Print out this message
         -V, --version  Show version information

Create empty file(s) in the specified folder
```

#### Example:
```
$ mktouch Aperture Aperture.apk oat

[+] Created 'Aperture.apk' in 'Aperture'
[+] Created 'oat' in 'Aperture'

$ ll Aperture

Aperture.apk oat
```

## omaps-backup
Creates an encrypted/unencrypted backup of Organic Maps downloaded mapfiles in external storage

#### Usage: omaps-backup \[OPTION]
```
$ omaps-backup --help

omaps-backup (C) 2023, Kolade Ayomide Olanrewaju (tether)
omaps-backup is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    omaps-backup [OPTION]

Examples: omaps-backup --encrypt
          omaps-backup --restore

Options: -en, --encrypt    Create an encrypted backup
         -h,  --help       Print out this message
         -l,  --list       List all available backups
         -un, --unencrypt  Create an unencrypted backup
         -r,  --restore    Restore organic maps from available backups
         -V,  --version    Show version information

Create and restore organic maps backups
```

#### Example:
```
$ omaps-backup --encrypt

[*] Creating encrypted backup 'omaps-backup.23.11.05.1013.7z'

Input Password:
Verify Password:

[+] Finished encrypting 'omaps-backup.23.11.05.1013.7z'
    Check '/storage/xxxx-xxxx/Misc/omaps-backup'

$ omaps-backup --restore
 
████████╗███████╗████████╗██╗   ██╗███████╗██████═╗ 
╚══██╔══╝██╔════╝╚══██╔══╝██║   ██║██╔════╝██╔═══██ 
   ██║   ███████╗   ██║   ████████║███████╗███████═╗
   ██║   ██╔════╝   ██║   ██╔═══██║██╔════╝██╔═══██║
   ██║   ███████╗   ██║   ██║   ██║███████╗██║   ██║
   ╚═╝   ╚══════╝   ╚═╝   ╚═╝   ╚═╝╚══════╝╚═╝   ╚═╝
 
[*] Restoring organic maps

1.omaps-backup.23.09.27.0340.7z
2.omaps-backup.23.10.12.1918.7z
3.omaps-backup.23.11.05.1013.7z

Select preferred backup: 3

[*]  Restoring organic maps using 'omaps-backup.23.11.05.1013.7z'

7-Zip (z) 22.01 (arm64) : Copyright (c) 1999-2022 Igor Pavlov : 2022-07-15
 64-bit arm_v:8 locale=C UTF8=- Threads:8, ASM

Scanning the drive for archives:
1 file, 343119954 bytes (328 MiB)

Extracting archive: omaps-backup.23.11.05.1013.7z

Enter password:
--
Path = omaps-backup.23.11.05.1013.7z
Type = 7z
Physical Size = 343119954
Headers Size = 322
Method = LZMA2:18 7zAES
Solid = -
Blocks = 3

Everything is Ok

Files: 3
Size:       343097989
Compressed: 343119954

7-Zip (z) 22.01 (arm64) : Copyright (c) 1999-2022 Igor Pavlov : 2022-07-15
 64-bit arm_v:8 locale=C UTF8=- Threads:8, ASM

Scanning the drive for archives:
1 file, 343096245 bytes (328 MiB)

Extracting archive: omaps-sdcard.7z
--
Path = omaps-sdcard.7z
Type = 7z
Physical Size = 343096245
Headers Size = 367
Method = LZMA2:18
Solid = +
Blocks = 4

Everything is Ok

Folders: 2
Files: 6
Size:       518757870
Compressed: 343096245

7-Zip (z) 22.01 (arm64) : Copyright (c) 1999-2022 Igor Pavlov : 2022-07-15
 64-bit arm_v:8 locale=C UTF8=- Threads:8, ASM

Scanning the drive for archives:
1 file, 82 bytes (1 KiB)

Extracting archive: omaps-storage.7z
--
Path = omaps-storage.7z
Type = 7z
Physical Size = 82
Headers Size = 82
Solid = -
Blocks = 0

Everything is Ok

Folders: 1
Files: 0
Size:       0
Compressed: 82

7-Zip (z) 22.01 (arm64) : Copyright (c) 1999-2022 Igor Pavlov : 2022-07-15
 64-bit arm_v:8 locale=C UTF8=- Threads:8, ASM

Scanning the drive for archives:
1 file, 1662 bytes (2 KiB)

Extracting archive: omaps-data.7z
--
Path = omaps-data.7z
Type = 7z
Physical Size = 1662
Headers Size = 312
Method = LZMA2:6k
Solid = +
Blocks = 1

Everything is Ok

Folders: 2
Files: 4
Size:       5756
Compressed: 1662

[+] Finished restoring 'omaps-backup.23.11.05.1013.7z'
```

## opencamera-backup
Creates an encrypted/unencrypted backup of Open Camera config files in external storage

#### Usage: opencamera-backup \[OPTION]
```
$ opencamera-backup --help

opencamera-backup (C) 2023, Kolade Ayomide Olanrewaju (tether)
opencamera-backup is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    opencamera-backup [OPTION]

Examples: opencamera-backup --encrypt
          opencamera-backup --restore

Options: -en, --encrypt    Create an encrypted backup
         -h,  --help       Print out this message
         -l,  --list       List all available backups
         -un, --unencrypt  Create an unencrypted backup
         -r,  --restore    Restore organic maps from available backups
         -V,  --version    Show version information

Create and restore open camera backups
```

#### Example:
```
$ opencamera-backup --encrypt

[*] Creating encrypted backup 'opencamera-backup.23.11.05.1013.7z'

Input Password:
Verify Password:

[+] Finished encrypting 'opencamera-backup.23.11.05.1013.7z'
    Check '/storage/xxxx-xxxx/Misc/opencamera-backup'

$ opencamera-backup --restore
 
████████╗███████╗████████╗██╗   ██╗███████╗██████═╗ 
╚══██╔══╝██╔════╝╚══██╔══╝██║   ██║██╔════╝██╔═══██ 
   ██║   ███████╗   ██║   ████████║███████╗███████═╗
   ██║   ██╔════╝   ██║   ██╔═══██║██╔════╝██╔═══██║
   ██║   ███████╗   ██║   ██║   ██║███████╗██║   ██║
   ╚═╝   ╚══════╝   ╚═╝   ╚═╝   ╚═╝╚══════╝╚═╝   ╚═╝
 
[*] Restoring organic maps

1.opencamera-backup.23.09.27.0340.7z
2.opencamera-backup.23.11.05.1013.7z

Select preferred backup: 2

[*]  Restoring organic maps using 'opencamera-backup.23.11.05.1013.7z'

7-Zip (z) 22.01 (arm64) : Copyright (c) 1999-2022 Igor Pavlov : 2022-07-15
 64-bit arm_v:8 locale=C UTF8=- Threads:8, ASM

Scanning the drive for archives:
1 file, 343119954 bytes (328 MiB)

Extracting archive: opencamera-backup.23.11.05.1013.7z

Enter password:
--
Path = opencamera-backup.23.11.05.1013.7z
Type = 7z
Physical Size = 343119954
Headers Size = 322
Method = LZMA2:18 7zAES
Solid = -
Blocks = 3

Everything is Ok

Files: 3
Size:       343097989
Compressed: 343119954

7-Zip (z) 22.01 (arm64) : Copyright (c) 1999-2022 Igor Pavlov : 2022-07-15
 64-bit arm_v:8 locale=C UTF8=- Threads:8, ASM

Scanning the drive for archives:
1 file, 343096245 bytes (328 MiB)

Extracting archive: opencamera-sdcard.7z
--
Path = opencamera-sdcard.7z
Type = 7z
Physical Size = 343096245
Headers Size = 367
Method = LZMA2:18
Solid = +
Blocks = 4

Everything is Ok

Folders: 2
Files: 6
Size:       518757870
Compressed: 343096245

[+] Finished restoring 'opencamera-backup.23.11.05.1013.7z'
```

## setup
Post-installation setup script for Voidlinux

#### Usage: setup \[OPTION]
```
$ setup --help

setup (C) 2023, Kolade Ayomide Olanrewaju (tether)
setup is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    setup [OPTION]

Examples: setup
          setup --help

Options: -h, --help     Print out this message
         -V, --version  Show version information

Post-installation setup utility for voidlinux
```

#### Example:
```
$ setup

████████╗███████╗████████╗██╗   ██╗███████╗██████═╗ 
╚══██╔══╝██╔════╝╚══██╔══╝██║   ██║██╔════╝██╔═══██ 
   ██║   ███████╗   ██║   ████████║███████╗███████═╗
   ██║   ██╔════╝   ██║   ██╔═══██║██╔════╝██╔═══██║
   ██║   ███████╗   ██║   ██║   ██║███████╗██║   ██║
   ╚═╝   ╚══════╝   ╚═╝   ╚═╝   ╚═╝╚══════╝╚═╝   ╚═╝
 
[*] Setting up Voidlinux

Install Desktop Environment: 
1.KDE 
2.Gnome 
3.Xfce 
4.Cinnamon 
5.Skip 
6.Exit

Select Desktop: 5

[*] Skipping Desktop Environment Installation

Install GPU Drivers: 
1.Intel 
2.AMD/radeon 
3.Skip 
4.Exit

Select GPU: 3

[*] Skipping GPU Driver Installation

Install VM Software (qemu, virt-manager): 
1.Yes 
2.Skip 
3.Exit

Select option: 2

[*] Skipping VM Software Installation

Install Printer Software: 
1.HP 
2.Epson 
3.Brother 
4.Skip 
5.Exit

Select Printer: 4

[*] Skipping Printer Software Installation

Install Audio Software: 
1.Pulseaudio 
2.ALSA 
3.Pipewire 
4.Skip 
5.Exit

Select Audio: 4

[*] Skipping Audio Software Installation

Install Extra/Misc Software (krita, libreoffice, wine): 
1.Yes 
2.Skip 
3.Exit

Select option: 2

[*] Skipping Extra/Misc Software Installation

Install Development Software (gcc, make tmux, vim, urxvt): 
1.Yes 
2.Skip 
3.Exit

Select option: 2

[*] Skipping Development Software Installation

Install Dotfiles (bash, tmux, vim, urxvt): 
1.Yes 
2.Skip 
3.Exit

Select option: 2

[*] Skipping Dotfiles Installation

Install Browser Software: 
1.Chromium 
2.Firefox 
3.Skip 
4.Exit

Select Browser: 3

[*] Skipping Browser Software Installation

Install Media-Player Software: 
1.VLC 
2.MPV 
3.Skip 
4.Exit

Select Media-Player: 3

[*] Skipping Media-Player Software Installation

Change Default Timezone: 
1.Yes 
2.Skip 
3.Exit

Select option: 2

[*] Skipping Timezone Change

Install Automatic Backlight Control: 
1.Yes 
2.Skip 
3.Exit

Select option: 2

[*] Skipping Automatic Backlight Control

Install Networking Software: 
1.Yes 
2.Skip 
3.Exit

Select option: 2

[*] Skipping Networking Software Installation

[-] Nothing left to do, exiting
```

## tfetch
System resource information tool

#### Usage: tfetch \[OPTION]
```
$ tfetch --help

tfetch (C) 2023, Kolade Ayomide Olanrewaju (tether)
tfetch is Licensed under GPL-3.0-or-later. See <https://www.gnu.org/licenses/> for detailed copyright notices.

Usage:    tfetch [OPTION]

Examples: tfetch
          tfetch --help

Options: -h, --help     Print out this message
         -V, --version  Show version information

System resource information tool
```

#### Example:
```
$ tfetch

user@user
 -----------------
Device:   Dell Inc. Inspiron 7375
OS:       Void Linux x86_64
Kernel:   Linux 6.5.9_1 
Init:     runit
Packages: 1058 xbps
Shell:    bash 5.2.15(1)
Desktop:  GNOME (wayland)
CPU:      AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx (4) @ 1600Mhz
CPU_CLK:  0 @ 1600Mhz, 1 @ 1600Mhz, 2 @ 1600Mhz, 3 @ 1380Mhz, 4 @ 1368Mhz, 5 @ 1600Mhz, 6 @ 3242Mhz, 7 @ 2000Mhz
Battery:  Full, 100% - (96.14% Health)
CPU Temp: [ ■■■■■■■■■■---------- ] 52.0°C
RAM:      [ ■■■■■--------------- ] 3916 / 13874 MiB (28%)
Swap:     [ -------------------- ] 0 / 0 MiB
Uptime:   8 days 20 hours 26 minutes 44 seconds
```

## tether

This is the main script.

#### Usage: tether \[FUNCTION] \[ARGUMENTS...]

```
$ tether --help

tether 23.11.05.1013-x86_64 (C) 2023, Kolade Ayomide Olanrewaju (tether)
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

Currently defined functions (20):
benchmark, chroot-backup, dotfiles, extract, ll, mkcp, mkmv, mktouch, omaps-backup, opencamera-backup, setup, tfetch, touchzip, viw, void-backup, void-deploy, void-install, void-mount, void-umount, whatsapp-backup
```