---
layout: post
title:  "Machinekit and EtherCAT Licensing Issues"
date:   2015-04-23 13:41:00
categories: EtherCAT
---

The [GPLv2 license][7], which binds the [Machinekit][8] and [Linux][9]
code, and the [Beckhoff EtherCAT Master license][6] that binds the
[IgH EtherCAT Master for Linux][4] are clearly incompatible. The
question remaining is whether GPL loop holes can be exploited to make
the combination possible, given the structure of the IgH
implementation and Sascha Ittner's [Machinekit EtherCAT interface][5].
I believe it can be done.

[7]: https://www.gnu.org/licenses/gpl-2.0.html
[8]: http://machinekit.io
[9]: http://en.wikipedia.org/wiki/Linux
[6]: http://www.ethercat.org/en/faq.html
[4]: http://www.etherlab.org/en/ethercat/
[5]: https://github.com/sittner/linuxcnc-ethercat

<!---more--->

This question has been raised many times before, both in public on the
[LinuxCNC forum][1], [LinuxCNC list][2] and [Machinekit list][3], as
well as in my own personal correspondence. I have spent quite some
time researching this in the past; here my findings are laid out.

[1]: http://www.linuxcnc.org/index.php/english/forum/24-hal-components/22346-ethercat-hal-driver
[2]: https://www.mail-archive.com/emc-developers@lists.sourceforge.net/msg11237.html
[3]: https://groups.google.com/d/msg/machinekit/3ADTcMTQtik/_RAtDxE4FWEJ

## The GPL and EtherCAT Master licenses are incompatible

Quoted below is part of an email I received from Gerd Hoppe, Beckhoff
'Corporate Management'. Mr. Hoppe says an EtherCAT master software
stack requires a license. The license is _free as in beer_, but not
_free as in freedom_: Mr. Hoppe points out restrictions not only that
the software must be licensed and must 'maintain compatibility', but
also that vendors must join the ETG.

**On 10/24/2013 11:56 AM, Gerd Hoppe wrote:**

> _For product /device manufacturers_

> Making, marketing and sale of a product making use of the EtherCAT
> technology requires membership in the ETG and licensing of the
> technology which comes at marginal cost for slave device licenses,
> and at no cost for master device licenses, /provided/ /however/ the
> devices or products maintain compatibility for the communication
> standard. This being said, Beckhoff makes no representation about
> code of third parties (such as, but not limited to, ISG) but only
> about the requirement of licensing the technologyfor device or
> product manufacturers. Obviously, if a product is a master
> stacksoftware, a vendor of the master stack or the master device
> does require a technology license agreement for the master product
> at no cost with Beckhoff. As such, we request master stack
> manufacturers pass this information along to users of code including
> a link to Beckhoff as licensor to the technology.

This conflicts with the GPL, which states that any additional
restrictions are prohibited. Therefore, the same piece of code cannot
be simultaneously licensed by both the GPL and EtherCAT licenses (as
IgH seems to be doing), and it is prohibited to 'combine' a software
EtherCAT implementation with GPL software in certain ways, esp. by
linking binary objects. This seems quite clear; so, is there any way
around this problem?

## Working around license restrictions

In my opinion, the software should be examined in light of the
Beckhoff license restrictions and the usual GPL loop holes to
determine what parts of the software are considered the EtherCAT
'product', and then to assess the total surface area of boundaries and
whether the means of combination is problematic. Of course the
software will have clear external boundaries, but there also may be
internal interfaces within the software where GPLv2 loop holes could
be exploited.

A widely-known GPLv2 exception is at the boundary between user/kernel
space, and the IgH EtherCAT Master for Linux includes code running on
both sides. A piece I'm familiar with, the NIC driver modifications,
live in the kernel, and wouldn't 'taint' Machinekit itself (at least
while running userland thread styles). The combination with Linux GPL
code also deserves investigation, which could possibly reveal
arguments that these NIC driver modifications aren't a proper part of
the EtherCAT 'product' anyway, and thus are not encumbered by the
Beckhoff license.

In cases where problematic code is linked, a work-around could be to
replace the interface with e.g. the HALTalk or ring buffer interface
code already in Machinekit, thus neatly side-stepping the GPL
restrictions on linking.

## Conclusion

[IANAL][10], but I do believe there's a way through this that will
limit risk and still enable users. Beckhoff granted an EtherCAT master
license for the IgH implementation, signaling they're not
fundamentally opposed to open-source EtherCAT implementations. The
Linux kernel and other open-source projects show that GPLv2 loop holes
can be successfully exploited in widely-used software.

I predict research will identify a set of boundaries to isolate
license-restricted portions of code, whether already isolated as-is
(like the NIC drivers), or else with modifications using mature
mechanisms that Machinekit already possesses. It's just a matter of
someone with enough interest deciding to take on the job. This seems
much more likely today than in the past, given the recent interest in
field bus interfaces for Machinekit, as well as the rapidly growing
community of Machinekit contributors.

[10]: http://en.wikipedia.org/wiki/IANAL
