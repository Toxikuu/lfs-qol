# lfs-qol (Linux From Scratch - Quality of Life)

This repository is dedicated to documenting the installation of some packages
on an LFS system that do not appear in LFS, MLFS, BLFS, and GLFS.

This project also assumes you are using a SysVinit LFS system.

Such packages that are included are, but not limited to:
- Fuse-2.9.9 (needed for appimages)
- Flatpak
- Hyprland
- i3
- SVR4-style tools
- And much more!

# Where to read

TBD...

# Installation

How do I convert these XML files to HTML myself? You need to have some software
installed that deal with these conversions. Please read the `INSTALL.md` file to
determine what programs you need to install and where to get instructions to
install that software.

After that, you can build the html with a simple `make` command.
The default target builds the html in `$(HOME)/public_html/lfs-qol.`
It will by default make each package and section its own page then link
everything together for a smooth experience.

The dark theme is also the default, but you can switch the theme by
running `make LFS_QOL_THEME=<theme>`. `<theme>` can equal:
- light
- dark

Makefile targets are: `pdf`, `nochunks`, `validate`, and `lfs-qol-patch-list`.

`pdf`: builds GLFS as a PDF file.

`nochunks`: builds GLFS in one huge file.

`validate`:  does an extensive check for xml errors in the book.

`lfs-qol-patch-list`: generates a list of all GLFS controlled patches in the book.
