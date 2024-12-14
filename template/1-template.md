[Home](../)

[Prev: PREV-PKG](./0-prev-pkg.md) - [Next: NEXT-PKG](./2-next-pkg.md)

***

# Introduction to Package-$PACKAGE-VERSION
Explain what Package does and why the user may want or need it.

## Package Information
Note: "Package" does not change to the actual package name, it should always
stay "Package"
- Download (HTTP): https://test.com/tarball-1.0.0.tar.gz
- Download md5sum: 00000000000000000000000000000000
- Download Size: 1.0M
- Build Size: 100M
- Build Time: 1.5 SBU

## Additional Download
- Required patch: https://test.com/tarball-1.0.0-fix-behavior.patch

## Package Dependencies
### Required
  [Fuse2](../binary/1-fuse2.md) (For userspace stuff),
  [git](https://linuxfromscratch.org/blfs/view/svn/general/git.html) (for tests), and
  [NSS](https://linuxfromscratch.org/blfs/view/svn/postlfs/nss.html)

### Recommended
  [Lua](https://linuxfromscratch.org/blfs/view/svn/general/lua.html) (for running lua scripts)

### Optional
  [LLVM](https://linuxfromscratch.org/blfs/view/svn/general/llvm.html) (with Clang)

## Kernel Configuration
Enable the following options in the kernel and recompile if necessary:
```
Kernel options here:
```

## Installation of Package
This package requires an extra user. Go ahead and add it:
```Bash
useradd ...
```

Apply a patch to fix behavior:
```Bash
patch -Np1 -i ../tarball-1.0.0-fix-behavior.patch
```

Now install Package by following the commands below:
```Bash
./configure --prefix=/usr --disable-static &&
make
```

Now as the ***root*** user:
```Bash
make install
```

## Command Explanations
  `--disable-static`: This parameter disables building unnecessary static
  libraries. Note that this explantion is here for the sake of being an
  example, but in real practice is unnecessary. This should be handled case by
  case basis, to decide if an instruction, flag, or parameter should be
  explained.

  `make install`: This command installs the package. Again, this explanation is
  not necessary and here for the sake of an example.

## Configuring Package
Add the following `/etc/package.conf` file:
```Bash
cat > /etc/package.conf << "EOF"
# Set this option to true
option = true
EOF
```
