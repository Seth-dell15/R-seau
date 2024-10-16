☀️ Uniquement avec des commandes, prouvez-que :

```powershell

client 1 :
2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:80:a4:4c brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.11/24 brd 10.5.1.255 scope global enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe80:a44c/64 scope link 

Static hostname: hugo
ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.036 ms

client 2 :

2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:ea:b1:d3 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.12/24 brd 10.5.1.255 scope global enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:feea:b1d3/64 scope link 
       valid_lft forever preferred_lft forever

Static hostname: hugo1
ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.067 ms

router :

1: lo: <LOOPBACK,UP,LOWER UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1088
in tp
a
link/loopback 88:08:08:08:08:08 brd 88:88:88:08:08:08 Inet 127.8.8.1/8 scope host lo
le
valid ift forever preferred_Ift forever
car
Inet6::1/128 scope host valid Ift forever preferred Ift forever
link/ether 88:88:27:96:a5:14 brd ff ff ff ff ff ff
Inet 18.5.1.254/24 brd 18.5.1.255 scope global nopref ixroute enpes3
appe
valid ift forever preferred_Ift forever Inets fe88::a88:27ff: fe%:a5f4/64 scope link
NAT
valid Ift forever preferred_Ift forever
link/ether 88:88:27:08:3e:c7 brd ffffffffffff
2: enp8s3: <BROADCAST, MULTICAST, UP, LOWER UP> mtu 1588 qdisc fq codel state UP group default qlen 1000
3: enpes: <BROADCAST, MULTICAST,UP,LOWER_UP> mtu 1588 qdisc fq_codel state UP group default qlen 1888

ping 127.0.0.1
PING 127.0.0.1 (127.8.8.1) 56(84) bytes of data,
igure bytes from 127.8.8.1: icmp_seq=2 ttl=64 time-8.853 m 64 bytes from 127.8.8.1: icmp_seq=1 ttl=64 time 8.881 ms
as 127.8.8.1 ping statistics ---
mette 2 packets transmitted, 2 received, 8% packet loss, time 1850ms 8.853/8.067/8.881/8.914m

Static hostname: box

```

☀️ Déjà, prouvez que le routeur a un accès internet

```powershell

PING www.nov.com (172.67.74.226) 56(04) bytes of data. 64 bytes from 172.67.74.226 (172.67.74.226): icmp seq=1 ttl=53 time-29.2 4 bytes from 172.67.74.226 (172.67. 2.74.226): icmp_seq=2 ttl=5311mm-26.9 64 bytes from 172.67.74.226 (172.67.74.226): icmp seq=3 tt1-53 time 44.0
www.mov.com ping statistics
3 packets transmitted, 3 received, Br packet loss, time 2824 rtt min/avg/max/mdev 26.93 .935/33.644/11.838/7.962 root@box network-scripts In

```
☀️ Activez le routage

```powershell

[root@box network-scripts]# sudo firewall-cmd --add-masquerade --permanent
success
[root@box network-scripts]# sudo firewall-cmd --reload
success
root@box network-scriptsl#

```
☀️ Prouvez que les clients ont un accès internet

```powershell

ping 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=53 time=83.1 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=53 time=22.9 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=53 time=27.3 ms

--- 1.1.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 22.926/44.433/83.060/27.372 ms

```
☀️ Montrez-moi le contenu final du fichier de configuration de l'interface réseau

```powershell

cat /etc/netplan/01-netcfg.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s8:
      dhcp4: no
      addresses: [10.5.1.12/24]

```
☀️ Sur routeur.tp5.b1, déterminer sur quel port écoute le serveur SSH

```powershell

sudo ss-Inpt | grep 22
LISTEN 0 128 0.0.0.0:22  0.0.0.0:*   users:(("sshd",pid=756,fd=3))
LISTEN 0 128    [::]:22     [::]:*   users:(("sshd",pid=756,fd=3))

```

☀️Sur routeur.tp5.b1, vérifier que ce port est bien ouvert

```powershell

sudo firewall-cmd --permanent --add-port=22/tcp
success

```