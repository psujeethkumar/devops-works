Check opened ports :

cat /etc/services
grep -w '[port-number]/tcp' /etc/services
sudo ss -tulpn

List actively used ports :
