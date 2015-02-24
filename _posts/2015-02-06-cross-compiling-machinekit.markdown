---
layout: post
title:  "Cross-compiling Machinekit"
date:   2015-02-06 16:20:00
categories: machinekit build
---

## The problem

[Machinekit], the open-source machine controller, is ported not
only to x86 but also ARM architecture, and members of the community
distribute packages for Beaglebone and Raspberry Pi boards.

The [Dovetail Automata Buildbot] serves as the de-facto CI
system for the project, and builds the Debian and Ubuntu packages
that most of the community use.  The Buildbot builds for and tests on
several real-time threads systems each on x86_64, i686 and armv7hl
architectures.  Needless to say, this system is complex, and even with
16 x86 cores and five ARM cores dedicated to building, it takes 45
minutes to build and test each RT thread system on each CPU
architecture.

<!---more--->

The ARM builds take over twenty minutes to build packages natively on
a four core armv7hl Wandboard with 2GB RAM, compared with six minutes
for x86 builds. Building for ARM with qemu emulation on x86 takes even
longer, even with 16 cores.

Furthermore, as of now, there are no ARM-architecture cloud services
that the heavier Buildbot jobs may be offloaded to.  [AWS
nixed] their ARM cloud plans, and other offerings like
the [Online Labs ARM cloud] are not yet
available.

[Machinekit]: http://machinekit.io
[Dovetail Automata Buildbot]: http://buildbot.dovetail-automata.com
[AWS nixed]: http://www.businesscloudnews.com/2014/11/18/aws-opts-for-custom-intel-over-arm-silicon/
[Online Labs ARM cloud]: http://techcrunch.com/2014/11/13/online-labs-designed-its-own-arm-servers-to-take-on-aws-digitalocean/


## The solution:  cross compiling

An x86 cross ARM build solves these problems.

A cross build takes about the same time as a native build.  That takes
over 15 minutes off the build time.

Building for ARM on x86 allows builds on x86 cloud infra.  [Already
proven][gh-z-mk-docker] with Docker.

Also, cross building opens up possibilities for porting Machinekit to
build for embedded systems where native compilation isn't an option
because of hardware limitations.


## Cross build environment

Setting up a cross build environment is not always easy, but cross
building Machinekit for ARM is much easier now thanks to progress in
Debian.  First, the Linaro `arm-linux-gnueabihf` tool chain ships in Debian
for the first time in Jessie (currently in testing) and Trusty, so
there's no need to find a tool chain outside the distro.  Second,
with Debian's `Multi-Arch` packages, introduced in Wheezy, 'foreign
architecture' library and `-dev` packages may be installed in the OS
filesystem right next to native packages.  With these changes, cross
building is as easy as `./configure --host=arm-linux-gnueabihf`.
Almost!

It can still be a challenge to install the correct packages
automatically.  One problem is that `Multi-Arch` support still isn't
complete.  For example, some tools like Cython that Machinekit must
run during build time are missing the 'Multi-Arch: foreign' tag in the
package, which means that the cross build should depend on the build
architecture package, not the host architecture package (the default).
As a result, even when `mk-build-deps` installs the correct packages
for a native build, be careful running `mk-build-deps -a armhf`
or you may find Apt uninstalling basic native architecture packages
like `gcc`, and a long list of dependent packages with it, and your
build environment will be in shambles.

Docker is an easy way to set up an isolated cross build environment.
[Gemi Orcullo][gh-kinsamanka], who contributes Machinekit packages for
Raspberry Pi, gave me an example `Dockerfile` for a native build of
Machinekit on x86 architecture.  This was the basis for [my
branch][gh-z-mk-docker] that I used for developing the cross build in
a Docker container.  To run it on a system with the `docker.io`
package installed, check out the branch and run the following:

   docker/build-image.sh -v -b -u trusty-armhf-cross

[gh-kinsamanka]: https://github.com/kinsamanka/


- [Gemi][gh-kinsamanka] helped
- Don't try this on your running system
  - Pkg dep hell will break your dev env
  - Docker [gh-z-mk-docker]
- How to run



[gh-mk-mk-pr477]: https://github.com/machinekit/machinekit/pull/477
[gh-mk-mk-iss479]: https://github.com/machinekit/machinekit/issues/479
[gh-z-mk-docker]: https://github.com/zultron/machinekit/tree/docker

## Issues

- Standardizing to distro
  - `m4` macros
    - NIH stuff breaks when put in other environment
  - `pkg-config` macros
    - hand-written stuff is too verbose
    - NIH stuff breaks

### Packages
- `Multi-Arch`
  - https://wiki.debian.org/Multiarch/CrossDependencies
  - https://wiki.debian.org/Multiarch/HOWTO
- `architecture.mk`
- clean up build-deps
  - run-time deps in build-deps
- fix my packages

### Autoconf
- `AC_TRY_RUN`
  - http://czmq.zeromq.org/manual:zsys
- Build arch vs. host arch
  - `AC_CANONICAL_*` actually not needed
  - `CC_FOR_BUILD`
    - `pasm`
  - `objcopy` and `ld`
    - wacky; not normally needed
- Broken `m4` macros
  - `autoreconf`
    - don't use `m4_include`; put in `autoreconf`
  - `tcl`, `pkg-config` distro-supplied macros
    - Wheezy's `tcl` macros broken; [bug #777085][debian-77085]
- CZMQ curve checks

### Other

- `PRELOAD_WORKAROUND` stuff breaks

# Next

http://www.vtk.org/Wiki/CMake_Cross_Compiling

# Organize_me_please

https://www.gnu.org/software/autoconf/manual/autoconf-2.69/html_node/Canonicalizing.html
http://www.gnu.org/software/automake/manual/html_node/Cross_002dCompilation.html
https://autotools.io/pkgconfig/pkg_check_modules.html



[debian-77085]:
https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=777085
