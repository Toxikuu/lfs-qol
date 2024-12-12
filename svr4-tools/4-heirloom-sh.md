# Introduction to heirloom-sh-050706
heirloom-sh is a portable variant of the traditional Unix Bourne Shell.

## Package Information
- Download (HTTP): https://downloads.sourceforge.net/heirloom/heirloom-sh/050706/heirloom-sh-050706.tar.bz2
- Download md5sum: 9169d9b3b845cb63c598ea29b8d2dfa0
- Download Size: 84K
- Build Size: 1000K
- Build Time: less than 0.1 SBU

## Additional Download
- Required patch: [heirloom-sh-050706-final-updates.patch](./patches/heirloom-sh/heirloom-sh-050706-final-updates.patch)
- Required patch: [heirloom-sh-050706-glibc234.patch](./patches/heirloom-sh/heirloom-sh-050706-glibc234.patch)

## Package Dependencies
### Required
  [heirloom-ng](./2-heirloom-ng.md), and

## Installation of heirloom-sh
Apply a patch to bring up the source to the last upstream commit:
```Bash
patch -Np1 -i ../heirloom-sh-050706-final-updates.patch
```

Now, apply a patch to fix the build with glibc 2.34 or newer:
```Bash
patch -Np1 -i ../heirloom-sh-050706-glibc234.patch
```

Compile heirloom-ng by following the commands below:
```Bash
make
```

Now as the ***root*** user:
```Bash
make install
```
## Configuring heirloom-sh
Update /etc/shells to include the Bourne shell program names (as the ***root*** user):
```Bash
cat >> /etc/shells << "EOF"
/usr/5bin/sh
/usr/5bin/jsh
EOF
```
