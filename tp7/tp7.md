🌞 Lister les ports en écoute sur la machine
```powershell
[hugo@web ~]$ sudo ss -lnpt | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=749,fd=6),("nginx",pid=748,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=749,fd=7),("nginx",pid=748,fd=7))
```
🌞 Ouvrir le port dans le firewall de la machine
```powershell

127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.7.1.11 sitedefou.tp7.b1

🌞 Vérifier que ça a pris effet
```powershell

hugo@client1:~$ curl sitedefou.tp7.b1
meow !
```
🌞 Capture tcp_http.pcap

[Capture tcp_https.pcap](./tcp_https.pcap)

🌞 Prouvez que vous avez bien une nouvelle carte réseau wg0
```powershell

4: wg0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none
    inet 10.7.200.1/24 scope global wg0
       valid_lft forever preferred_lft forever
```
🌞 Déterminer sur quel port écoute Wireguard
```powershell

[hugo@vpn ~]$ sudo ss -lnpu | grep 51820
UNCONN 0      0            0.0.0.0:51820      0.0.0.0:*
UNCONN 0      0               [::]:51820         [::]:*
```
🌞 Ouvrez ce port dans le firewall

🌞 Ping ping ping !
```powershell

hugo@client1:~$ ping 10.7.200.1
PING 10.7.200.1 (10.7.200.1) 56(84) bytes of data.
64 bytes from 10.7.200.1: icmp_seq=1 ttl=64 time=7.05 ms
64 bytes from 10.7.200.1: icmp_seq=2 ttl=64 time=1.87 ms
^C
--- 10.7.200.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.866/4.455/7.045/2.589 ms
```
🌞 Capture ping1_vpn.pcap

[Capture ping1_vpn.pcap](./ping1_vpn.pcap)

🌞 Capture ping2_vpn.pcap

[Capture ping2_vpn.pcap](./ping2_vpn.pcap)

🌞 Prouvez que vous avez toujours un accès internet
```powershell

traceroute to 1.1.1.1 (1.1.1.1), 64 hops max
  1   10.7.200.1  1.460ms  3.897ms  2.675ms
  2   10.7.1.254  5.654ms  5.373ms  8.069ms
  3   10.0.2.2  10.735ms  4.929ms  8.996ms
```
🌞 Visitez le service Web à travers le VPN


