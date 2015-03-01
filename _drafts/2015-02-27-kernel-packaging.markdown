Smallish rant: Kernels are really hard to package.  It's pretty
frustrating that there are so many disparate methods of doing so, even
within the same distro.  Both RedHat and Debian official kernel
packaging provide ways to customize, but both are very limited.  I
spent a lot of time writing generic hooks for the Debian package to
make it easier to build more challenging variants like Xenomai and
RTAI, but that work is made less valuable because the packaging is so
complex in general.  The Debian make-kpkg stuff is absolutely hideous
for lots of reasons, but folks still use it.  I don't know much about
RCN's stuff, but in general he likes to write custom scripts that are
only useful for his system, and like jeplerware, require a lot of work
to teach it a new trick.  The worst thing is we can't seem to get on
the same page about this, so we have a whole slew of ways to build
kernels that are all poor, and