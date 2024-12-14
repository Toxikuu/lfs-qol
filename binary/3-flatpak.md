[Home](../)

[Prev: OSTree](./2-ostree.md)

***

# Introduction to Flatpak-1.14.10
Flatpak allows you to download apps and run them in a sandbox. It downloads all
of the dependencies of a given package in a sandbox and allows you to run the
package as if it was not in a sandbox. Some packages only exist as a Flatpak,
and some packages have a lot of dependencies that it might be worth it to
install the Flatpak version instead.

## Package Information
- Download (HTTP): https://github.com/flatpak/flatpak/releases/download/1.14.10/flatpak-1.14.10.tar.xz
- Download md5sum: 4eb3f96ab7a73b01b408e5bb15630106
- Download Size: 1.6M
- Build Size: 106M
- Build Time: 0.5 SBU

## Package Dependencies
**NOTE: the following packages may not be in their right section.**
### Required
  [AppStream](https://linuxfromscratch.org/blfs/view/svn/general/appstream.html),
  [dbus](https://linuxfromscratch.org/blfs/view/svn/general/dbus.html),
  [elogind](https://linuxfromscratch.org/blfs/view/svn/general/elogind.html),
  [Fuse3](https://linuxfromscratch.org/blfs/view/svn/postlfs/fuse.html),
  [Glib2](https://linuxfromscratch.org/blfs/view/svn/general/glib2.html),
  [gpgme](https://linuxfromscratch.org/blfs/view/svn/postlfs/gpgme.html),
  [json-glib](https://linuxfromscratch.org/blfs/view/svn/general/json-glib.html),
  [libseccomp](https://linuxfromscratch.org/blfs/view/svn/general/libseccomp.html),
  [libsoup3](https://linuxfromscratch.org/blfs/view/svn/basicnet/libsoup3.html),
  [OSTree](./2-ostree.md),
  [p11-kit](https://linuxfromscratch.org/blfs/view/svn/postlfs/p11-kit.html), and
  [pyparsing](https://linuxfromscratch.org/blfs/view/svn/general/python-modules.html#pyparsing)

### Recommended
  [appstream-glib](https://linuxfromscratch.org/blfs/view/svn/general/appstream-glib.html),
  [Avahi](https://linuxfromscratch.org/blfs/view/svn/basicnet/avahi.html),
  [Bubblewrap](https://linuxfromscratch.org/blfs/view/svn/general/bubblewrap.html),
  [cURL](https://linuxfromscratch.org/blfs/view/svn/basicnet/curl.html),
  [DConf](https://linuxfromscratch.org/blfs/view/svn/gnome/dconf.html),
  [docbook-4.5-dtd](https://linuxfromscratch.org/blfs/view/svn/pst/docbook-4.5-dtd.html),
  [docbook-xml-4.5](https://linuxfromscratch.org/blfs/view/svn/pst/docbook.html),
  [docbook-xsl-nons](https://linuxfromscratch.org/blfs/view/svn/pst/docbook.html),
  [GTK-Doc](https://linuxfromscratch.org/blfs/view/svn/general/gtk-doc.html),
  [libarchive](https://linuxfromscratch.org/blfs/view/svn/general/libarchive.html),
  [libXau](https://linuxfromscratch.org/blfs/view/svn/x/libXau.html),
  [libxml2](https://linuxfromscratch.org/blfs/view/svn/general/libxml2.html),
  [libxslt](https://linuxfromscratch.org/blfs/view/svn/general/libxslt.html),
  [xdg-dbus-proxy](https://linuxfromscratch.org/blfs/view/svn/general/xdg-dbus-proxy.html),
  [xdg-desktop-portal](https://linuxfromscratch.org/blfs/view/svn/x/xdg-desktop-portal.html), and
  [xmlto](https://linuxfromscratch.org/blfs/view/svn/pst/xmlto.html)
  
### Optional
  [malcontent](https://gitlab.freedesktop.org/pwithnall/malcontent) (for parental features) and
  [Valgrind](https://linuxfromscratch.org/blfs/view/svn/general/valgrind.html)

## Installation of Flatpak

[//]: # (A Flatpak user seems to be unnecessary as Arch does not employ one.)

Install Flatpak by following the commands below:
```Bash
./configure --prefix=/usr     \
            --sysconfdir=/etc \
            --localstatedir=/var &&
make
```

Now as the ***root*** user:
```Bash
make install
```
