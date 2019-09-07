# netfilter items
Files related to netfilter like nftables, fail2ban and using blocklists

These files are initially made for my system: Raspberry Pi with Raspbian (Buster), and with 
 - IPv6 enabled
 - Fail2Ban
 - rules for both Ipv4 and IPv6 (https://gist.github.com/jirutka/3742890)
 - blocklist-with-nftables      (https://github.com/kubax/blocklist-with-nftables, see there) 
  
Upgrading to Buster left me saying goodbye to iptables, netfilter-persistent and ipset. I had to rebuild my previous firewall into nftables. Finally I did a 'sudo apt remove iptables ipset netfilter-persistent'. 


