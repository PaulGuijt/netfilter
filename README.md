# netfilter items
Files related to netfilter like nftables, fail2ban and using blocklists

These files are initially made for my system: Raspberry Pi with Raspbian (Buster), and with 
 - IPv6 enabled
 - a separate logfile
 - Fail2Ban                     (https://wiki.meurisse.org/wiki/Fail2Ban)
 - blocklist-with-nftables      (https://github.com/kubax/blocklist-with-nftables, see there) 
 - rules for both Ipv4 and IPv6 (https://gist.github.com/jirutka/3742890)
 
Upgrading to Buster left me saying goodbye to iptables, netfilter-persistent and ipset. I had to rebuild my previous firewall into nftables. 

In /etc/nftables.conf I added 
   include "/etc/nftables/include/*.nft"

Instead of the fail2ban.conf I put my fail2ban.nft into /etc/nftables/. I implemented all other suggestions of 

In /etc/rsyslog.conf I added in the Rules section 
   :msg, contains, "Firewall"              /var/log/firewall.log
   & stop
and restarted rsyslog with ' sudo systemctl restart rsyslog'. 
Also I added 

Finally I did a 'sudo apt remove iptables ipset netfilter-persistent'. 


