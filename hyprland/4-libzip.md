# Introduction to libzip-1.11.2
The libzip package contains a library and utilities for handling zip archives.

## Package Information
- Download (HTTP): https://libzip.org/download/libzip-1.11.2.tar.xz
- Download md5sum: c3551b8417082b0a9c74d19d1e5270ea
- Download Size: 772K
- Build Size: 13M
- Build Time: less than 0.1 SBU

## libzip Dependencies
### Required
  [GnuTLS](https://linuxfromscratch.org/blfs/view/svn/postlfs/gnutls.html)

## Installation of libzip
Install libzip by following the commands below:
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
