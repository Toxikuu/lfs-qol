[Home](../)

[Next: heirloom-ng](./2-heirloom-ng.md)

***

# A note on paths, or a quick history lesson

The packages in this category are installed to various non-standard locations
inside /usr. The purpose behind this is to be more accurate to where UNIXen from
where these tools were ported put said files, and an explanation of where said paths
came from is provided below.

- /bin and /usr/bin/ — the traditional, pre-dating formal standardization, general toolsets; 
from a post-formal-standardization viewpoint, commands that conform to the System V Interface 
Definition and the X/Open Portability Guide version 3 (or, in Linux's case, standard Linux tools)
- /usr/ucb/ — UCB (i.e. BSD) compatibility directory with BSD-compatible tools
- /5bin and /usr/5bin/ — System V (i.e. 5) compatibility directory with AT&T Unix System 5 compatible
tools
- /usr/ccs/bin — various developer tools
- /usr/sadm/bin - pkgadd internal tooling

The rest of the non-standard folders' meanings can be easily deduced from basic Linux knowledge and the
above.

If you want to know more about old UNIXen' path conventions, and are willing to fall down a rabbit hole
of 80s-90s UNIX variants, DEC equipment and various other old UNIX conventions, old hardware and everyday 
jobs of UNIX sysops of the 90s, a much more comprehensive guide can be found on [here](https://unix.stackexchange.com/a/448799/5132).

# A note on Linux, UNIX SVR4 and BSD

It is also of note that Linux tools are much closer in UI and parameters to their BSD counterparts than
their SVR4 ones. If you want to use tools from this category on a daily basis and you're not familiar
with UNIX SVR4, you might first need to learn how SVR4 tools work.
