# Introduction to hyprlang-0.5.3
The hyprlang package provides a configuration language used by the Hypr
ecosystem of packages and may be used by other packages not in the ecosystem.

## Package Information
- Download (HTTP): https://github.com/hyprwm/hyprlang/archive/refs/tags/v0.5.3.tar.gz
- Download md5sum: daec6dd0f8c6b4c86969f1d000f2ab16
- Download Size: 56K
- Build Size: 2.0M
- Build Time: less than 0.1 SBU

## hyprlang Dependencies
### Required
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html) and
  [hyprutils](./1-hyprutils.md)

## Installation of hyprlang
Install hyprlang by following the commands below:
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
