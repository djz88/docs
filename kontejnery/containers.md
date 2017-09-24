Containers (find out a better name)
-----------------------------------

What containers are about
-------------------------
When we talk about containers we can think about book in a shelf.
There are multiple chapters in the book. But every chapter has
different "story" but they belong to the same piece of book.

- Sometimes called as *"jail on steroids"*.
- Containers provide an additional layer of the security by isolating
  resources(can be used together with apparmor/SELinux)
- Solves issues with shared libraries(multiple versions).
- Helps with keeping OS clean(easily destroyed)

Difference between virtual machines & containers
------------------------------------------------
- VM are "hevier" to setup/start - in general
- Whole OS is needed to boot
- HW isolation level(HVM/PV/PVHVM)


- Lightweight(MiB-"hundreds of MiB")
- Can be application oriented
- isolation on a OS level(later on)

What containers technologies I will talk about?
-----------------------------------------------
- docker
- lxc
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
- has deamon "docker" and command line application "docker"

-
- has public or private repositories for images




LXC
---



SYSTEMD-NSPAWN
--------------



When we should/can use containers
---------------------------------
- testing a new application(from source or the internet)
- fast deployments - "iso" template for the application(or for whole
  cycle)
