[Home](../)

[Next: hyprlang](./2-hyprlang.md)

***

# Introduction to hyprutils-0.2.6
The hyprutils package provides a utility library that is used by the entire
Hypr ecosystem.

## Package Information
- Download (HTTP): https://github.com/hyprwm/hyprutils/archive/refs/tags/v0.2.6.tar.gz
- Download md5sum: 0ada5cb26f08fd2ec9b0a248d7de0b48
- Download Size: 24K
- Build Size: 2.1M
- Build Time: less than 0.1 SBU

## hyprutils Dependencies
### Required
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html) and
  [Pixman](https://linuxfromscratch.org/blfs/view/svn/general/pixman.html)

## Installation of hyprutils
Install hyprutils by following the commands below:
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
