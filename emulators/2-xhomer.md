[Home](../)

[Prev: idle](./1-idle.md) - [Next: freebee](./3-freebee.md)

***

# Introduction to xhomer-2-19-24
XHomer is an emulator for the DEC Pro 350 computer, a PDP-11-based machine that was sold in the early to mid-80s.

## Package Information
- Download (HTTP): http://xhomer.isani.org/xhomer/xhomer-2-19-24.tgz
- Download md5sum: b47f5a26b154fe746e8aafe3f1a0ffad
- Download Size: 444K
- Build Size: 2.3M
- Build Time: less than 0.1 SBU

## Additional Download
- Required patch: [xhomer-2-19-24-close-properly.patch](./patches/xhomer/xhomer-2-19-24-close-properly.patch)
- Required patch: [xhomer-2-19-24-fix-util-build.patch](./patches/xhomer/xhomer-2-19-24-fix-util-build.patch)

## Package Dependencies
### Required
  [The X Window System](https://www.linuxfromscratch.org/blfs/view/svn/x/installing.html)

## Installation of xhomer
Apply a patch to allow for proper restoring of terminal settings in certain commonly
used scenarios of closing XHomer:
```Bash
patch -Np1 -i ../xhomer-2-19-24-close-properly.patch
```

Now, apply a patch to fix compilation of misc included utilities:
```Bash
patch -Np1 -i ../xhomer-2-19-24-fix-util-build.patch
```

Then, install XHomer by following the commands below:
```Bash
make &&
cc UTILITIES/lbn2xhomer.c -o UTILITIES/lbn2xhomer &&
cc UTILITIES/venix2xhomer.c -o UTILITIES/venix2xhomer
```

Now as the ***root*** user:
```Bash
install -Dm755 xhomer /usr/bin/xhomer &&
install -Dm755 UTILITIES/lbn2xhomer /usr/bin/lbn2xhomer &&
install -Dm755 UTILITIES/venix2xhomer /usr/bin/venix2xhomer
```

Optionally, install the documentation as the ***root*** user:
```Bash
install -v -m755 -d /usr/share/doc/xhomer-2-19-24 &&
install -v -m644 DOC/* /usr/share/doc/xhomer-2-19-24
```
