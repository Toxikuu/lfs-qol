# Introduction to Hyprland-0.45.2
Hyprland is an independent Wayland compositor aiming to have more features than
other Wayland compositors and be highly customizable, written in C++.

## Package Information
- Download (HTTP): https://github.com/hyprwm/Hyprland/releases/download/v0.45.2/source-v0.45.2.tar.gz
- Download md5sum: 8b3188d27d51a9689f8c8895b816bf71
- Download Size: 52M
- Build Size: 482M
- Build Time: 1.1 SBU

## Hyprland Dependencies
### Required
  [aquamarine](./8-aquamarine.md),
  [Cairo](https://linuxfromscratch.org/blfs/view/svn/x/cairo.html),
  [CMake](https://linuxfromscratch.org/blfs/view/svn/general/cmake.html),
  [elogind](https://linuxfromscratch.org/blfs/view/svn/general/elogind.html),
  [GLib2](https://linuxfromscratch.org/blfs/view/svn/general/glib2.html),
  [Glslang](https://linuxfromscratch.org/blfs/view/svn/x/glslang.html),
  [hyprcursor](./5-hyprcursor.md),
  [hyprlang](./2-hyprlang.md),
  [hyprutils](./1-hyprutils.md),
  [hyprwayland-scanner](./7-hyprwayland-scanner.md),
  [libdisplay-info](https://linuxfromscratch.org/blfs/view/svn/general/libdisplay-info.html),
  [libdrm](https://linuxfromscratch.org/blfs/view/svn/x/libdrm.html),
  OpenGL ([Mesa](https://linuxfromscratch.org/blfs/view/svn/x/mesa.html) or
  [libglvnd](https://glfs-book.github.io/glfs/shareddeps/libglvnd.html)
  (only the normal installation is needed)),
  [libinput](https://linuxfromscratch.org/blfs/view/svn/x/x7driver.html#libinput),
  [libliftoff](./9-libliftoff.md),
  [libxkbcommon](https://linuxfromscratch.org/blfs/view/svn/general/libxkbcommon.html),
  [Pango](https://linuxfromscratch.org/blfs/view/svn/x/pango.html) (with Cairo),
  [Pixman](https://linuxfromscratch.org/blfs/view/svn/general/pixman.html),
  [seatd](https://glfs-book.github.io/glfs/shareddeps/seatd.html),
  [tomlplusplus](./3-tomlplusplus.md),
  [Vulkan-Loader](https://linuxfromscratch.org/blfs/view/svn/x/vulkan-loader.html),
  [Wayland](https://linuxfromscratch.org/blfs/view/svn/general/wayland.html),
  [Wayland-Protocols](https://linuxfromscratch.org/blfs/view/svn/general/wayland-protocols.html),
  [XCB Utils](https://glfs-book.github.io/glfs/shareddeps/xcb-utils.html)
  (xcb-util-errors is necessary; only normal installation is necessary), and
  [Xorg Libraries](https://linuxfromscratch.org/blfs/view/svn/x/x7lib.html)

### Recommended
  [Xwayland](https://linuxfromscratch.org/blfs/view/svn/x/xwayland.html)

### Optional
  [cpio](https://linuxfromscratch.org/blfs/view/svn/general/cpio.html) (to
  build and install plugins)

## Installation of Hyprland
Install Hyprland by following the commands below:
```Bash
rm -fv scripts/generateVersion.sh &&
make release PREFIX=/usr
```

Now as the ***root*** user:
```Bash
make install &&
rm -fv /usr/include/hyprland/src/version.h.in
```

## Command Explanations
  `rm -fv scripts/generateVersion.sh`: This command works around an issue where
  this package installs an invalid `/usr/include/hyprland/src/version.h` as it
  is missing all values.

  `rm -fv /usr/include/hyprland/src/version.h.in`: This command removes an
  unneeded `.h.in` file, an artifact from the previous explained command.

## Configuring Hyprland
Hyprland can be configured via `"$HOME"/.config/hypr/hyprland.conf`. First
create the directory then copy the file to it:
```Bash
mkdir -pv "$HOME"/.config/hypr &&
cp /usr/share/hypr/hyprland.conf "$HOME"/.config/hypr
```

Now inspect the file and make any changes to suit your workflow.
