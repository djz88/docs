# New machine checklist

- [Common settings](#common-settings)  
  - [Basic stuff](#basic-stuff)  
  - [Miscs](#miscs)  
  - [Security stuff](#security-stuff)  
- [Webservers](#webservers)  
- [Database servers](#database-servers)  



## Common settings
#### Basic stuff
* minimal installation  
  and add stuff when needed
* setup networking  
  if not done during an installation
* backup  
  setup backing-up of important files
* Raid  
  setup RAID on host or guest to prevent data lost
* Encryption  
  setup encryption of a data or disk depending on needs

  

#### Miscs
* /etc/motd  
  describes purpose of the system(webserver, db server) and OPTIONALLY versions
* profile file  
  should contain some information about the system  
  (usage, space, network stuff, last logged)
* ntpdate/ntp  
  directly to setup date synchronisation
* setup email notification/alert
* deploy monitoring scritps
  free space/mail queue/root activity/load/etc.
* install system monitor things
  like sysstat, psmisc, iotop, iftop, lsof, fuser
* adjust rsyslog/systemd configs 

#### Security stuff
* debsums/rpm checks  
  which files have been modified compared to default ones(in packages)
* logcheck  
  server setting - sometimes tweak of files is needed (create separate file is recommended)
* auditd  
  check logs(/var/log/{audit,syslog} and adjust if needed
* fail2ban  
  turn on ssh jails and additional one which fits to system purpose
* firewall setup  
  default policy for INPUT, FORWARD to DROP (optionally OUTPUT as well and tune ebtables)
* apparmor/selinux  
  enhances "permission" of a applications like what can access/read/write where  
  apparmor has utility to scan a log for desired unconfient application and "create"  
  basic profile (manual check needed)
* rootkit hunter
  for rootkit protection
