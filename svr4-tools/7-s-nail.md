# Introduction to nail-14.9.25
s-nail is a mail user agent derived from Berkeley Mail 8.1.

## Package Information
- Download (HTTP): https://ftp.sdaoden.eu/s-nail-14.9.25.tar.xz
- Download md5sum: 59d5818c54246d22f8ff599b8783250d
- Download Size: 788K
- Build Size: 7.7M
- Build Time: 0.2 SBU

## Package Dependencies
### Required
  [An MTA](https://www.linuxfromscratch.org/blfs/view/svn/server/mail.html) (at runtime)

### Optional
  [MIT Kerberos](https://www.linuxfromscratch.org/blfs/view/svn/postlfs/mitkrb.html) and
  [Apache SpamAssassin](https://spamassassin.apache.org)

## Installation of s-nail
First, configure s-nail by executing the commands below:
```Bash
VAL_BINDIR=/usr/5bin VAL_LIBEXECDIR=/usr/5lib VAL_MANDIR=/usr/share/man/5man VAL_SYSCONFDIR=/etc make config
```

Now, compile s-nail by following the commands below:
```Bash
make
```

Now as the ***root*** user:
```Bash
make install
```

Optionally, make a few compatibility symlinks as the ***root*** user:
```Bash
install -v -m755 -d /usr/ucb &&
ln -svf /usr/5bin/s-nail /usr/5bin/mailx &&
ln -svf /usr/5bin/s-nail /usr/ucb/Mail &&
ln -svf /usr/5bin/s-nail /usr/ucb/mail
```

## Command Explanations
   ``VAL_MTA=/usr/bin/sendmail`` - Set the path to an MTA.

   ``VAL_MTA_ARGV0=sendmail`` - This variable is used for mailwrapper(8) compatibility. Mailwrapper is
   a wrapper program that can be installed as sendmail which will automatically redirect queries to the
   installed sendmail-compatible MTA.
