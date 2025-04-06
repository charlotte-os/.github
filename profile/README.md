# CharlotteOS

## An Experimental Modern Operating System

### What the heck is this?

`CharlotteOS` is an experimental attempt to create a much more modern operating system than those that are in common use today. It seeks to achieve this by incorporating several features that have been described
in the operating systems research literature but thus far not used in any mainstream operating system despite providing clear advantages over their equivalents in the actual mainstream systems. Among these features are the following:

- Capability based access control
- A strongly typed system namespace used to enumerate and interact with all system resources from the filesystem to the registry and beyond as well as the same features on other hosts
- A low level OS API that allows developers to aggressively optimize their applications and libraries when they so choose and also allows for the layering of their preferred abstractions atop it
- URIs as namespace paths allowing access to system resources both locally and on the network without mounting or unmounting anything
- A highly modular kernel that internally abstracts almost all of its components to common interfaces allowing for implementations to be replaced or added relatively easily
- Graceful failure mechanisms that avoid total system failure to the extent possible by making any kernel function that can fail return a Result unless the error absolutely cannot be recovered from at all.
- Intuitive and easy to use text based and graphical interfaces
- Atomic update and installation transactions for all software including OS components with easy rollback
- A pure monolithic kernel which cannot be dynamically modified or extended in any way after it is compiled to prevent tampering and eliminate an entire category of security vulnerabilities and potential stability issues.
- others to be determined in the course of development

### How will CharlotteOS compare to other existing operating systems?

This table compares CharlotteOS to major existing operating systems across key architectural and design dimensions. It explains *why CharlotteOS exists* and how it differs fundamentally from Unix-based systems and proprietary OSes.

| Feature / OS                  | **CharlotteOS**             | **Windows 11**         | **Linux**               | **BSDs**                | **macOS**              | **Haiku**               |
|------------------------------|-----------------------------|------------------------|--------------------------|--------------------------|------------------------|-------------------------|
| **Kernel Architecture**       | Pure Monolithic (Drivers can only be added or removed at compile time by design), exokernel-inspired driver model as system calls | Hybrid              | Monolithic (modular)     | Monolithic               | Hybrid (XNU)           | Hybrid (custom)         |
| **Boot Standard**             | UEFI + ACPI only            | UEFI + ACPI            | BIOS, UEFI, DT           | BIOS, UEFI               | UEFI + ACPI            | BIOS, UEFI (limited ACPI)|
| **Init / Service Model**      | `sys-executive`, async     | `wininit`, `svchost`   | `systemd`, `OpenRC` etc. | `rc`, `launchd` (Darwin) | `launchd`              | `launch_daemon`         |
| **Filesystem Model**          | System Namespace with URI paths, Volume-centric FS subnamespace, no `/` root | Drive letters, NTFS    | Unix FS hierarchy        | Unix FS hierarchy        | APFS, Unix hierarchy   | BFS, simplified hierarchy|
| **Syscall Interface**         | New CharlotteOS specific  | Win32 / NT Native      | POSIX                    | POSIX                    | POSIX + Apple syscalls | BeOS-style syscalls     |
| **Programming Model**         | Rust idioms focused system libararies exposed via stable C ABI | Win32, C/C++, .NET | POSIX, C/C++, Rust       | POSIX, C/C++             | Obj-C, Swift, POSIX    | C++, BeAPI              |
| **User/Kernel Separation**    | Strong, capability-enforced | Partial                | Strong, but mixed        | Strong                   | Strong                 | Moderate                |
| **Security Model**            | Capability-based             | ACLs + Token-based     | DAC, SELinux, AppArmor   | DAC, MAC (optional)      | App Sandbox, SIP       | Basic permissions       |
| **Concurrency Model**         | Async-first, lightweight preemptive threading   | Threads (preemptive)   | Threads + async options  | Threads                  | Threads + GCD/queues   | Preemptive threads      |
| **Driver Model**              | Kernel-mode only but driver only abstract specific devices to a common interface for their device class which userspace must handle directly similar to an exokernel based system  | Kernel-mode & UMDF     | Kernel-only (some FUSE)  | Kernel-only              | Kernel with sandboxing | Mostly kernel drivers   |
| **Graphics Stack**            | Custom set of APIs, compositing in-kernel             | DWM, DirectX           | Wayland, X11             | X11, some Wayland        | Metal, Quartz          | App Server (custom GUI) |
| **Target Platforms**          | x86-64 only (for now)        | x86-64, ARM64          | x86, ARM, RISC-V, more   | x86, ARM (some)          | ARM64 (Apple Silicon)  | x86-64 (RISC-V WIP)     |
| **Licensing**                 | GPLv3 or later (with proprietary driver clarification)| Proprietary            | GPL, MIT, etc.           | BSD, ISC                 | Proprietary            | MIT                     |
| **Backwards Compatibility**   | None (clean break)           | Heavy legacy (Win32)   | High POSIX & ABI support | High POSIX               | High legacy support    | Partial BeOS ABI        |
| **Design Philosophy**         | Human centric, high stability, secure, and fast | Backward-compatible, mass-market | Flexibility, community-driven | Stability, correctness | UX-first, closed ecosystem | Simple desktop usability |


### How can I get involved?

Just clone any of the repositories in this organization, make a new branch and make your desired changes, then make a pull request and a maintainer will review it and either merge it or make a request for changes. You can also
feel free to open issues in any of our repositories or participate in the disussion sections.

### Is there documentation or a wiki?

Not yet but it would be ideal to create a centralized repository of developer knowledge some point soon to avoid the issues that come with relying on so called tribal knowledge.

### Licensing

All executables within this project are licensed under the GNU General Public License version 3 or later while libraries are licensed under the GNU Lesser General Public License version 3 or later. Individual repositories may also contain notices regarding specific exceptions to the requirements of the GPL 3.0 persuant to section 7 of the license which apply only to the repository in which they are placed.

If you do not wish to license your
contributions under these terms then please do not contribute. We consider the strong copyleft license to be a feature of our project as much as any functionality of the software itself.
