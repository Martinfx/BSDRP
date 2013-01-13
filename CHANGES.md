# Release 1.3 (not released)

## New features
* sparc64 support almost complete (just the upgrade script to fix)
* None: It's a bug-fixes-only release.

## Bug fixes
* Add the missing ipfw_nat module
* Netmap fixes by sync code with -current but only for em(4) and re(4) nic, not ixgbe(4)

## Installed packages
Sames as in release 1.2:
* NetPIPE-3.7.1                  A self-scaling network benchmark
* bird-1.3.8                     Dynamic IP routing daemon (IPv4 version)
* bird6-1.3.8                    Dynamic IP routing daemon (IPv6 version)
* dlmalloc-2.8.4                 Small, fast malloc library by Doug Lea
* fprobe-1.1_1                   Tool that collects network traffic data
* freevrrpd-1.1                  This a VRRP RFC2338 Compliant implementation under FreeBSD
* iperf-2.0.5                    A tool to measure maximum TCP and UDP bandwidth
* ipfw-user-0.1                  Netmap-enabled IPFW userspace version
* ipmitool-1.8.12_1              CLI to manage IPMI systems
* ipsec-tools-0.8.0_3            KAME racoon IKE daemon, ipsec-tools version
* isc-dhcp42-relay-4.2.4         The ISC Dynamic Host Configuration Protocol relay
* isc-dhcp42-server-4.2.4_2      The ISC Dynamic Host Configuration Protocol server
* libevent-1.4.14b_2             Provides an API to execute callback functions on certain events
* libgcrypt-1.5.0_1              General purpose crypto library based on code used in GnuPG
* libgpg-error-1.10              Common error values for all GnuPG components
* mcast-tools-20061214_1         IPv6 multicast routing daemons and tools
* mpd-5.6                        Multi-link PPP daemon based on netgraph(4)
* mrouted-3.9.6                  Multicast routing daemon providing DVMRP for IPv4
* net-snmp-5.7.2_1               An extendable SNMP implementation
* openldap-client-2.4.33_1       Open source LDAP client implementation
* pftop-0.7_1                    Utility for real-time display of statistics for pf
* pimdd-0.2.1.0                  UO Dense Protocol-Independent Multicast (PIM-DM) daemon for IPv4
* pkg-1.0.3_1                    New generation package manager
* quagga-re-0.99.17.11           A branch of popular quagga software pointed at stability
* ssmtp-2.64                     Extremely simple MTA to get mail off the system to a mail hub
* sudo-1.8.6.p3_1                Allow others to run commands as root
* tmux-1.7_1                     A Terminal Multiplexer
* ucarp-1.5.2_1                  Userlevel Common Address Redundancy Protocol
* virtio-kmod-9.1-0.242658       virtio kernel modules port for 8.[23]/9.[01]

-----------------------------------------
# Release 1.2 (2012/12/20)

## New features
* Update base to FreeBSD 9.1-Release
* Add Kernel drivers: netmap (framework for fast packet I/O), Encapsulating Interface (enc), some 1OG NICs (cxgb, cxgbe, mxge, nxge), SCSI/RAID controllers, Intel ICH watchdog, ipmi, asni and virtio
* FreeBSD patches:
	* kern/163208 PF state key linking mismatch
	* if_bridge and if_lagg: increased performance (from -current)
	* boot-loader and dual console (vga/serial)
      no more hang if no serial port present, the vga image have dual console (vga/serial) enabled
	* syslogd: IPv6 support (from -current)
* Default kern.ipc.nmbclusters increased to 275MB
* Re-enable DMA and disk-caching
* Transmit and receive descriptors for igb(4) and em(4) set to max (4096) and kern.ipc.nmbclusters increased
  This changes create problems on i386 arch with less than 256Mb of RAM
  For solving it: Remove all line that contains hw.*.?xd in /boot/loader.conf.local
* Migrated to the new pkg tool
* New packages:
	* mctest (a multicast test tool)
    * net/pimdd
    * security/sudo
    * sysutils/ipmitool
    * security/ipsec-tools
* Man pages are now included
* Add 'system rollback': Rollback to previous version
* Add 'system expand-data-slice': Expand the size of /data to all available space on disk and enable soft update journaling on it.
* Redirect periodic output to a log file
* User customized /boot/loader.conf.local file is preserved after an upgrade
* Add version number on the boot menu
* Build script speed improvement: add mdmfs support, kept distfiles in the same folder as FreeBSD sources, didn't compile all kernel modules 
* Lab tools: Scripts adapted to virtualbox 4.2 (maximum number of NIC increased to 36) and virtio mode supported

## Updated packages
* Bird to 1.3.8
* Quagga to Quagga-RE 0.99.17.11
* ISC-isc-dhcp to 4.2.4-P1
* freevrrpd to 1.1
* net-snmp 5.7.2
* mrouted to 3.9.6

## Notes
Regarding netmap:
* Only 3 demos tools available:
    * ipfw-userland version (use /usr/local/bin/ipfw in place of /usr/bin/ipfw)
    * pkt-gen: a packet sink/source
    * bridge: a two-port jumper wire
* Support only theses NICs: em, igb, lem, re, ixgbe
* Minimum RAM requirements was increased to 512MB (netmap needs about 200MB)
* More information about netmap: http://info.iet.unipi.it/~luigi/netmap/

## Installed packages
* NetPIPE-3.7.1                  A self-scaling network benchmark
* bird-1.3.8                     Dynamic IP routing daemon (IPv4 version)
* bird6-1.3.8                    Dynamic IP routing daemon (IPv6 version)
* dlmalloc-2.8.4                 Small, fast malloc library by Doug Lea
* fprobe-1.1_1                   Tool that collects network traffic data
* freevrrpd-1.1                  This a VRRP RFC2338 Compliant implementation under FreeBSD
* iperf-2.0.5                    A tool to measure maximum TCP and UDP bandwidth
* ipfw-user-0.1                  Netmap-enabled IPFW userspace version
* ipmitool-1.8.12_1              CLI to manage IPMI systems
* ipsec-tools-0.8.0_3            KAME racoon IKE daemon, ipsec-tools version
* isc-dhcp42-relay-4.2.4         The ISC Dynamic Host Configuration Protocol relay
* isc-dhcp42-server-4.2.4_2      The ISC Dynamic Host Configuration Protocol server
* libevent-1.4.14b_2             Provides an API to execute callback functions on certain events
* libgcrypt-1.5.0_1              General purpose crypto library based on code used in GnuPG
* libgpg-error-1.10              Common error values for all GnuPG components
* mcast-tools-20061214_1         IPv6 multicast routing daemons and tools
* mpd-5.6                        Multi-link PPP daemon based on netgraph(4)
* mrouted-3.9.6                  Multicast routing daemon providing DVMRP for IPv4
* net-snmp-5.7.2_1               An extendable SNMP implementation
* openldap-client-2.4.33_1       Open source LDAP client implementation
* pftop-0.7_1                    Utility for real-time display of statistics for pf
* pimdd-0.2.1.0                  UO Dense Protocol-Independent Multicast (PIM-DM) daemon for IPv4
* pkg-1.0.3_1                    New generation package manager
* quagga-re-0.99.17.11           A branch of popular quagga software pointed at stability
* ssmtp-2.64                     Extremely simple MTA to get mail off the system to a mail hub
* sudo-1.8.6.p3_1                Allow others to run commands as root
* tmux-1.7_1                     A Terminal Multiplexer
* ucarp-1.5.2_1                  Userlevel Common Address Redundancy Protocol
* virtio-kmod-9.1-0.242658       virtio kernel modules port for 8.[23]/9.[01]
 
----------------------------
# Release 1.1 (2012/02/16)

## New features
* Upade base to FreeBSD 8.2-RELEASE-p6
* netblast/netstend/netreceive bench tools now support IPv6
* Add keymap languages files
* Add a tools for using Quagga as BGP route generator: quagga-bgp-netgen
* Lab script: Permit to configure routers' RAM size
* Kernel: Disable softupdates and swapping, enable IPSEC NAT-T

## Bug fix
* fix "can't set default locale" message
* netstat -z now clear IPv6 stats too (bin/153206)

## Updated packages
* Bird to 1.3.6
* net-snmp to 5.7.1_4
* tmux to 1.6
* mpd to 5.6

## Installed packages
* NetPIPE-3.7.1       A self-scaling network benchmark
* bird-1.3.6          Dynamic IP routing daemon (IPv4 version)
* bird6-1.3.6         Dynamic IP routing daemon (IPv6 version)
* dlmalloc-2.8.4      Small, fast malloc library by Doug Lea
* fprobe-1.1_1        Tool that collects network traffic data
* freevrrpd-1.0       This a VRRP RFC2338 Compliant implementation under FreeBSD
* iperf-2.0.5         A tool to measure maximum TCP and UDP bandwidth
* isc-dhcp42-relay-4.2.3 The ISC Dynamic Host Configuration Protocol relay
* isc-dhcp42-server-4.2.3_2 The ISC Dynamic Host Configuration Protocol server
* libevent-1.4.14b_2  Provides an API to execute callback functions on certain ev
* mcast-tools-20061214_1 IPv6 multicast routing daemons and tools
* mpd-5.6             Multi-link PPP daemon based on netgraph(4)
* mrouted-3.9.5       Multicast routing daemon providing DVMRP for IPv4
* net-snmp-5.7.1_4    An extendable SNMP implementation
* quagga-0.99.20_3    Free RIPv1, RIPv2, OSPFv2, BGP4, IS-IS route software
* ssmtp-2.64          Extremely simple MTA to get mail off the system to a mail h
* tmux-1.6            A Terminal Multiplexer
* ucarp-1.5.2_1       Userlevel Common Address Redundancy Protocol

----------------------------
# Release 1.0 (2011/10/04)

## New features
* Upade base to FreeBSD 8.2-RELEASE-p4
* Add FreeBSD network benchmark tools: netblast,netsend and netreceive
* Use XZ in place of BZIP2 for config files archives
* mtree: remove md5 checksum
* kernel patched for bird and FIB usage
* Freevrrp rc script: Auto-load netgraph modules
* Add telnet (usefull for connecting local mpd control port)

## Bug fixes
* fix "config save", that save unmodified files and didn't delete old files
* fix "show" that didn't support more than 1 option
* Fix ndp tools installation
* Fix default bird startup scripts that used bad folder for control socket
* Fix Ethernet interfaces names in bird
* Fix the upgrade script (merge changes in /boot/loader.conf)
* Fix a carp bug when preemption is enabled (kern/161123)
* Forgot to add the dummynet kernel module
* Build tool: Add a check to the FreeBSD source code branch used

## Updated packages
* Quagga to 0.99.20
* Bird to 1.3.3 (support FIB and include config file)
* mrouted to 3.9.5
* net-snmp to 5.7
* isc-dhcp server/relay to 4.2.2

## Installed packages
* NetPIPE-3.7.1       A self-scaling network benchmark
* bird-1.3.3          Dynamic IP routing daemon (IPv4 version)
* bird6-1.3.3         Dynamic IP routing daemon (IPv6 version)
* dlmalloc-2.8.4      Small, fast malloc library by Doug Lea
* expat-2.0.1_2       XML 1.0 parser written in C
* fprobe-1.1_1        Tool that collects network traffic data
* freevrrpd-1.0       This a VRRP RFC2338 Compliant implementation under FreeBSD
* iperf-2.0.5         A tool to measure maximum TCP and UDP bandwidth
* isc-dhcp42-relay-4.2.2 The ISC Dynamic Host Configuration Protocol relay
* isc-dhcp42-server-4.2.2 The ISC Dynamic Host Configuration Protocol server
* libevent-1.4.14b_2  Provides an API to execute callback functions on certain ev
* libpdel-0.5.3_4     Packet Design multi-purpose C library for embedded applicat
* mcast-tools-20061214_1 IPv6 multicast routing daemons and tools
* mpd-5.5             Multi-link PPP daemon based on netgraph(4)
* mrouted-3.9.5       Multicast routing daemon providing DVMRP for IPv4
* net-snmp-5.7_3      An extendable SNMP implementation
* quagga-0.99.20      Free RIPv1, RIPv2, OSPFv2, BGP4, IS-IS route software
* ssmtp-2.64          Extremely simple MTA to get mail off the system to a mail h
* tmux-1.5            A Terminal Multiplexer
* ucarp-1.5.2_1       Userlevel Common Address Redundancy Protocol

---------------------------------------------------------
# Release 0.35 (2011/03/06)

## WARNING
Special upgrade procedure is needed for this release ! (check notes)

## New features
* Update to FreeBSD 8.2-RELEASE
* BSDRP's nanobsd patches were include to FreeBSD-current, then replace BSDRP's nanobsd by FreeBSD's nanobsd
* Reduce bootloader timeout to 1 second
* Reduce the security level of the kernel to default value (loading kernel module is easiest)
* Use xz in place of bzip2 for BSDRP files (images, mtree)
* Possibility to use a post-upgrade script included in the new image during upgrade
* Detect KVM guest usage
* MS Windows Virtualbox lab script improvement: Permit to use a 'shared with host (hostonly)' interface
* Added: net/mpd5, a PPP Multilink daemon (multilink, PAP, CHAP, MS-CHAP and EAP authentication, PPTP, L2TP, PPPoE, etc...)
* Disable polling by default: Modern NIC include interrupt management and enabling polling on this modern NIC can reduce performance

## Bug fixes
* Hardened the upgrade and config scripts
* Add missing kernel modules and binary: ipfw_nat, libaliase, pflog, tap interface

## Updated packages
* freeVRRPd (It depends of some netgraph modules now)
* Quagga
* Bird
* tmux
* ssmtp

## Know bugs
* "system endpoint" seams to decrease TCP performance in place of increase them
* FreeBSD Bootloader manager (boot0) didn't support serial speed value more than 9600 baud (kernel and console use 38400)

## Upgrade procedure
The new nanobsd script change the glabel name scheme of the partition, then the embedded upgrade script can't manage
theses new names.
You need to use a special upgrade script, that will convert partition name.

1 Download the special upgrade script to your router in /tmp
  As example, using fetch:
  cd /tmp
  fetch http://bsdrp.net/tools/upgrade-to-035
  chmod +x /tmp/upgrade-to-035
2 Launch the upgrade using this newly downloaded upgrade script
  As example, from a SSH server:
  ssh username@ssh-sever-name cat /directory-to/BSDRP_0.35_upgrade_i386_serial.img.xz | unxz | /tmp/upgrade-to-035
3 Once done, reboot and answer "no" to the question "Do you want to save your configuration?"

## Installed packages
* NetPIPE-3.7.1       A self-scaling network benchmark
* bird-1.2.5          Dynamic IP routing daemon (IPv4 version)
* bird6-1.2.5         Dynamic IP routing daemon (IPv6 version)
* dlmalloc-2.8.4      Small, fast malloc library by Doug Lea
* expat-2.0.1_1       XML 1.0 parser written in C
* fprobe-1.1_1        Tool that collects network traffic data
* freevrrpd-1.0       This a VRRP RFC2338 Compliant implementation under FreeBSD
* iperf-2.0.5         A tool to measure maximum TCP and UDP bandwidth
* isc-dhcp31-relay-3.1.ESV,1 The ISC Dynamic Host Configuration Protocol relay
* isc-dhcp31-server-3.1.ESV,1 The ISC Dynamic Host Configuration Protocol server
* libevent-1.4.14b_2  Provides an API to execute callback functions on certain ev
* libpdel-0.5.3_4     Packet Design multi-purpose C library for embedded applicat
* mcast-tools-20061214_1 IPv6 multicast routing daemons and tools
* mpd-5.5             Multi-link PPP daemon based on netgraph(4)
* mrouted-3.9_1       Multicast routing daemon providing DVMRP for IPv4
* net-snmp-5.5_4      An extendable SNMP implementation
* quagga-0.99.17_5    Free RIPv1, RIPv2, OSPFv2, BGP4, IS-IS route software
* ssmtp-2.64          Extremely simple MTA to get mail off the system to a mail h
* tmux-1.4_4          A Terminal Multiplexer
* ucarp-1.5.2_1       Userlevel Common Address Redundancy Protocol

-------------------------------------------
# Release 0.34 (2010/09/15)

## New features
* Kernel:
	* Add ipdivert module 
	* Re-enable kbd-mux that permit to use USB keyboard
* Clean the default /etc/rc.conf, put specials BSDRP parameters in /etc/rc.conf.misc 
* Add tmux (terminal multiplexer)
* Add patch that permit to compile net/bird and net/bird6 on sparc64
* Secure quagga VTY by listenning to localhost only (thankt to Nugroho Atmotaruno)
* Updated ports:
	* Bird to 1.2.4
	* Quagga to 0.99.17

## Bug fix
* Fix ipfw module load by adding libalias module 
* Fix ucarp comportement by using carp-up/carp-down script that create an alias for the virtual IP on the master host
* Fix writing ssh keys for root (Thanks to Christian Degen)
* Fix crontab backup (Thanks to Christian Degen)
* Fix the problem of "Device not configured." after an upgrade (using gpart in place of fdisk)
* Fix error message "blanktimevidcontrol: not found" (Thanks to Nugroho Atmotaruno)

## Know bug
* "system endpoint" seams to decrease TCP performance in place of increase them

## Installed packages
* NetPIPE-3.7.1       A self-scaling network benchmark
* bird-1.2.4          Dynamic IP routing daemon (IPv4 version)
* bird6-1.2.4         Dynamic IP routing daemon (IPv6 version)
* dlmalloc-2.8.4      Small, fast malloc library by Doug Lea
* fprobe-1.1_1        Tool that collects network traffic data
* freevrrpd-0.9.3     This a VRRP RFC2338 Compliant implementation under FreeBSD
* iperf-2.0.4         A tool to measure maximum TCP and UDP bandwidth
* isc-dhcp31-relay-3.1.3_1 The ISC Dynamic Host Configuration Protocol relay
* isc-dhcp31-server-3.1.3_1 The ISC Dynamic Host Configuration Protocol server
* libevent-1.4.14b_1  Provides an API to execute callback functions on certain ev
* mcast-tools-20061214 IPv6 multicast routing daemons and tools
* mrouted-3.9_1       Multicast routing daemon providing DVMRP for IPv4
* net-snmp-5.5_4      An extendable SNMP implementation
* quagga-0.99.17      Free RIPv1, RIPv2, OSPFv2, BGP4, IS-IS route software
* ssmtp-2.62.3        Extremely simple MTA to get mail off the system to a mail h
* tmux-1.3            A Terminal Multiplexer
* ucarp-1.5.2_1       Userlevel Common Address Redundancy Protocol

---------------------------------------------------
# Release 0.33 (2010/07/21)

## New features
* Media size needs reduced from 512MB to 256MB (Thanks Warner Losh)
* Based on FreeBSD 8.1-Release
* Security: Reference file available for integrity check (mtree with sha256 and md5 hash)
* Change serial port default speed to 38400 baud (8 bits, no parity, and 1 stop bit)
* Kernel:
	* CPU support: Geode, Soekris, Elan
	* siis drivers (SiliconImage Serial ATA Host Controller)
* Kernel modules added:
	* GRE module (GRE and MOBILE encapsulation)
	* Hifn 7751/7951/7811/7955/7956 crypto accelerator padlock
	  (cryptographic functions and RNG in VIA C3, C7 and Eden processors)
	* safe (SafeNet crypto accelerator)
	* ubsec (SafeNet crypto accelerator)
	* glxsb (i386 only: Geode LX Security Block crypto accelerator)
* Replace dhcprelya by isc-dhcp-relay
* Replace XORP by BIRD (BIRD is more used and lighter)
* Upgraded ports:
	* quagga from quagga-0.99.15_5 to 0.99.16
	* ucarp from 1.5.1 to 1.5.2
* Add isc-dhcp-server: Permit to use BSDRP as a DHCP server
* Add ssmtp: Permit to send mail from BSDRP
* Add some bench tools: iperf and netpipe
* Add IPv6 multicast PIM routing daemons and tools
* Add IPv4 DVMRP (multicast) routing daemon: mrouted
* Add "show tech-support"
* Add multiple VHID support on rc CARP script
* Sysctl: Do not generate core files, enable zerocopy for bpf by default
* Re-enable "system virtualize" for FreeBSD 8.1
  reduce kern.hz in VM (seem that FBSD 8.1 didn't auto-adapt anymore)
* Removed VIM-lite: Ratio size/feature (syntaxe colorization) not enough usefull
* Use UTF-8 for console
* Disable ATA DMA in loader.conf for fixing Soekris boot
* Remove sendmail error message during bootup (thanks Nugroho Atmotaruno)

Related:
* Add a MS Windows VBScript for BSDRP VirtualBox lab:
  http://bsdrp.svn.sourceforge.net/viewvc/bsdrp/trunk/virtualbox.vbs

## Bugs fixes
* Quagga IPv6 address on interface (quagga bug id 408)
* Virtual box lab script: Fix problem with use of serial line terminal emulation (thanks to Baptiste Daroussin)
* Add a delay during boot sequence for permit to boot from USB device (FreeBSD 8.0/8.1 bug: usb/143790)
* Fix RC polling script that display inversed result
* vga consoles are disabled on the serial release (prevent to display getty errors messages)
* Fix upgrade script that can't change the active partition

## Installed packages
* bird-1.2.3, Dynamic IP routing daemon (IPv4 version) 
* bird6-1.2.3, Dynamic IP routing daemon (IPv6 version) 
* dlmalloc-2.8.4, Small, fast malloc library by Doug Lea 
* fprobe-1.1_1, Tool that collects network traffic data 
* freevrrpd-0.9.3, This a VRRP RFC2338 Compliant implementation under FreeBSD 
* iperf-2.0.4, A tool to measure maximum TCP and UDP bandwidth
* isc-dhcp31-relay-3.1.3_1, The ISC Dynamic Host Configuration Protocol relay 
* isc-dhcp31-server-3.1.3_1, The ISC Dynamic Host Configuration Protocol server 
* mcast-tools-20061214, IPv6 multicast routing daemons and tools 
* mrouted-3.9_1, Multicast routing daemon providing DVMRP for IPv4
* NetPIPE-3.7.1, A self-scaling network benchmark
* net-snmp-5.5_3, An extendable SNMP implementation 
* openlldp-0.3.a_1, Link Layer Discovery Protocol daemon 
* quagga-0.99.16, Free RIPv1, RIPv2, OSPFv2, BGP4, IS-IS route software
* ssmtp-2.62.3, Extremely simple MTA to get mail off the system to a mail hub 
* ucarp-1.5.2, Userlevel Common Address Redundancy Protocol 

--------------------------------------------------
# Release 0.32 (2010/02/17)
## New features
* Based on FreeBSD 8.0-Release-p2
* Add tools:
	* "show memory" and "show traffic" options
	* "rvi" , that use RCS revisionning for editing file
	* "config put" / "config get" , permit to send/download config file (SCP)
* Add fprobe (NetFlow probes)
* Add OpenLLDP (Link-Layer Discovery Protocol)
* Add dhcprelya (DHCP relay)
* Disable "system virtualized" tuning tool when detecting FreeBSD 8
* Replace carp in kernel by ucarp (userland carp)
* Add VRRP (using FreeVRRPd)
* Move packet filter from kernel to a module (disable pfsync and pflog)
* Provide Qemu and Virtualbox lab scripts (see http://bsdrp.net for more information)
* Upgrade to Quagga 0.99.15
* Kernel more smaller: Disable audit, MAC, Gjournal
* Increase /var to 10Mb

## Bugs fixes
* Remove vm-check in /root/.cshrc that prevent use of scp
* Serial port no more mandatory for vga release (#2857424)
* Keyboard works under Virtualbox (#2840062)
* nsswitch error messages in /var/log/cron
* Bad xorp default configuration file 

## Know bugs
* Quagga: Can't set IPv6 address on interface (https://bugzilla.quagga.net/show_bug.cgi?id=408)
* Virtualbox lab script: TAB and arrows key didn't works using the serial release (socat problem ?)
* There are lot's of regression in FreeBSD 8.0-Release, will release a new as soon as 8.1-Release
  will be available

-----------------------------------------------------
# Release 0.31 (2009/08/30)

## New features
* Add Virtualbox detection on "system check-vm" (thanks to Baptiste Chaussade)
* Cleanup default /etc/rc.conf
* Remove not impacting sysctl tunning (TCP endpoint related)
* Prevent somes warning message during startup (dumpdev, net-snmp)
* Kernel : enable Packet filter (mandatory for altq), enable ALTQ_NOPPC because kernel use SMP

## Bug fixes
* "system check-vm" tool badly detected allready tuned system 
* make.sh need to be started twice for generating the images (Bug 2843819)
* Adapt nsswitch.conf to BSDRP (WITHOUT_NIS)
* Problem with bad permission on saved configuration directories, that prevent to start Quagga after a reboot (Bug 2843816)
* "system virtualized" hang the system by baddly remount an allready mounted filesystem (Bug 2843819)
* Add bridgestp module (needed for bridge)
* upgrade script doesn't works (#2846985): After using geom debug and boo0cfg, all UFS label are removed, the / is no more useable.

## Know bug
* Keyboard input don't works under VirtualBox (#2840062)

---------------------------------------------------------------
# Release 0.3 (2009/08/16)

## New features
* Downgrade to FreeBSD 7.2 (permit to use it in production environement without waiting for FreeBSD 8.0 stable)
* Add XORP (http://www.xorp.org/): Add VRRP and PIM (with OSPF, BGP, RIP)
* Add ISISd with Quagga
* Enable IPv6 forwarding by default
* Enable carp,lagg,vlan,netgraph,zero_copy_sockets in the kernel
* Cleanup: Remove all non usefull kernel modules, remove perl, gzip kernel, replace vim with vim-lite, remove docs/infos files
* Begin to tune kernel and sysctl values
* Enable device polling for all NIC that support it  and changes kern.HZ from 1000 to 2000
* BSDRP script: Add system tool, and prevent to halt/reboot without saving configuration
* Add warning if running under Qemu without tuning kern.hz is detected
* Build tools:
	* Patch NanoBSD with a proposed patch (http://www.freebsd.org/cgi/query-pr.cgi?pr=136889)
	* Permit to build BSDRP from a FreeBSD 7.2 or 8.0 source base
	* Prevent to rebuild ports for each nanobsd image rebuild
	* Create a qemu script for testing BSDRP
	* Replace questions in the make.sh script by command line options
	* Add auto-cleanup function of unmounted unionfs directory

## Bugs fix
* Fix quagga vty permission: This bug prevent to start quagga after a reboot
* Adapt NanoBSD update script to the new comportement of boot0cfg since FreeBSD 7.2: This bug prevent to boot on the correct
slice after an upgrade.
* Fix TARGET_ARCH variable in make.sh for compiling ports

----------------------------------------------------------------
# Release 0.2 (2009/07/12)

## New features
* Upgrade to FreeBSD 8.0-BETA1
* Removing "ad0" or "da0" dependency using glabel: Big thanks to Scott Ullrich (pfSense) for this tips!
* Reduce the minimum disk size from 1GB to 512MB
* Tune Kernel: Enable MROUTING and ALTQ, MULTIPLE FIB (4), disable flowtable
* Improve/fix bugs in the BSDRP scripts: upgrade and config

-----------------------------------------------------------------
# Release 0.1 (2009/07/04)

First Release that include:
* Base FreeBSD 8.0-CURRENT system (NanoBSD), without VIMAGE support
* Customized script (config, upgrade, help, command completion, etc.)
* Quagga ready to use (OSPFv2, OSPFv3, RIP, RIPng and BGP)