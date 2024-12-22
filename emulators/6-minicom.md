[Home](../)

[Prev: lrzsz](./5-lrzsz.md) - [Next: gkermit](./7-gkermit.md)

***

# Introduction to minicom
Minicom is a serial communication program. It is provided in this category for communicating with UNIX 3.51 on
FreeBee and transferring files over xmodem.

## Package Information
- Download (HTTP): https://salsa.debian.org/minicom-team/minicom/-/archive/2.9/minicom-2.9.tar.gz
- Download md5sum: e52a82ee01e8de7d02d8fb7df8bafb02
- Download Size: 1020K
- Build Size: 6.6M
- Build Time: less than 0.1 SBU

## Package Dependencies
### Recommended
  [lrzsz](./5-lrzsz.md)

### Optional
  [C-Kermit](https://github.com/KermitProject/ckermit)

## Installation of minicom
Install minicom by running the commands below:
```Bash
./configure --prefix=/usr &&
make
```

Now as the ***root*** user:
```Bash
make install
```

