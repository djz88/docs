Kernel isolation - Containers
-----------------------------

Fully virtualised guests
------------------------
"Completely" separated, has bootloder, has kernel, resources in-direct through hypervisor.
Not modified OS. Novadays PVHVM can be used if OS supports it (Kernel 2.6.32+)

Paravirtualisation
------------------
We can call it as a hybrid of HVM and containers.
Guest OS has to be aware of the fact it is being paravirtualised.(Kernel 3.0+)

- Performance gain (direct access to resources)
- Faster boot - Can boot kernel directly (no bootloader)


- Still needs a hypervisor(Xen)
- Uses own kernel

What containers are about
-------------------------
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
- HW isolation level(HVM/PV/PVHVM)


- Lightweight(MiB-"hundreds of MiB")
- Can be application oriented
- isolation on a OS level(later on)

What containers technologies I will talk about?
-----------------------------------------------
- docker
- lxc(lxd)
- systemd-nspawn

Common basics? Or What are they using to isolate resources.
-----------------------------------------------------------

*(from docker and lxc)*
PID namespace—Process identifiers and capabilities
UTS namespace—Host and domain name
MNT namespace—File system access and structure
IPC namespace—Process communication over shared memory
NET namespace—Network access and structure
USR namespace—User names and identifiers
-Controls the location of the file system root
cgroups—Resource protection(cpu usage, memory usage)

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
