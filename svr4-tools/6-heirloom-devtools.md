[Home](../)

[Prev: heirloom-doctools](./5-heirloom-doctools.md) - [Next: s-nail](./7-s-nail.md)

***

# Introduction to heirloom-devtools-070527
heirloom-devtools is a package that provides yacc, lex, m4, make and SCCS.
Those tools are portable derivatives of the tools released as a part of
OpenSolaris, which were derived from the original UNIX versions.

## Package Information
- Download (HTTP): https://downloads.sourceforge.net/heirloom/heirloom-devtools/070527/heirloom-devtools-070527.tar.bz2
- Download md5sum: a777644467001a23da024ce66017045d
- Download Size: 376K
- Build Size: 6.2M
- Build Time: 0.1 SBU

## Additional Download
- Required patch: [heirloom-devtools-070527-final-updates.patch](./patches/heirloom-devtools/heirloom-devtools-070527-final-updates.patch)
- Required patch: [heirloom-devtools-070527-fix-make-build.patch](./patches/heirloom-devtools/heirloom-devtools-070527-fix-make-build.patch)

## Package Dependencies
### Required
  [heirloom-ng](./2-heirloom-ng.md) and
  [libtirpc](https://www.linuxfromscratch.org/blfs/view/svn/basicnet/libtirpc.html)

### Recommended
  [heirloom-sh](./4-heirloom-sh.md)

## Installation of heirloom-devtools
Apply a patch to bring up the source to the last upstream commit:
```Bash
patch -Np1 -i ../heirloom-devtools-070527-final-updates.patch
```

Now, apply a patch to fix the compile of the make utility:
```Bash
patch -Np1 -i ../heirloom-devtools-070527-fix-make-build.patch
```

Execute the following command to tell heirloom-devtools to use libtirpc:
```Bash
sed -i 's=-O=-O -I/usr/include/tirpc=g' mk.config
```

If you have heirloom-sh installed, execute the following commands to tell heirloom-devtools
where to find it:
```Bash
sed -i 's-/sbin/sh-/usr/5bin/sh-g' mk.config &&
sed -i 's-/bin/sh-/usr/5bin/sh-g' mk.config &&
sed -i 's-/bin/sh-/usr/5bin/sh-g' sccs/src/sccsdiff.sh
```

Otherwise, execute the following commands:
```Bash
sed -i 's-/sbin/sh-/bin/sh-g' mk.config
```

Compile heirloom-devtools by following the commands below:
```Bash
make
```

Now as the ***root*** user:
```Bash
make install
```
