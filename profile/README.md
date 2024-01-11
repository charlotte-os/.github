# The Charlotte Project

A project with the ambitious goal of creating a novel modern (i.e. non-POSIX/SUS) open source operating system that is flexible, stable, secure, and easy to use and develop for.

Status: Very early development

Subprojects:

- CharlotteCore: The kernel of CharlotteOS
  - Will provide a paravirtualized interface between applications and system hardware so that it can offer many of the benefits of an exokernel but with better security, stability, and fault tolerance
  - Most drivers will run in userspace and use privileged kernel APIs to have essentially the same level of access to system hardware as the kernel itself
  - Some drivers for common busses and hardware such as PCI Express, USB, and storage media will be built into the kernel though they can be removed at compile time via conditional compilation
  - Will only securely multiplex hardware resources and provide mechanisms to user space application with the appropriate capabilities
    - The kernel will enoforce rules and policies decided upon by userspace however it will generally not impose any of its own
- CharlotteExec: The executive process of CharlotteOS
  - Will provide many of the OS features not directly provided in the kernel
  - Loaded by the bootloader alongside the kernel since the kernel will not have any form of program loader built in
  - Has all possible capabilities at all times (and thus must be designed to be secure given the potential for exploitation)
  - Will provide a program loader that uses kernel provided mechanisms to construct a process from raw parts i.e. at least a virtual address space with the needed mappings and a main thread started at the program entry point
  - Will provide shared library loading used kernel provided mechanisms
  - Can delegate certain tasks to child processes launched with the necessary capabilities to perform them in order to provide better fault tolerance and separation of concerns
  - Provides the means to load kernel servers since they are userspace processes

Notable Third-Party Components:

- Limine: A modern bootloader with the ability to load 64-bit UEFI operating systems like The Charlotte Project

Licensing: 

All software directly maintained by this project will be licensed under the latest version of the GNU General Public License unless the repository for a subproject indicates otherwise.
