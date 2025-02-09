
Check opened ports :

```
cat /etc/services
grep -w '[port-number]/tcp' /etc/services
sudo ss -tulpn
iptables -L
```

List actively used ports :

``` 
netstat -tunlp
```

Open a port using firewalld:

```
sudo firewall-cmd --zone=public --add-port=[port-number]/tcp --permanent
sudo firewall-cmd --reload
```

PS: --permanent flag will make the rule persist across the reboots.
Verify the new port opened :

```
firewall-cmd --list-all
```