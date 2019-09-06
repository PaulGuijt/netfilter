# netfilter items
Files related to netfilter like nftables, fail2ban and using blocklists

These files are initially made for my system: Raspberry Pi with Raspbian (Buster), and with 
 - IPv6 enabled
 - Fail2Ban
 - blocklist-with-nftables (https://github.com/kubax/blocklist-with-nftables)
  
Netfilter-persistent and Fail2Ban go well together, as long as you add to the header of /etc/init.d/netfilter-persistent
```
# X-Start-Before:    fail2ban
# X-Stop-After:      fail2ban
```

Upgrading to Buster left me saying goodbye to iptables, netfilter-persistent and ipset. I had to rebuild my previous firewall into nftables. 


