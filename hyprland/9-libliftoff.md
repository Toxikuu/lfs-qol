[Home](../)

[Prev: aquamarine](./8-aquamarine.md) - [Next: Hyprland](./10-hyprland.md)

***

# Introduction to libliftoff
The libliftoff packages provides a library that handles KMS planes.

## Package Information
- Download (HTTP): https://gitlab.freedesktop.org/emersion/libliftoff/-/archive/v0.5.0/libliftoff-v0.5.0.tar.gz
- Download md5sum: e26483537eea0db5469b71c783189f74
- Download Size: 40K
- Build Size: 5.9
- Build Time: less than 0.1 SBU

## libliftoff Dependencies
### Required
  [libdrm](https://linuxfromscratch.org/blfs/view/svn/x/libdrm.html)

## Installation of libliftoff
Install libliftoff by following the commands below:
```Bash
mkdir build &&
cd    build &&

meson --prefix=/usr --buildtype=release .. &&
ninja
```

Now as the ***root*** user:
```Bash
ninja install
```
