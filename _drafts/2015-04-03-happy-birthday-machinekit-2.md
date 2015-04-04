---
layout: post
title:  "Happy Birthday Machinekit! Part 2"
date:   2015-04-03 12:00:00
categories: Machinekit
---

## A Year of Success

In just a year, [Machinekit] made enormous technical leaps, and more
important, has grown a large and high-quality community.

It's impossible to list all the technical achievements to be found in
over a thousand commits, so here are a few of the more visible ones.
The new Machinetalk API enables applications to remotely control
Machinekit. Two remote GUI applications for controlling CNC machine
tools and 3D printers demonstrate the new QtQuickVCP toolkit for
building cross-platform PC or mobile applications. Major optimizations
to the trajectory planner enable Machinekit to follow the most complex
paths close to, but not exceeding, the maximum theoretical machine
speed.  These are just a few of the major accomplishments, and ignore
those many that smaller but also important.

The community thrives, as proven by hundreds of GitHub tracker issues
filed as well as the growing list with high-powered discussion and
frequent success stories. The project enjoys major contributions and
support from industry, including [Tormach], the [BeagleBoard.org
Foundation], [The Cool Tool], and several other companies integrating
Machinekit into their products. The rapidly growing groups of CNC
machine tool and 3D printer enthusiasts represent another major
portion of contributions. All this activity earned repeat media
attention.

This is amazing progress in such a short time.  How did it happen?

## C4:  Success:  Technical and community

The feedback relationship between an open-source project's technical
success and its popularity seems obvious: a community will grow faster
around a technically-superior project, and at the same time, a project
grows technically superior with more contributors. Against the initial
intuition of many, the thinking behind the Collective Code
Construction Contract ([C4]), which the successful open-source [ØMQ]
project organizes by, is that the latter is the most important.  A
healthy community is key to an open-source project's success.

Although a Machinekit co-founder had first discovered the ØMQ
project's community process, I pushed hardest to adopt C4. Pieter
Hintjens argues persuasively for C4 in [ØMQ Guide, Chap. 6]. Moreover
it meshes with my studies of entrepreneurship, such as Geoffrey
Moore's book, __[Crossing the Chasm]__ (about marketing high tech
products in the seed stage), which says the very first 'visionaries'
to adopt a new high tech product, critical to the product's later
adoption among other groups, don't expect perfection.

The C4 goals also looked like the antidote to the stagnation we saw in
our code's legacy project. Lower hurdles to patch acceptance and a
successful contributor will become a **repeat contributor**. Automate,
distribute and streamline the work of reviewing and accepting patches
so **nobody becomes burdened or a bottleneck**. Minimize and
formalize requirements to serve in maintainer and admin roles to
enforce **community** project ownership. And when a group wants to
take things another direction, **encourage** a project fork and
support diversity in general.

From my perspective as a Machinekit Contributor, C4 has been a real
breath of fresh air. As promised, for the most part, my patches are
accepted quickly, and that encourages me to do more. The Maintainer
role also turns out to be a pleasure, since it's not difficult to
review patches, and if I'm swamped for a couple of weeks, there are
enough other Maintainers that their burden isn't greatly increased.

The growing, productive and talented Machinekit community could be a
case study for C4.  **more


[C4]: http://rfc.zeromq.org/spec:22
[ØMQ Guide, Chap. 6]: http://zguide.zeromq.org/page:chapter6
[Crossing the Chasm]: http://en.wikipedia.org/wiki/Crossing_the_Chasm

## Other project infrastructure

In my opinion, C4 is the single most important piece of project
infrastructure, but C4 and the community depend on other pieces, too.
The C4 process, based around the [pull-request] (PR) model, requires
using GitHub. We looked for tools that are like GitHub: simple,
flexible, free, transparent and cloud-based. After all, if
collaboration is easy, people will do more, and if infrastructure can
be duplicated, it's difficult to hold a project hostage.

Git is complicated, but GitHub's PR model can be as easy as clicking
buttons on a website, and is even simpler with only a single `master`
branch, as required by C4.  The light and simple GitHub issue
tracker is extra valuable with its tight repository integration.

The http://machinekit.io site is hosted on [GitHub Pages] with the
[Jekyll] static page generator (same as this one!).  Running the
website from a git repository with C4 rules *really* puts the project
in the community's hands, since not only the code but the project's
external face can be changed by anyone with minimal barriers.

We picked [Google groups] for community discussion, since the combined
forum and list offer both popular formats for post-based discussion
without splitting it into two separate channels.

Finally, my company runs the project's Buildbot CI infrastructure.
This turns out to be the exception to the 'simple, flexible, free,
transparent and cloud-based' requirements, and is also the project's
Achilles heel. I originally picked the Buildbot to be compatible with
the code base's legacy project infrastructure. It took way, way too
much time to set up, and because Machinekit is especially difficult to
compile and test on three host architectures and in five real-time
thread environments, it's not easy to fix. While it does give me an
elevated sense of importance to have the project depend on me, it's
also a maintenance nuisance that I'm pretty burnt out on, and a system
disaster several months back left the project hanging for days while I
scrambled to bring service back online. At this point, I've been
working with a few others to identify and test replacement
infrastructure that satisfies the above requirements, and I hope it
can be distributed as well. Keep an eye for articles on this site
about that.


## I'm so proud!


- Started successful project
  - First time
  - Feels like magic
- Built community infra myself
  - ...but it depends on me less and less
- Doing good for humanity

