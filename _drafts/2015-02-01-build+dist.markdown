- 5 systems 


- Build + deploy parts:

  - Build pkgs
    - Can build point at other 3rd-party repos?
  - Run tests
  - Build package repo
    - Signatures?
  - Put repo online
  - Coordinate all of above
    - Automated dependency checking and rebuild?
    - Test result reporting on issue tracker
    - Log gathering

- Coordination:

  - Can coordinate many sources, e.g. OBS + resin.io?
  - Snapshots of each build on Docker!
    - Get THEM to save history



- Features:


- Systems tested
Some of below may depend on future distro releases

  - Buildbot
    - Hardest
  - RCN
  - OBS + Buildbot
    - Ugly; still needs #5 on private infra
  - COPR and Koji
  - Docker servers, proot, cheating
  - Docker, local, proot
  - Docker, local, binfmt-misc
  - Resin.io
    - C4 Stabilization Branch
  - Cross-compile

- Future systems
  - Distributed/federated Buildbot
  - Amazon
  - VPS

- Follow up article:
  - Machinekit's portability in so many dimensions


- Metrics
  - Buildbot build counts accelerating, disk fills
  - Web stats?  Downloads?

- Infrastructure overview
  - From Madison

- Opportunities

  - Docker & Resin guys:  CI infra
    - Docker's orchestration services
    - Open up APIs and build results
    - Project's builds visibile to community
    - GitHub revenue model:  pay for proprietary builds
  - Pressure OBS to do better with Debian
  - If I can connect everybody for a single monitoring of builds,
    - I can have some leverage
  - Ben:  Orchestrated infrastructure
    - Docker runs on Windows
  - Build Tormach's code
  - Xenomai build+unit-test resin.io container
  - Real hardware unit tests


- Disruptive
  - End of patents
    - Big companies simply can't keep up
    - Communication and collaboration so easy, patents are obsolete
  - Maxes access to educational resources
    - Most level playing field online


- Machinekit infra
  - Self-maintaining
  - 