[Home](../)

[Prev: xhomer](./2-xhomer.md) - [Next: s4-3b1-pc7300](./4-s4-3b1-pc7300.md)

***

# Introduction to freebee-b72776
FreeBee is an AT&T 3B1/7300 UNIX PC emulator.

## Package Information
- Download (HTTP): https://github.com/philpem/freebee/archive/b727767d2ac48b86f984bf816dfbad9ece94776f.zip
- Download md5sum: e4eb3cc9c475a2ddaa5945f5dd3ea992
- Download Size: 120K
- Build Size: 4.5M
- Build Time: less than 0.1 SBU

## Additional Download
- Required submodule: https://github.com/kstenerud/Musashi/archive/fc7a6fc602e2fbcd24851670a5242358765feacf.zip
- Required submodule md5sum: d49057c107f7fe78462ad6929a1844e8
- Required ROMs: http://bitsavers.org/pdf/att/3b1/firmware/3b1_roms.zip
- Required ROMs md5sum: 16db01b7106736cbdc4c97e22f816e7f
- Recommended patch: [freebee-b72776-system-roms.patch](./patches/freebee/freebee-b72776-system-roms.patch)

## Package Dependencies
### Required
  [UnZip](https://www.linuxfromscratch.org/blfs/view/svn/general/unzip.html) (to unpack the distribution) and
  [SDL2](https://www.linuxfromscratch.org/blfs/view/svn/multimedia/sdl2.html)

## Installation of freebee
Optionally, before unpacking, move the distribution zipfiles to a more sensible name:
```Bash
mv b727767d2ac48b86f984bf816dfbad9ece94776f.zip freebee-b72776.zip &&
mv fc7a6fc602e2fbcd24851670a5242358765feacf.zip musashi-fc7a6f.zip
```

Unpack the musashi submodule into the right place:
```
unzip ../musashi-fc7a6f.zip -d src/ &&
rmdir src/musashi &&
mv src/Musashi-fc7a6fc602e2fbcd24851670a5242358765feacf src/musashi
```

It is of note that, during extraction of the musashi submodule, you may get the following error message:
```
lchmod (file attributes) error: Operation not supported
```
You may ignore said error message, everything is fine. The error message is being caused by an attempt
to set the file attributes on a symbolic link, which are ignored on most Unix and Unix-like systems, a
notable exception being macOS.

Optionally, apply a patch to set the default ROM search path to a system-wide location and not the
current directory:
```Bash
patch -Np1 -i ../freebee-b72776-system-roms.patch
```

Compile freebee by following the commands below:
```Bash
make src/musashi/m68kops.h &&
make &&
make -C tools
```

Now as the ***root*** user:
```Bash
install -v -Dm755 freebee /usr/bin/freebee &&
install -v -Dm755 tools/makehdimg /usr/bin/makehdimg &&
install -v -m644 freebee.1 /usr/share/man/man1 &&
install -v -m644 tools/makehdimg.1 /usr/share/man/man1
```

Optionally, install the documentation:
```Bash
install -v -m755 -d /usr/share/doc/freebee-b72776 &&
install -v -m644 README.md /usr/share/doc/freebee-b72776 &&
install -v -m644 README.serial.md /usr/share/doc/freebee-b72776 &&
install -v -m644 sample.freebee.toml /usr/share/doc/freebee-b72776 &&
install -v -m644 doc/3B1\ Memory\ Map.ods /usr/share/doc/freebee-b72776
```

If you have applied the systemwide ROMs patch, install those ROMs as the ***root*** user:
```Bash
install -v -m755 -d /usr/share/freebee/roms &&
unzip ../3b1_roms.zip -d /usr/share/freebee/roms &&
rm -vf /usr/share/freebee/roms/*.hex &&
rm -vf /usr/share/freebee/roms/README &&
mv -v /usr/share/freebee/roms/14C\ 72-00616.bin /usr/share/freebee/roms/14c.bin &&
mv -v /usr/share/freebee/roms/15C\ 72-00617.bin /usr/share/freebee/roms/15c.bin
```

## Command Explanations
   ``make src/musashi/m68kops.h`` - explicitly generate a header file used during 
   build time to avoid a race condition.

## Configuring FreeBee
If you have not applied the systemwide ROMs patch, you will have to put the roms/ folder
as documented in the README into every folder you run FreeBee from, although it is possible
to explicitly set the ROM path in the FreeBee config file if you do not want to do that.

FreeBee can be configured via the file ``.freebee.toml``. It is of note that the only search
paths for this file are the current directory and your home folder. If you want to learn how
to configure said file, refer to the ``sample.freebee.toml`` file in the source distribution
or, if you installed the documentation, it is also available in the documentation folder.
