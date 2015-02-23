---
layout: post
title:  "Welcome to Dovetail Automata!"
date:   2015-01-27 20:40:00
categories: jekyll update
---

- 3D printers are clearly on track to be easy to use as a regular
  printer

- Android client for 3D printers; why are regular printers so behind?

- Yocto:  is that my market?  3D printer retrofits

- Packaging in many distros

- Cloud infra
  - Docker + resin.io
  - OBS has poor support of Debian + Ubuntu; no Debian ARM (yet)
  - Koji limited to RPM & distro packages
  - Copr limited to RPM & x86 arch

- PC Distros
  - Debian
    - PC fave, esp. in Maker circles
    - Fuck all for public build infra; OBS barely counts
  - Ubuntu by extension
    - Support
    - Launchpad cloud build infra
  - Fedora and EPEL
    - 3D printer spin?
    - Maybe FreeCAD is being sponsored?
    - Copr has no ARM arch, still, despite Fedora and RHEL ARM distros
    - But few packages
      - I get credit for FreeCAD and PyCAM
  - OpenSUSE has ARM distros
    - CAD packages?

- Embedded distros
  - Docker
    - resin.io public build infra!
    - Containers for Buildbots:  distributed tests
    - Deployment tools

- resin.io

  - This is exactly what I've been trying to say! [From their
    site][what_is_resin_io]:

    [Setting up a CI infra and deployment system [as I've done]]
    manually involves setting up an operating system, establishing a
    secure local network, configuring some means of recording and
    viewing logs, and providing some means of shipping new versions of
    code to devices in the field, amongst other equally vexing tasks.

  - resin.io layers:
    - On the [what's inside][what_in_resion_io] page
    - Yocto
      - Docker
        - 

[what_is_resin_io]: http://docs.resin.io/#/pages/about.md#what-is-resin-io-
[what_in_resion_io]: http://docs.resin.io/#/pages/inside.md

- Docker

  - 

[what_is_docker]: https://www.docker.com/whatisdocker/

  
- Social media

  - Blogs weekly
    - this shit above is exciting
  - Promote self on FB, Twitter, LinkedIn, Google+
  - Core competency:  writing; can I get myself to blog?
  - Everything I do is of interest to some circle.




A little more plugging:  Machinekit is powerful embedded machine control software, and the hardware integrator's dream.  It runs under Linux on a variety of ARM and x86 hardware, with well-supported Beaglebone and RPi OS images.  Drivers for GPIO pins, FPGA cards, field buses, and many other h/w interfaces appear as 'components' with 'pins' that can be 'wired' together, either with simple net-list-like configuration files or programmatically.  It includes 100+ software components out of the box, from simple logic gates to quadrature decoders and a CNC motion controller.  

connects your app, running on any platform anywhere, to your hardware electronics, like sensors and steppers.  One of our founders who ported Machinekit to Beaglebone has attracted dozens of 3D printer enthusiasts to the project with the RAMPS-like Beaglebone cape 'CRAMPS' that he designed.  Machinekit's 

Machinekit is powerful, open-source embedded machine control software, and both the hardware integrator's and the app developer's dream.  Even though the project is young, we have a large and growing community, and several commercial backers.  3D printer enthusiasts see Machinekit as freedom from Arduino hardware limitations, and CNC machine tool integrators see it as an attractive alternative to FANUC.  It seems like folks here should be interested.




You'll find this post in your `_posts` directory - edit this post and re-build (or run with the `-w` switch) to see your changes!
To add new posts, simply add a file in the `_posts` directory that follows the convention: YYYY-MM-DD-name-of-post.ext.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll's GitHub repo][jekyll-gh].

[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
