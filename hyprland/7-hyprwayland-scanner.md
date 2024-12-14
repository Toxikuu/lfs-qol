[Home](../)

[Prev: pugixml](./6-pugixml.md) - [Next: aquamarine](./8-aquamarine.md)

***

# Introduction to hyprwayland-scanner-0.4.2
The hyprwayland-scanner package provides a Hyprland-specific implementation of
`wayland-scanner` provided by
[wayland-protocols](https://linuxfromscratch.org/blfs/view/svn/general/wayland-protocols.html).

## Package Information
- Download (HTTP): https://github.com/hyprwm/hyprwayland-scanner/archive/refs/tags/v0.4.2.tar.gz
- Download md5sum: 700e4abd566bdd5ac346e88da123cfaf
- Download Size: 12K
- Build Size: 1.9M
- Build Time: less than 0.1 SBU

## hyprwayland-scanner Dependencies
### Required
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html) and
  [pugixml](./6-pugixml.md)

## Installation of hyprwayland-scanner
Install hyprwayland-scanner by following the commands below:
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
