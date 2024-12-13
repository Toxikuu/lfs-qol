# Introduction to heirloom-doctools-080407
heirloom-doctools is a package that provides troff, nroff and related tools.
Those tools are enhanced versions of the tools released as a part of
OpenSolaris, which are themselves variants of ditroff, which are themselves
descendants of the original UNIX troff.

## Package Information
- Download (HTTP): https://downloads.sourceforge.net/heirloom/heirloom-doctools/080407/heirloom-doctools-080407.tar.bz2
- Download md5sum: 0fa9000c1508b793e533c6ffcaa0f647
- Download Size: 820K
- Build Size: 12M
- Build Time: 0.1 SBU

## Additional Download
- Required patch: [heirloom-doctools-080407-final-updates.patch](./patches/heirloom-doctools/heirloom-doctools-080407-final-updates.patch)
- Required patch: [heirloom-doctools-080407-gcc10.patch](./heirloom-doctools-080407-gcc10.patch)

## Package Dependencies
### Required
  [heirloom-ng](./2-heirloom-ng.md)

### Recommended
  [heirloom-sh](./4-heirloom-sh.md)

## Installation of heirloom-doctools
Apply a patch to bring up the source to the last upstream commit:
```Bash
patch -Np1 -i ../heirloom-doctools-080407-final-updates.patch
```

Now, apply a patch to fix a multiple definition issue breaking the compile:
```Bash
patch -Np1 -i ../heirloom-doctools-080407-gcc10.patch
```

If you have heirloom-sh installed, execute the following commands to tell heirloom-doctools 
where to find it:
```Bash
sed -i 's-/sbin/sh-/usr/5bin/sh-g' mk.config &&
sed -i 's-/sbin/sh-/usr/5bin/sh-g' stuff/showfont.sh
```

Otherwise, execute the following commands:
```Bash
sed -i 's-/sbin/sh-/bin/sh-g' mk.config &&
sed -i 's-/sbin/sh-/bin/sh-g' stuff/showfont.sh
```

Compile heirloom-doctools by following the commands below:
```Bash
make -j1
```

Now as the ***root*** user:
```Bash
make install
```

## Command Explanations
   ``make -j1``  - due to a race condition in ``pic``, force -j1 so we can build reliably.
