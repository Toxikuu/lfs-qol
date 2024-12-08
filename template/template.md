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

## Configuring Package
Add the following `/etc/package.conf` file:
```Bash
cat > /etc/package.conf << "EOF"
# Set this option to true
option = true
EOF
```
