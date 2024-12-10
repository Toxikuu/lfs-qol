# Introduction to tomlplusplus
The tomlplusplus package is a TOML configuration parser for C++.

## Package Information
- Download (HTTP): https://github.com/marzer/tomlplusplus/archive/refs/tags/v3.4.0.tar.gz
- Download md5sum: c1f32ced14311fe949b9ce7cc3f7a867
- Download Size: 1.3M
- Build Size: 7.1M
- Build Time: less than 0.1 SBU

## Installation of tomlplusplus
Install tomlplusplus by following the commands below:
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
