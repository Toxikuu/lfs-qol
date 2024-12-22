[Home](../)

[Prev: s4-3b1-pc7300](./4-s4-3b1-pc7300.md) - [Next: minicom](./6-minicom.md)

***

# Introduction to lrzsz-0.12.20
lrzsz is a UNIX communication package providing the XMODEM, YMODEM and ZMODEM file transfer protocols. 

## Package Information
- Download (HTTP): https://www.ohse.de/uwe/releases/lrzsz-0.12.20.tar.gz
- Download md5sum: b5ce6a74abc9b9eb2af94dffdfd372a4
- Download Size: 276K
- Build Size: 4.8M
- Build Time: 0.2 SBU

## Additional Download
- Required patch: [lrzsz-0.12.20-AR.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-AR.patch)
- Required patch: [lrzsz-0.12.20-automake-1.12.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-automake-1.12.patch)
- Required patch: [lrzsz-0.12.20-automake-1.13.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-automake-1.13.patch)
- Required patch: [lrzsz-0.12.20-c23.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-c23.patch)
- Required patch: [lrzsz-0.12.20-c99.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-c99.patch)
- Required patch: [lrzsz-0.12.20-configure-clang16.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-configure-clang16.patch)
- Required patch: [lrzsz-0.12.20-fix-integer-overflow.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-fix-integer-overflow.patch)
- Required patch: [lrzsz-0.12.20-gettext-0.20.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-gettext-0.20.patch)
- Required patch: [lrzsz-0.12.20-gettext-0.22.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-0.12.20-gettext-0.22.patch)
- Required patch: [lrzsz-autotools.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-autotools.patch)
- Required patch: [lrzsz-implicit-decl.patch](https://github.com/gentoo/gentoo/raw/f7f659b24dba90b0278e54a2f4d966e24c7a94fb/net-dialup/lrzsz/files/lrzsz-implicit-decl.patch)

## Installation of lrzsz
First, apply patches to fix various configuration, build and security issues:
```Bash
patch -Np1 -i ../lrzsz-autotools.patch &&
patch -Np1 -i ../lrzsz-implicit-decl.patch &&
patch -Np1 -i ../lrzsz-0.12.20-automake-1.12.patch &&
patch -Np1 -i ../lrzsz-0.12.20-automake-1.13.patch &&
patch -Np1 -i ../lrzsz-0.12.20-gettext-0.20.patch &&
patch -Np1 -i ../lrzsz-0.12.20-AR.patch &&
patch -Np1 -i ../lrzsz-0.12.20-configure-clang16.patch &&
patch -Np1 -i ../lrzsz-0.12.20-gettext-0.22.patch &&
patch -Np1 -i ../lrzsz-0.12.20-c99.patch &&
patch -Np1 -i ../lrzsz-0.12.20-fix-integer-overflow.patch &&
patch -Np1 -i ../lrzsz-0.12.20-c23.patch
```

Now, regenerate the autoconf files:
```Bash
touch config.rpath &&
rm -vf missing &&
rm -vf acconfig.h &&
autoreconf -fiv
```

Then, configure and compile the package:
```Bash
./configure --prefix=/usr --disable-nls &&
make
```

Now as the ***root*** user:
```Bash
make install &&

for x in {r,s}{b,x,z} ; do
	ln -svf l${x} /usr/bin/${x} &&
	ln -svf l${x:0:1}z.1 /usr/share/man/man1/${x}.1 &&
	[ "${x:1:1}" = "z" ] || ln -svf l${x:0:1}z.1 /usr/share/man/man1/l${x}.1
done
```

## Command Explanations
   ``touch config.rpath`` - automake gets all unhappy if this file is missing, so create it.

   ``rm -vf missing`` - The provided ``missing`` file is too old to be used, so remove it for automake
   to put in a newer copy.

   ``rm -vf acconfig.h`` - autoheader does not like seeing this file, so remove it.

   ``--disable-nls`` - NLS is broken for this package due to missing files.

   ``for i in {r,s}{b,x,z} ; do...`` - Create compatibility symlinks for the original rzsz package.
   This is required for ``minicom``.
