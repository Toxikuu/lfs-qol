[Prev](./1-fuse2.md): Fuse2 - [Next](./3-flatpak.md): Flatpak

# Introduction to OSTree-2024.9
The OSTree package for container deployment and the like. It is required by
[Flatpak](./3-flatpak.md).

## Package Information
- Download (HTTP): https://github.com/ostreedev/ostree/releases/download/v2024.9/libostree-2024.9.tar.xz
- Download md5sum: b37704388816de5e52f5497bfb16c5b7
- Download Size: 2.1M
- Build Size: 43M
- Build Time: 0.4 SBU

## Package Dependencies
**NOTE: These dependencies may not be in the right category.**
### Required
  [Fuse2](./1-fuse2.md) or [Fuse3](https://linuxfromscratch.org/blfs/view/svn/postlfs/fuse.html) and
  [Glib2](https://linuxfromscratch.org/blfs/view/svn/general/git.html) (with GObjectIntrospection)

### Recommended
  [elogind](https://linuxfromscratch.org/blfs/view/svn/general/elogind.html),
  [GTK-Doc](https://linuxfromscratch.org/blfs/view/svn/general/gtk-doc.html),
  [libsoup](https://linuxfromscratch.org/blfs/view/svn/basicnet/libsoup.html),
  [libsoup3](https://linuxfromscratch.org/blfs/view/svn/basicnet/libsoup3.html), and
  [libxslt](https://linuxfromscratch.org/blfs/view/svn/general/libxslt.html)

## Installation of OSTree
Install OSTree by following the commands below:
```Bash
./configure --prefix=/usr --disable-static &&
make
```

Now as the ***root*** user:
```Bash
make install
```
