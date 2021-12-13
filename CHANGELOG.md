# Changelog

Notable changes to Xen will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)

## [4.15.0 UNRELEASED](https://xenbits.xen.org/gitweb/?p=xen.git;a=shortlog;h=RELEASE-4.15.0) - TBD

### Added / support upgraded
 - ARM IOREQ servers (device emulation etc.) (Tech Preview)
 - Renesas IPMMU-VMSA (Supported, not security supported; was Tech Preview)
 - ARM SMMUv3 (Tech Preview)
 - Switched MSR accesses to deny by default policy.
 - Intel Processor Trace support (Tech Preview)
 - Named PCI devices for xl/libxl
 - Improved documentation for xl PCI configuration format
 - Support for zstd-compressed dom0 (x86) and domU kernels
 - EFI: Enable booting unified hypervisor/kernel/initrd/DT images
 - Reduce ACPI verbosity by default
 - Add ucode=allow-same option to test late microcode loading path
 - Library improvements from NetBSD ports upstreamed
 - CI loop: Add Alpine Linux, Ubuntu Focal targets; drop CentOS 6
 - CI loop: Add qemu-based dom0 / domU test for ARM
 - CI loop: Add dom0less aarch64 smoke test
 - x86: Allow domains to use AVX-VNNI instructions
 - Factored out HVM-specific shadow code, improving code clarity and reducing the size of PV-only hypervisor builds
 - Added XEN_SCRIPT_DIR configuration option to specify location for Xen scripts, rather than hard-coding /etc/xen/scripts
 - xennet: Documented a way for the backend (or toolstack) to specify MTU to the frontend
 - xenstore can now be live-updated on a running system. (Tech preview)
 - Some additional affordances in various xl subcommands.
 - Added workarounds for the following ARM errata: Cortex A53 #843419, Cortex A55 #1530923, Cortex A72 #853709, Cortex A73 #858921, Cortex A76 #1286807, Neoverse-N1 #1165522
 - On detecting a host crash, some debug key handlers can automatically triggered to aid in debugging
 - Increase the maximum number of guests which can share a single IRQ from 7 to 16, and make this configurable with irq-max-guests

### Removed / support downgraded

 - qemu-xen-traditional as host process device model, now "No security
   support, not recommended".  (Use as stub domain device model is still
   supported - see SUPPORT.md.)

## [4.14.0](https://xenbits.xen.org/gitweb/?p=xen.git;a=shortlog;h=RELEASE-4.14.0) - 2020-07-23

### Added
 - This file and MAINTAINERS entry.
 - Use x2APIC mode whenever available, regardless of interrupt remapping
   support.
 - Performance improvements to guest assisted TLB flushes, either when using
   the Xen hypercall interface or the viridian one.
 - Assorted pvshim performance and scalability improvements plus some bug
   fixes.
 - Hypervisor framework to ease porting Xen to run on hypervisors.
 - Initial support to run on Hyper-V.
 - Initial hypervisor file system (hypfs) support.
 - libxl support for running qemu-xen device model in a linux stubdomain.
 - New 'domid_policy', allowing domain-ids to be randomly chosen.
 - Option to preserve domain-id across migrate or save+restore.
 - Support in kdd for initial KD protocol handshake for Win 7, 8 and 10 (64 bit).
 - Tech preview support for Control-flow Execution Technology, with Xen using
   Supervisor Shadow Stacks for its own protection.

### Changed
 - The CPUID data seen by a guest on boot is now moved in the migration
   stream.  A guest migrating between non-identical hardware will now no
   longer observe details such as Family/Model/Stepping, Cache, etc changing.
   An administrator still needs to take care to ensure the features visible to
   the guest at boot are compatible with anywhere it might migrate.

## [4.13.0](https://xenbits.xen.org/gitweb/?p=xen.git;a=shortlog;h=RELEASE-4.13.0) - 2019-12-17

> Pointer to release from which CHANGELOG tracking starts
