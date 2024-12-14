[Home](../)

[Prev: hyprcursor](./5-hyprcursor.md) - [Next: hyprwayland-scanner](./7-hyprwayland-scanner.md)

***

# Introduction to pugixml-1.14
The pugixml package provides a light-weight XML parser for C++.

## Package Information
- Download (HTTP): https://github.com/zeux/pugixml/releases/download/v1.14/pugixml-1.14.tar.gz
- Download md5sum: 06e4242ee2352ee63c2b6627c6e3addb
- Download Size: 384K
- Build Size: 3.2
- Build Time: less than 0.1 SBU

## pugixml Dependencies
### Required
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html)

## Installation of pugixml
Install pugixml by following the commands below:
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
