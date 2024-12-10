# Introduction to aquamarine-0.5.0
The aquamarine package provides a rendering backend library to use with Wayland
compositors. It was made to break Hyprland's dependency on wlroots.

## Package Information
- Download (HTTP): https://github.com/hyprwm/aquamarine/archive/refs/tags/v0.5.0.tar.gz
- Download md5sum: 43558331b2174f4b9457c0931236b466
- Download Size: 76K
- Build Size: 10M
- Build Time: 0.1 SBU

## aquamarine Dependencies
### Required
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html),
  [hyprutils](./1-hyprutils.md),
  [hyprwayland-scanner](./7-hyprwayland-scanner.md),
  [libdisplay-info](https://linuxfromscratch.org/blfs/view/svn/general/libdisplay-info.html),
  [libdrm](https://linuxfromscratch.org/blfs/view/svn/x/libdrm.html),
  [libinput](https://linuxfromscratch.org/blfs/view/svn/x/x7driver.html#libinput),
  [Mesa](https://linuxfromscratch.org/blfs/view/svn/x/mesa.html) (for the GBM),
  OpenGL ([Mesa](https://linuxfromscratch.org/blfs/view/svn/x/mesa.html) or
  [libglvnd](https://glfs-book.github.io/glfs/shareddeps/libglvnd.html)
  (Only the normal installation is required)),
  [Pixman](https://linuxfromscratch.org/blfs/view/svn/general/pixman.html),
  [pugixml](./6-pugixml.md),
  [seatd](https://glfs-book.github.io/glfs/shareddeps/seatd.html),
  [wayland](https://linuxfromscratch.org/blfs/view/svn/general/wayland.html), and
  [wayland-protocols](https://linuxfromscratch.org/blfs/view/svn/general/wayland-protocols.html)

### Recommended
  [hwdata](https://linuxfromscratch.org/blfs/view/svn/general/hwdata.html)

## Installation of aquamarine
Install aquamarine by following the commands below:
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
