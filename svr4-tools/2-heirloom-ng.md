# Introduction to heirloom-ng-59f7cc
Heirloom-ng is a collection of standard Unix utilities that is intended to provide maximum compatibility
with traditional Unix while incorporating additional features necessary today.

## Package Information
- Download (HTTP): https://github.com/Projeto-Pindorama/heirloom-ng/archive/59f7cc870f72adc4a2df8a64acc75ab425d8ff6b.zip
- Download md5sum: c5102f8a7666eb6eebb613945c0790f0
- Download Size: 1.5M
- Build Size: 23M
- Build Time: 0.3 SBU

## Additional Download
- Required patch: [heirloom-ng-59f7cc-no-static.patch](./patches/heirloom-ng/heirloom-ng-59f7cc-no-static.patch)
- Required patch: [heirloom-ng-59f7cc-fix-libcommon-build.patch](./patches/heirloom-ng/heirloom-ng-59f7cc-fix-libcommon-build.patch)
- Required patch: [heirloom-ng-59f7cc-fix-chroot-build.patch](./patches/heirloom-ng/heirloom-ng-59f7cc-fix-chroot-build.patch)
- Required patch: [heirloom-ng-59f7cc-fix-date-build.patch](./patches/heirloom-ng/heirloom-ng-59f7cc-fix-date-build.patch)
- Required patch: [heirloom-ng-59f7cc-fix-shl-build.patch](./patches/heirloom-ng/heirloom-ng-59f7cc-fix-shl-build.patch)
- Required patch: [heirloom-ng-59f7cc-dont-link-nonexistent-files.patch](./patches/heirloom-ng/heirloom-ng-59f7cc-dont-link-nonexistent-files.patch)

## Package Dependencies
### Required
  [UnZip](https://www.linuxfromscratch.org/blfs/view/svn/general/unzip.html) (to unpack the distribution), and
  [ed](https://www.linuxfromscratch.org/blfs/view/svn/postlfs/ed.html)

## Installation of heirloom-ng
Optionally, before unpacking, move the distribution zipfile to a more sensible name:
```Bash
mv 59f7cc870f72adc4a2df8a64acc75ab425d8ff6b.zip heirloom-ng-59f7cc.zip
```

Apply a patch to avoid usage of static libraries:
```Bash
patch -Np1 -i ../heirloom-ng-59f7cc-no-static.patch
```

Now, apply patches to fix builds of various components:
```Bash
patch -Np1 -i ../heirloom-ng-59f7cc-fix-libcommon-build.patch &&
patch -Np1 -i ../heirloom-ng-59f7cc-fix-chroot-build.patch &&
patch -Np1 -i ../heirloom-ng-59f7cc-fix-date-build.patch &&
patch -Np1 -i ../heirloom-ng-59f7cc-fix-shl-build.patch
```

Finally, apply a patch to avoid a failure during installation:
```Bash
patch -Np1 -i ../heirloom-ng-59f7cc-dont-link-nonexistent-files.patch
```

Compile heirloom-ng by following the commands below:
```Bash
make -j1
```

Now as the ***root*** user:
```Bash
make -j1 install
```
