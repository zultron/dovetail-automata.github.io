---
layout: post
title:  "What is Machinekit?"
date:   2015-02-07
categories: machinekit
---

**Moves.  Controls.  Things.**

This is the promise of [Machinekit], the flexible, portable,
industrial class, open-source machine control framework.

Dovetail Automata LLC invests heavily in Machinekit development
because we think Machinekit will be disruptive in the machine
controller market.

At present, there are several companies investing in Machinekit.
Machinekit ships on at least one CNC controller, with another in the
pipeline.  Machinekit technology is used
- retrofit big iron
- new, small CNC mills and lathes

Hobbyists use it for CNC mills and lathes, and 3D printers





# Functions #

It suits projects requiring any of the following:

- Hardware interface drivers, including SoC GPIO pins, FPGA-based I/O,
  field buses
- Coordinated joint motion
- Integration into applications (GUIs, monitors, etc.) through remote
  control APIs

# Portable #

Machinekit is portable.  It runs in several real-time thread
environments, CPU architectures and embedded/non-embedded platforms,
and GNU/Linux distributions, and drives many hardware I/O interfaces.

## Real-time thread environments ##

Machinekit runs in the Xenomai, RT_PREEMPT and RTAI RT
thread systems, and POSIX non-RT threads.  New RT environments easily
integrate through a simple API.

## CPU architectures and hardware platforms ##

Machinekit runs on x86 and ARM CPU architectures, and the project
specially targets the PC, Beaglebone and Raspberry Pi platforms.
Easily port to new systems, including cross-compiling for embedded
devices.

## Hardware I/O interfaces ##

Machinekit drives any hardware, and includes many drivers for
e.g. GPIO pins, FPGA-based I/O controllers and field buses.

# Community and project #

The active Machinekit community grows at an explosive rate.  We
attribute this greatly to the project's repeated success stories and
perfect positioning in the Maker Revolution.

Even more important is the community itself.  New users find
themselves welcomed with enthusiastic support for getting started.

Contributors quickly become owners in the project, which follows the
[C4] process for accepting contributions.  C4, based on the GitHub
pull request model, minimizes hurdles by distributing, automating and
simplifying review tasks.  When contributions are accepted through a
simple, predictable and fast process, we find contributors tend to
come back.

# Project infrastructure #

The project relies on public or distributed infrastructure wherever
possible.  Developers collaborate on the project's GitHub
[code repository] and [issue tracker], and the project
[website][Machinekit] lives on GitHub pages.  The [Google group] gives
community members the choice between email list and forum interfaces
to the same discussion.  Any community member may volunteer to
distribute [packages].

An exception is the [CI system], contributed by Dovetail Automata LLC,
which ensures the C4 process requirement that contributed patches must
build and pass tests for targeted platforms.  This system builds
Machinekit on `x86_64`, `i686` and `armv7hl` architectures, and runs
tests on each possible combination of architecture and Xenomai,
RT_PREEMPT, RTAI and POSIX thread systems.  Building and testing for
all of these combinations is complex, so while we seek a solution for
distributing the test functions, the Dovetail Automata CI system fills
that need in the interim.



[Machinekit]: http://machinekit.io
[C4]: http://rfc.zeromq.org/spec:22
[code repository]: https://github.com/machinekit/machinekit/
[issue tracker]: https://github.com/machinekit/machinekit/issues
[Google group]: http://groups.google.com/group/machinekit
[CI system]: http://buildbot.dovetail-automata.com/grid
[packages]: http://www.machinekit.io/docs/packages-debian/
