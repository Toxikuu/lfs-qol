# Introduction to xdg-desktop-portal-hyprland-1.3.8
The xdg-desktop-portal-hyprland package provides a portal backend for Hyprland.

## Package Information
- Download (HTTP): https://github.com/hyprwm/xdg-desktop-portal-hyprland/archive/refs/tags/v1.3.8.tar.gz
- Download md5sum: 9fb1561bd5c6068e4609712353de6e86
- Download Size: 52K
- Build Size: 6.6M
- Build Time: 0.1 SBU

## xdg-desktop-portal-hyprland Dependencies
### Required
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html),
  [hyprlang](./2-hyprlang.md),
  [hyprutils](./1-hyprutils.md),
  [hyprwayland-scanner](./7-hyprwayland-scanner.md),
  [libdrm](https://linuxfromscratch.org/blfs/view/svn/x/libdrm.html),
  [Mesa](https://linuxfromscratch.org/blfs/view/svn/x/mesa.html) (for the GBM),
  [Pipewire](https://linuxfromscratch.org/blfs/view/svn/multimedia/pipewire.html),
  [Qt-6](https://linuxfromscratch.org/blfs/view/svn/x/qt6.html),
  [sdbus-c++](./11-sdbus-cpp.md),
  [Wayland](https://linuxfromscratch.org/blfs/view/svn/general/wayland.html),
  [Wayland-Protocols](https://linuxfromscratch.org/blfs/view/svn/general/wayland-protocols.html), and
  [xdg-desktop-portal](https://linuxfromscratch.org/blfs/view/svn/x/xdg-desktop-portal.html)

### Recommended
  [inih](https://linuxfromscratch.org/blfs/view/svn/general/inih.html)

### Optional Runtime
  [grim](https://archlinux.org/packages/extra/x86_64/grim/)
  (for the screenshot portal) and
  [slurp](https://archlinux.org/packages/extra/x86_64/slurp/) (for the
  interactive mode in the screenshot portal)

## Installation of xdg-desktop-portal-hyprland
Install xdg-desktop-portal-hyprland by following the commands below:
```Bash
rm -rf subprojects/sdbus-cpp &&
mkdir build                  &&
cd    build                  &&

cmake -D CMAKE_INSTALL_PREFIX=/usr   \
      -D CMAKE_BUILD_TYPE=Release    \
      -G Ninja .. &&

ninja
```

Now as the ***root*** user:
```Bash
ninja install &&
rm -rvf /usr/lib/systemd
```

## Command Explanations
  `rm -rf subprojects/sdbus-cpp`: This command removes vendored source code
  that FTBFS.

  `rm -rvf /usr/lib/systemd`: This command removes unnecessary Systemd files.
