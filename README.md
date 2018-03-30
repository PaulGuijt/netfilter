# netfilter items
Files related to netfilter like iptable, ipset and fail2ban

These files are initially made for my system: Raspberry Pi with Raspbian, and with 
 - IPv6 enabled
 - netfilter-persistent, including its plugins for ipset and iptables 
 - Fail2Ban
 - [IPSet-Blacklist](https://github.com/trick77/ipset-blacklist)
 
Netfilter-persistent and Fail2Ban go well together, as long as you add to the header of /etc/init.d/netfilter-persistent
```
# X-Start-Before:    fail2ban
# X-Stop-After:      fail2ban
```

Ipsets-persistent flushes the ipsets at shutdown and restores from /etc/iptables/rules.* at startup. That's why in /etc/ipset-blacklist/ipset-blacklist.conf must be set
```
IP_BLACKLIST_RESTORE=/etc/iptables/rules.ipset
```
/etc/ipset-blacklist/ip-blacklist.restore can be deleted (and should, to avoid mishap), and rules.ipset is by definition the same as the ipset blacklist in memory.
