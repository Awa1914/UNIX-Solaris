# UNIX-Solaris
CHEATSHEET (INTRO SOL SERVER TO NETWORK)

1) Hostname change (three files)
	> /etc/nodename
	> /etc/hostname.e1000g0
	> /etc/hosts
2) Default Gateway Configuration
	> /etc/defaultrouter
3) DNS configuration
	> /etc/resolv.conf
	> /etc/nsswitch.conf
4) Static IP Change
	> Add new static IP in "/etc/hosts"
	> $ifconfig e1000g0 inet <new ip>/24 up (new IP maintains first 3 octets, hostname & changes)

E) ASSIGNING A TEMPORARY DYNAMIC IP TO YOUR SERVER
   NB: This must be performed on a system configured for static
   $ifconfig e1000g0 dhcp start
   $ifconfig -a (to verify)

Reset the dynamic IP of your Solaris Server
   $ifconfig e1000g0 dhcp drop
   $ifconfig e1000g0 dhcp start

Reset the NIC of the Solaris Server (in a situation where data isnt flowing thro the NIC)
   $ifconfig e1000g0 down
   $ifconfig e1000g0 up

F) SWITCHING A SOLARIS SERVER PERMANENTLY CONFIGURED FOR STATIC BACK TO DYNAMIC

1) $ifconfig e1000g0 dhcp start (to pick up dynamic IP from DHCP)
2) $touch /etc/dhcp.e1000g0 (to permanently switch the server from static to dynamic)
