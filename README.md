# netfilter items
Files related to netfilter like nftables, fail2ban and using blocklists

These files are initially made for my system: Raspberry Pi with Raspbian (Buster), and with 
 - IPv6 enabled
 - a separate logfile, and tailored logging
 - Fail2Ban                     (https://wiki.meurisse.org/wiki/Fail2Ban)
 - blocklist-with-nftables      (https://github.com/kubax/blocklist-with-nftables, see there) 
  
Upgrading to Buster left me saying goodbye to iptables, netfilter-persistent and ipset. I had to rebuild my previous firewall into nftables. 

In /etc/nftables.conf I added 
   include "/etc/nftables/include/*.nft"

In /etc/nftables/include/ I put filter.nft, with some additional rules to cater my system. 

Instead of the fail2ban.conf I put my fail2ban.nft into /etc/nftables/. I implemented all other suggestions of wiki.meurisse.org.

In /etc/rsyslog.conf I added in the Rules section 
   :msg, contains, "Firewall"              /var/log/firewall.log
   & stop
and restarted rsyslog with ' sudo systemctl restart rsyslog'. 
Also I added the file firewall to /etc/logrotate.d. 
In /etc/logwatch/conf/logfiles/iptables.conf I set the LogFile to /var/log/firewall.log. 

Finally I did a 'sudo apt remove iptables ipset netfilter-persistent'. 

!! Any comments or suggestions are welcome !!
