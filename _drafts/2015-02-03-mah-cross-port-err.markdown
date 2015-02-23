
Canadian Cross build
x86_64 cross ARM EABI


```
root@3f6f68866cb6:/usr/src/machinekit/src# ./autogen.sh && CC=arm-linux-gnueabihf-gcc-4.8 CXX=arm-linux-gnueabihf-g++-4.8 ./configure --with-platform-beaglebone --host=arm-linux-gnueabihf --with-xenomai --disable-gtk --without-libusb-1.0
 --host=arm-linux-gnueabihf --with-xenomai --disable-gtk --without-libusb-1.0
checking if cython is usable... checking for cython... no
rebuilding Cython bindings will require installing cython - not normally required
checking build toplevel... /usr/src/machinekit
checking installation prefix... run in place
checking for grep... /bin/grep
checking for egrep... /bin/egrep
checking for arch... /usr/bin/arch
checking for arm-linux-gnueabihf-gcc... arm-linux-gnueabihf-gcc-4.8
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... yes
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether arm-linux-gnueabihf-gcc-4.8 accepts -g... yes
checking for arm-linux-gnueabihf-gcc-4.8 option to accept ISO C89... none needed
checking how to run the C preprocessor... arm-linux-gnueabihf-gcc-4.8 -E
checking build system type... x86_64-unknown-linux-gnu
checking host system type... arm-unknown-linux-gnueabihf
checking for arm-linux-gnueabihf-pkg-config... /usr/bin/arm-linux-gnueabihf-pkg-config
checking platform-pc... disabled for this architecture
checking platform-beaglebone... enabled on command line
checking platform-raspberry... disabled for this architecture
checking for uuidgen... /usr/bin/uuidgen
setting unique Machinekit UUID to b2adeab7-080b-4b44-bc56-117897f29d8e
checking whether to enable remote operation... local operation on IPC sockets only, zeroconf not used
checking which directory to use for IPC sockets and other transient files... using /tmp for IPC sockets and other transient files
checking whether to build programming examples... not building example programs
checking for proto2js... none
checking whether to build protobuf Javascript bindings... not protobuf Javascript bindings
checking whether to use the common shared memory driver... default is no
checking whether to use inb/outb or ppdev ioctl on the x86 for parport I/O... using defaults: no
checking whether to build the emcweb interface... not building the emcweb interface
checking whether to build unstable development code... not building  development code
checking for arm-linux-gnueabihf-pkg-config... (cached) /usr/bin/arm-linux-gnueabihf-pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for CZMQ... yes
checking for PROTOBUF... yes
checking for protoc... /usr/bin/protoc
checking python module: google.protobuf.descriptor... yes
checking python module: google.protobuf.descriptor_pb2... yes
checking python module: google.protobuf.compiler.plugin_pb2... yes
checking for JANSSON... yes
checking for URIPARSER... yes
checking for LWS... yes
checking for SSL... yes
checking for UUID... yes
checking for AVAHI... yes
checking whether to enable NML-using parts... not building non-essential NML-using parts
checking python module: pyftpdlib.authorizers... yes
checking python module: pyftpdlib.handlers... yes
checking python module: pyftpdlib.servers... yes
checking whether to build POSIX threads... no
checking whether to build RT_PREEMPT threads... no
checking for xeno-config... /usr/bin/xeno-config
checking usability of xenomai utility, /usr/bin/xeno-config... yes
checking Xenomai runtime library... works
checking whether to build Xenomai userland threads... yes
checking whether to build Xenomai kernel threads... no
checking whether to build RTAI threads... no
checking whether to build hardware drivers... yes
checking for libudev... not found
checking whether to build usermode PCI hardware drivers... no; depends on libudev
fatal: Not a git repository (or any of the parent directories): .git
fatal: Not a git repository (or any of the parent directories): .git
no annotated tags found, not even unsigned
fatal: Not a git repository (or any of the parent directories): .git
fatal: Not a git repository (or any of the parent directories): .git
checking for usability of rdtscll from asm/msr.h... no
checking for usability of linux/hidraw.h... yes
checking for libmodbus3... not found; disabling
checking for glib... configure: error: no -- required until somebody makes glib optional
root@3f6f68866cb6:/usr/src/machinekit/src# 
```
