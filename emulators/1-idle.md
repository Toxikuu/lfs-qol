[Home](../)

[Next: xhomer](./2-xhomer.md)

***

# Introduction to idle-r26
Idle is a minimalistic Lisa 1/2 emulator.

## Package Information
- Download (HTTP): https://sourceforge.net/code-snapshots/svn/i/id/idle-lisa-emu/code/idle-lisa-emu-code-r26.zip
- Download md5sum: b723b91a28dd079e2ddffcd332f54dbe
- Download Size: 216K
- Build Size: 4.1M
- Build Time: less than 0.1 SBU

## Additional Download
- Required ROMs: https://downloads.sourceforge.net/idle-lisa-emu/Windows%20binary/win_sdl_r23/idle_win32_bin.zip
- Required ROMs md5sum: 893e280f6512e3826ba1db2aab2c770b
- Required patch: [idle-r26-fix-sigill.patch](./patches/idle/idle-r26-fix-sigill.patch)
- Recommended patch: [idle-r26-system-roms.patch](./patches/idle/idle-r26-system-roms.patch)
- Optional patch: [idle-r26-pretend-we-are-a-lisa-2-10.patch](./patches/idle/idle-r26-pretend-we-are-a-lisa-2-10.patch)

## Package Dependencies
### Required
  [UnZip](https://www.linuxfromscratch.org/blfs/view/svn/general/unzip.html) (to unpack the distributions) and
  [sdl12-compat](https://www.linuxfromscratch.org/blfs/view/svn/multimedia/sdl.html)

## Installation of idle
Apply a patch to fix various SIGILLs due to security mitigations in modern processors:
```Bash
patch -Np1 -i ../idle-r26-fix-sigill.patch
```

Optionally, apply a patch to search for the ROMs in a system-wide location and not the
current directory:
```Bash
patch -Np1 -i ../idle-r26-system-roms.patch
```

!! WARNING WARNING WARNING !!  
ONLY apply the following patch if you REALLY know what you're doing. This patch pretends
the Lisa II/5 as properly emulated by the IDLE emulator is actually a Lisa II/10, without
actually introducing any new behaviour or adding any new hardware from the Lisa II/10.
It is VERY likely to introduce problems in software specifically coded for the Lisa II/10,
or software with proper support for it for that matter. The ONLY thing this patch is good at
is making SCO Xenix properly use a 10MB ProFile drive, because SCO Xenix' ProFile driver
makes an assumption about the installed hard disk size by looking at the system model,
and attempting to format a 10MB drive on a Lisa II/5, or a 5MB drive on a Lisa II/10, for
that matter, WILL result in errors from mkfs.  
  
If, after you read the above, you still want to apply the patch, run the following:
```Bash
patch -Np1 -i ../idle-r26-pretend-we-are-a-lisa-2-10.patch
```
!! WARNING WARNING WARNING !!  

Now install IDLE by following the commands below:
```Bash
make -f Makefile.unixsdl
```

Now as the ***root*** user:
```Bash
install -Dm755 idle /usr/bin/idle-emu
```

If you have applied the systemwide ROMs patch, install those ROMs as the ***root*** user:
```Bash
install -v -m755 -d /usr/share/idle/bios &&
install -v -m644 bios/vidstate.rom /usr/share/idle/bios &&
unzip ../idle_win32_bin.zip &&
install -v -m644 idle_win32_bin/bios/341-0175-h /usr/share/idle/bios &&
install -v -m644 idle_win32_bin/bios/341-0176-h /usr/share/idle/bios &&
install -v -m644 idle_win32_bin/bios/L175REVC.bin /usr/share/idle/bios &&
install -v -m644 idle_win32_bin/bios/L176REVC.bin /usr/share/idle/bios &&
rm -rf idle_win32_bin
```

## Configuring IDLE
If you have not applied the systemwide ROMs patch, you will have to put the bios/ folder
from idle_win32_bin.zip with vidstate.rom replaced from the source distribution into every
folder you plan on executing IDLE from. It is also of note that the ProFile drive image
is hardcoded to be in the current directory and is named ``profile.raw``.
