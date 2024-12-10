# Introduction to sdbus-c++-2.1.0
The sdbus-c++ package provides a C++ API for D-Bus.

## Package Information
- Download (HTTP): https://github.com/Kistler-Group/sdbus-cpp/archive/refs/tags/v2.1.0.tar.gz
- Download md5sum: ed9c6b8f1d93ecc9392b95b426b53cb1
- Download Size: 248K
- Build Size: 4.2M
- Build Time: less than 0.1 SBU

## sdbus-c++ Dependencies
### Required
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html) and
  [D-Bus](https://linuxfromscratch.org/blfs/view/svn/general/dbus.html)

### Recommended
  [doxygen](https://linuxfromscratch.org/blfs/view/svn/general/doxygen.html)
  (for generating documentation) and
  [elogind](https://linuxfromscratch.org/blfs/view/svn/general/elogind.html)

## Installation of sdbus-c++
Install sdbus-c++ by following the commands below:
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
