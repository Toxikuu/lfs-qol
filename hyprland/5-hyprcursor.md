# Introduction to hyprcursor-0.1.10
The hyprcursor package provides a cursor format, an alternative to xcursor,
and is used by some Wayland compositors outside the Hypr ecosystem.

## Package Information
- Download (HTTP): https://github.com/hyprwm/hyprcursor/archive/refs/tags/v0.1.10.tar.gz
- Download md5sum: 3fb0adb1b8802cb1322f335c0b3bd575
- Download Size: 28K
- Build Size: 3.6M
- Build Time: 0.1 SBU

## hyprcursor Dependencies
### Required
  [Cairo](https://linuxfromscratch.org/blfs/view/svn/x/cairo.html),
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html),
  [hyprlang](./1-hyprlang.md),
  [librsvg](https://linuxfromscratch.org/blfs/view/svn/general/librsvg.html),
  [libzip](./4-libzip.md), and
  [tomlplusplus](./3-tomlplusplus.md)

## Installation of hyprcursor
Install hyprcursor by following the commands below:
```Bash
mkdir build &&
cd    build &&

cmake -D CMAKE_INSTALL_PREFIX=/usr   \
      -D CMAKE_BUILD_TYPE=Release    \
      -D CMAKE_SKIP_INSTALL_RPATH=ON \
      -G Ninja .. &&

ninja
```

Now as the ***root*** user:
```Bash
ninja install
```

## Command Explanations
  `-D CMAKE_SKIP_INSTALL_RPATH=ON`: This switch makes `cmake` remove hardcoded
  library search paths (rpath) when installing a binary executable file or a
  shared library. This package does not need rpath once it's installed into the
  standard location, and rpath may sometimes cause unwanted effects or even
  security issues.
