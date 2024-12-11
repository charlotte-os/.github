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

### How can I get involved?

Just clone any of the repositories in this organization, make a new branch and make your desired changes, then make a pull request and a maintainer will review it and either merge it or make a request for changes. You can also
feel free to open issues in any of our repositories or participate in the disussion sections.

### Is there documentation or a wiki?

Not yet but it would be ideal to create a centralized repository of developer knowledge some point soon to avoid the issues that come with relying on so called tribal knowledge.

### Licensing

All executables within this project are licensed under the GNU General Public License version 3 or later while libraries are licensed under the GNU Lesser General Public License version 3 or later. Individual repositories may also contain notices regarding specific exceptions to the requirements of the GPL 3.0 persuant to section 7 of the license which apply only to the repository in which they are placed.

If you do not wish to license your
contributions under these terms then please do not contribute. We consider the strong copyleft license to be a feature of our project as much as any functionality of the software itself.
