[Home](../)

[Prev: heirloom-ng](./2-heirloom-ng.md) - [Next: heirloom-sh](./4-heirloom-sh.md)

***

# Introduction to star from schilytools-2024-03-21
Due to various upstream-acknowledged issues in heirloom-ng tar, it is preferred
to use a different SVR4-compatible tar implementation. This package is exactly that.

## Package Information
- Download (HTTP): https://codeberg.org/schilytools/schilytools/releases/download/2024-03-21/schily-2024-03-21.tar.bz2
- Download md5sum: 42e8e766f2111e3eb8d900a5817cfe9d
- Download Size: 4.7M
- Build Size: 78M
- Build Time: 1.5 SBU

## Installation of star

Compile schilytools by following the commands below:
```Bash
make
```

Now install star and supplementary tools as the ***root*** user:
```Bash
install -v -m755 -d /usr/5bin &&
install -v -m755 star/OBJ/*/star /usr/5bin &&
install -v -m755 star_sym/OBJ/*/star_sym /usr/5bin &&
install -v -m755 tartest/OBJ/*/tartest /usr/5bin &&
install -v -m755 -d /usr/share/man/5man/man1 &&
install -v -m644 star/star.1 /usr/share/man/5man/man1 &&
install -v -m644 star_sym/star_sym.1 /usr/share/man/5man/man1 &&
install -v -m644 tartest/tartest.1 /usr/share/man/5man/man1
```
