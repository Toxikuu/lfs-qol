[Home](../)

[Prev: s-nail](./7-s-nail.md) - [Next: heirloom-ex-vi](./9-ex-vi.md)

***

# Introduction to pkgsuite-ea4286
pkgsuite is a patched-up version of the Heirloom Packaging tools, which is itself a patched-up
portable version of the UNIX SVR4 packaging utilities.

## Package Information
- Download (HTTP): https://github.com/mamccollum/pkgsuite/archive/ea428661c1eb40ae7ad24d6ff449bfeda59de725.zip
- Download md5sum: 6d8e0be9b0927346bce44edd860d43c2
- Download Size: 1.5M
- Build Size: 13M
- Build Time: 0.1 SBU

## Additional Download
- Required patch: [pkgsuite-ea4286-paths.patch](./patches/pkgsuite/pkgsuite-ea4286-paths.patch)

## Package Dependencies
### Required
  [UnZip](https://www.linuxfromscratch.org/blfs/view/svn/general/unzip.html) (to unpack the distribution),
  [Which](https://www.linuxfromscratch.org/blfs/view/svn/general/which.html) and
  [heirloom-ng](./2-heirloom-ng.md) (at runtime)

## Installation of pkgsuite
Optionally, before unpacking, move the distribution zipfile to a more sensible name:
```Bash
mv ea428661c1eb40ae7ad24d6ff449bfeda59de725.zip pkgsuite-ea4286.zip
```

Apply a patch to make the installation paths conform with the others in this category:
```Bash
patch -Np1 -i ../pkgsuite-ea4286-paths.patch
```

Compile pkgsuite by following the commands below:
```Bash
cd src &&
./configure &&
make
```

Now as the ***root*** user:
```Bash
make install
```
