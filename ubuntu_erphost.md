Installation layout
===================

Language: english_gb
Keyboard: czech

- HW Raid 1		disk0 + disk1
  + in the system sdc
    + part 1	512MB EFI
    + part 2	278G LVM rootvg-erphost
	  + homelv-erphost		40GB
		ext4 label=home-erphost (nosuid)
	  + rootlv-erphost		50GB
		ext4 label=root-erphost
	  + swaplv-erphost		3GB
	  + varloglv-erphost	5GB
		ext4 label=varlog-erphost (noexec)
- SW Raid 1		disk2 + disk3
  + in the system sda + sdb
Users: 




Postinstallation steps
======================


Packages
--------
- lm-sensors
- smartmontools
- vim
- mc
- postfix




Changes
-------
