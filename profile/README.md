# CharlotteOS

A project with the ambitious goal of creating a novel modern (i.e. non-POSIX/SUS) open source operating system that is flexible, stable, secure, and easy to use and develop for.

Status: Very early development

Subprojects:

- `Charlotte Core`: The kernel of CharlotteOS
  - Will provide a paravirtualized interface between applications and system hardware so that it can offer many of the benefits of an exokernel but with better security, stability, and fault tolerance
  - Most drivers will run in userspace and use privileged kernel APIs to have essentially the same level of access to system hardware as the kernel itself
  - Some drivers for common busses and hardware such as PCI Express, USB, and storage media will be built into the kernel though they can be removed at compile time via conditional compilation
  - Will only securely multiplex hardware resources and provide mechanisms to user space application with the appropriate capabilities
    - The kernel will enforce rules and policies decided upon by userspace however it will generally not impose any of its own
- `Zenalloc`
  - A library crate similar to the standard Rust `alloc` crate that is designed to never panic making it suitable for use in operating system kernels like Charlotte Core

Notable Third-Party Components:

- `Limine`: A 64-bit UEFI bootloader with a modern boot protocol suitable for use by operating systems like CharlotteOS
