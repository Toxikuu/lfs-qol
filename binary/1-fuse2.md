# Introduction to Fuse2
FUSE, or Filesystem in Userspace, allows userspace programs to create virtual
filesystems. This is a really helpful technology, and the current Fuse version
is major version 3. Fuse2 on the otherhand is still used by AppImages which
rely on this technology. You may extract AppImages as you wish which would
bypass this requirement, but other people opt to just install Fuse2 and run the
AppImages directly.

## Package Information
- Download (HTTP): https://github.com/libfuse/libfuse/releases/download/fuse-2.9.9/fuse-2.9.9.tar.gz
- Download md5sum: 8000410aadc9231fd48495f7642f3312
- Download Size: 1.8M
- Build Size: 17M
- Build Time: 0.1 SBU

## Additional Download
- Required patch: https://gitlab.archlinux.org/archlinux/packaging/packages/fuse2/-/raw/main/conditionally-define-closefrom.patch

## Kernel Configuration
Enable the following options in the kernel and recompile if necessary:
```
File systems --->
  <*/M> FUSE (Filesystem in Userspace) support                         [FUSE_FS]
```

It would also be a good idea to enable the following options as well, once
again recompile the kernel if necessary:
```
File systems --->
  <*/M> FUSE (Filesystem in Userspace) support                         [FUSE_FS]
  <*/M>   Character device in Userspace support                           [CUSE]
```

## Installation of Fuse2
First apply a patch to fix compatibility with glibc-2.34 and up and regenerate
the `configure` script:
```Bash
patch -Np1 -i ../conditionally-define-closefrom.patch &&
autoreconf -i
```

Now install Fuse2 by following the commands below:
```Bash
./configure --prefix=/usr --disable-static \
            INIT_D_PATH=/tmp/init.d &&

make
```

Now as the ***root*** user:
```Bash
make install &&

rm -rf  /tmp/init.d &&

install -v -m755 -d /usr/share/doc/fuse-2.9.9 &&
install -v -m644    doc/{how-fuse-works,kernel.txt} \
                    /usr/share/doc/fuse-2.9.9
```

## Configuring Fuse2
Some options regarding mount policy can be set in the file `/etc/fuse.conf`.
To install the file run the following command as the ***root*** user:
```Bash
cat > /etc/fuse.conf << "EOF"
# Set the maximum number of FUSE mounts allowed to non-root users.
# The default is 1000.
#
#mount_max = 1000

# Allow non-root users to specify the 'allow_other' or 'allow_root'
# mount options.
#
#user_allow_other
EOF
```
