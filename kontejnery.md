Upravy
======

upravena sluzba, ktera pousti kontejnery(aby nemenila uzivatele)
------------------------------------------------------------------

--- /lib/systemd/system/systemd-nspawn@.service	2016-12-17 18:49:44.291074320 +0100
+++ /lib/systemd/system/systemd-nspawn@.service_orig	2016-12-17 18:49:24.567268996 +0100
@@ -13,7 +13,7 @@
 After=network.target
 
 [Service]
-ExecStart=/usr/bin/systemd-nspawn --quiet --keep-unit --boot --link-journal=try-guest --settings=override --machine=%i
+ExecStart=/usr/bin/systemd-nspawn --quiet --keep-unit --boot --link-journal=try-guest --network-veth -U --settings=override --machine=%i
 KillMode=mixed
 Type=notify
 RestartForceExitStatus=133

vytvoren symlink - hardcodovana cesta na /var/lib/machines
----------------------------------------------------------

lrwxrwxrwx 1 root     root       15 Dec 17 16:30 machines -> /srv/containers



Poznamky
========

* adresar s kontejnery(link z /var/lib/machines)  
  /srv/containers


* adresar s "OS"  
  /srv/images

Vytvoreni "rootu"
=================

* debian/ubuntu deboostrap  
  debootstrap --variant=minbase stable mumble-new http://deb.debian.org/debian/

  *nutne po nainstalovani pustit konsoli a nainstalovat co je potreba pripadne vytvorit uzivatele + sudo*  
  systemd-nspawn -D "/srv/containers/mumble"


ovladani kontejneru
===================

* pusteni kontejneru s prihlasenim do shellu  
  systemd-nspawn -D "/srv/containers/mumble"

* boot kontejneru s login prompt  
  systemd-nspawn -bD "/srv/containers/mumble"

* login do konzole  
  machinectl login mumble

* pusteni na pozadi  
  machinectl start mumble

* stopnuti kontejneru  
  machinectl poweroff mumble

* pusteni sluzby(po startu)  
  systemctl start systemd-nspawn@mumble

* vypnuti sluzby(po startu)  
  systemctl stop systemd-nspawn@mumble
