(Kernel) Isolation - HVM, PV, OS-Virtualization technologies
============================================================
In short, this is an introduction and description of the isolation differences between HM, PV and OS-Virtualization technologies.
Presentation contains short descriptions about mentioned technologies with closer look on OS-level Virtualization (a.k.a. containers). 

Hardware-assisted virtualization
--------------------------------
AKA full virtualization

- "Completely" separated (OS doesn't know it is virtualized)
  binary translation to trap and virtualize non-virtualized instructions ... emulation
- Has own bootloder
- Has own kernel
- Not modified OS. 
- Need CPU flags (Intel `vmx` | AMD `svm`)

Resources in-direct through hypervisor.Novadays PVHVM can be used if OS supports it (Kernel 2.6.32+)

Paravirtualization
------------------
We can call it as a hybrid of HVM and containers.

- Guest OS has to be aware of the fact it is being paravirtualised.(Kernel 3.0+)
  hypervisor provides API to communicate and OS calls it
- Performance gain (direct access to resources)
- Faster boot - Can boot kernel directly (no bootloader)


- Still needs a hypervisor(Xen)
- Uses own kernel

Operating-system-level virtualization
-------------------------------------
When we talk about containers we can think about a book in a shelf.
There are multiple chapters in the book. Every chapter has
different "story" but they belong to the same piece of book.

- Sometimes called as *"jail on steroids"*.
- Containers provide an additional layer of the security by isolating
  resources(can be used together with apparmor/SELinux)
- Solves issues with shared libraries(multiple versions).
- Helps with keeping OS clean
- Easily destroyed   >:P

Difference between virtual machines & containers
------------------------------------------------
- VM are "heavier" to setup/start - in general
- OS boot takes up to minutes (PV/HVM difference)
- HW isolation on a hypervisor level(HVM/PV/PVHVM)
  qemu process represents virtual machine, 
  storage backend involved


- Lightweight(MiB-"hundreds of MiB")
- Can be application oriented
- isolation on a OS level(later on)
  process tree

Container technologies
----------------------
- chroot *1982*
  + partial file system isolation
  + nested virtualization
- OpenVZ *2005*
  + file system isolation
  + disk quotas (ZFS)
  + IO limiting
  + memory limits
  + cpu quotas
  + network isolation
  + partial nested virtualization
  + live migraion
  + root isolation
- lxc(lxd) *2008*
  + file system isolation
  + partial disk quotas (lvm/btrfs)
  + partial IO limiting (btrfs)
  + memory limits
  + cpu quotas
  + network isolation
  + partial nested virtualization
  + root isolation
- docker *2013*
  + file system isolation
  + IO limiting (since 1.10)
  + memory limits
  + cpu quotas
  + network isolation
  + partial nested virtualization
  + root isolation (since 1.10)
- systemd-nspawn
  + file system isolation
  + disk quotas 
  + partial IO limiting (systemd+Cgroups)
  + memory limits (systemd+Cgroups)
  + cpu quotas (systemd+Cgroups)
  + network isolation
  + nested virtualization
  + root isolation


Common basics? Or What are they using to isolate resources.
-----------------------------------------------------------

*(from docker and lxc)*
PID namespace—Process identifiers and capabilities
UTS namespace—Host and domain name
MNT namespace—File system access and structure
IPC namespace—Process communication over shared memory
NET namespace—Network access and structure
USR namespace—User names and identifiers
- Controls the location of the file system root

cgroups
- Resource protection(cpu usage, memory usage)

Docker
------
- using own library or lxc
- has daemon "docker" and command line application "docker"

-
- has public or private repositories for images




LXC with LXD
------------



SYSTEMD-NSPAWN
--------------



When we should/can use containers
---------------------------------
- testing a new application(from source or the internet)
- fast deployments - "iso" template for the application(or for whole
  cycle)



Used sources
------------
https://en.wikipedia.org/wiki/Hardware-assisted_virtualization
https://en.wikipedia.org/wiki/Operating-system-level_virtualization
http://www.linux-magazine.com/Issues/2016/184/systemd-nspawn
