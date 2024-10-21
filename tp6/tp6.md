☀️ Prouvez que...

Static hostname: dhcp
PING ynov.com (104.26.10.233) 56(84) bytes of data.
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=1 ttl=53 time=21.9 ms
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=2 ttl=53 time=19.9 ms

--- ynov.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 19.857/20.883/21.909/1.026 ms

Static hostname: web
PING ynov.com (172.67.74.226) 56(84) bytes of data.
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=1 ttl=53 time=26.9 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=2 ttl=53 time=22.8 ms

--- ynov.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1004ms
rtt min/avg/max/mdev = 22.770/24.827/26.885/2.057 ms

PING 10.6.1.253 (10.6.1.253) 56(84) bytes of data.
64 bytes from 10.6.1.253: icmp_seq=1 ttl=63 time=4.70 ms
64 bytes from 10.6.1.253: icmp_seq=2 ttl=63 time=4.29 ms
64 bytes from 10.6.1.253: icmp_seq=3 ttl=63 time=4.78 ms

--- 10.6.1.253 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 4.293/4.591/4.782/0.213 ms

☀️ Prouvez que...

Static hostname: client1.tp6
2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:02:f6:a3 brd ff:ff:ff:ff:ff:ff
    inet 10.6.1.137/24 metric 100 brd 10.6.1.255 scope global dynamic enp0s8
       valid_lft 547sec preferred_lft 547sec
    inet6 fe80::a00:27ff:fe02:f6a3/64 scope link
       valid_lft forever preferred_lft forever

Link 2 (enp0s8)
    Current Scopes: DNS
         Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS
                    DNSSEC=no/unsupported
       DNS Servers: 1.1.1.1 1.0.0.1
        DNS Domain: srv.world

default via 10.6.1.254 dev enp0s8 proto static onlink
default via 10.6.1.254 dev enp0s8 proto dhcp src 10.6.1.137 metric 100
1.1.1.1 via 10.6.1.254 dev enp0s8 proto dhcp src 10.6.1.137 metric 100
10.6.1.0/24 dev enp0s8 proto kernel scope link src 10.6.1.137 metric 100
10.6.1.254 dev enp0s8 proto dhcp scope link src 10.6.1.137 metric 100

PING google.com (172.217.21.14) 56(84) bytes of data.
64 bytes from fra07s29-in-f14.1e100.net (172.217.21.14): icmp_seq=1 ttl=112 time=60.2 ms
64 bytes from fra07s29-in-f14.1e100.net (172.217.21.14): icmp_seq=2 ttl=112 time=19.0 ms
64 bytes from fra07s29-in-f14.1e100.net (172.217.21.14): icmp_seq=3 ttl=112 time=31.8 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 19.016/37.034/60.245/17.227 ms

☀️ Déterminer sur quel port écoute le serveur NGINX

LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1571,fd=6),("nginx",pid=1570,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=1571,fd=7),("nginx",pid=1570,fd=7))

☀️ Ouvrir ce port dans le firewall

[hugo@localhost ~]$ sudo firewall-cmd --permanent --add-port=80/tcp
success
[hugo@localhost ~]$ sudo firewall-cmd --reload
success

☀️ Visitez le site web !

curl http://10.6.2.11
<!doctype html>
<html>
  <head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <title>HTTP Server Test Page powered by: Rocky Linux</title>
    <style type="text/css">
      /*<![CDATA[*/
      
      html {
        height: 100%;
        width: 100%;
      }  

☀️ Déterminer sur quel(s) port(s) écoute le service BIND9

LISTEN 0      10         127.0.0.1:53        0.0.0.0:*    users:(("named",pid=2245,fd=22))",pid=679,fd=4))
LISTEN 0      10         10.6.2.12:53        0.0.0.0:*    users:(("named",pid=2245,fd=25))d",pid=2245,fd=27))
LISTEN 0      4096       127.0.0.1:953       0.0.0.0:*    users:(("named",pid=2245,fd=28))
LISTEN 0      4096           [::1]:953          [::]:*    users:(("named",pid=2245,fd=29))
LISTEN 0      10             [::1]:53           [::]:*    users:(("named",pid=2245,fd=27))

☀️ Ouvrir ce(s) port(s) dans le firewall

[hugo@dns ~]$ sudo firewall-cmd --permanent --add-port=53/tcp
success
[hugo@dns ~]$ sudo firewall-cmd --permanent --add-port=953/tcp
success

☀️ Effectuez des requêtes DNS manuellement depuis le serveur DNS lui-même dans un premier temps

[hugo@dns ~]$ dig ynov.com @10.6.2.12

; <<>> DiG 9.16.23-RH <<>> ynov.com @10.6.2.12
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13748
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: 20d024cd88be876c010000006710dc4591f9730d929ee341 (good)
;; QUESTION SECTION:
;ynov.com.                      IN      A

;; ANSWER SECTION:
ynov.com.               300     IN      A       172.67.74.226
ynov.com.               300     IN      A       104.26.10.233
ynov.com.               300     IN      A       104.26.11.233

;; Query time: 422 msec
;; SERVER: 10.6.2.12#53(10.6.2.12)
;; WHEN: Thu Oct 17 11:43:33 CEST 2024
;; MSG SIZE  rcvd: 113

☀️ Effectuez une requête DNS manuellement depuis client1.tp6.b1

hugo@client1:~$ dig web.tp6.b1 @10.6.2.12

; <<>> DiG 9.18.28-0ubuntu0.24.04.1-Ubuntu <<>> web.tp6.b1 @10.6.2.12
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50475
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: dd00a64dc3a475c1010000006710df786f1a8a62ca3176ae (good)
;; QUESTION SECTION:
;web.tp6.b1.                    IN      A

;; ANSWER SECTION:
web.tp6.b1.             86400   IN      A       192.168.1.11

;; Query time: 14 msec
;; SERVER: 10.6.2.12#53(10.6.2.12) (UDP)
;; WHEN: Thu Oct 17 11:57:12 CEST 2024
;; MSG SIZE  rcvd: 83

☀️ Capturez une requête DNS et la réponse de votre serveur

[toto.pcap](./toto.pcap)

☀️ Créez un nouveau client client2.tp6.b1 vitefé

Link 2 (enp0s8)
    Current Scopes: DNS
         Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 1.1.1.1
       DNS Servers: 1.1.1.1 1.0.0.1 10.6.2.12
        DNS Domain: srv.world

🌞 ping.py

Begin emission:
Finished sending 1 packets.
*
Received 1 packets, got 1 answers, remaining 0 packets
Pong reçu : QueryAnswer(query=<Ether  dst=08:00:27:b7:b3:52 src=08:00:27:d9:12:5b type=IPv4 |<IP  frag=0 proto=icmp src=10.6.1.137 dst=10.6.1.254 |<ICMP  type=echo-request |>>>, answer=<Ether  dst=08:00:27:d9:12:5b src=08:00:27:b7:b3:52 type=IPv4 |<IP  version=4 ihl=5 tos=0x0 len=28 id=19842 flags= frag=0 ttl=64 proto=icmp chksum=0x15cd src=10.6.1.254 dst=10.6.1.137 |<ICMP  type=echo-reply code=0 chksum=0x0 id=0x0 seq=0x0 |<Padding  load='\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00' |>>>>)

🌞 dns_request.py

Begin emission:
Finished sending 1 packets.
..*
Received 3 packets, got 1 answers, remaining 0 packets
Pong reçu : QueryAnswer(query=<Ether  dst=08:00:27:b7:b3:52 src=08:00:27:d9:12:5b type=IPv4 |<IP  frag=0 proto=icmp src=10.6.1.137 dst=1.1.1.1 |<ICMP  type=echo-request |>>>, answer=<Ether  dst=08:00:27:d9:12:5b src=08:00:27:b7:b3:52 type=IPv4 |<IP  version=4 ihl=5 tos=0x0 len=28 id=47810 flags= frag=0 ttl=53 proto=icmp chksum=0xbd8e src=1.1.1.1 dst=10.6.1.137 |<ICMP  type=echo-reply code=0 chksum=0x0 id=0x0 seq=0x0 |<Padding  load='\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00' |>>>>)

🌞 dhcp request.py

Begin emission:
Finished sending 1 packets.
....*
Received 5 packets, got 1 answers, remaining 0 packets
Pong reçu : QueryAnswer(query=<IP  frag=0 proto=icmp dst=1.1.1.1 |<ICMP  |>>, answer=<IP  version=4 ihl=5 tos=0x0 len=28 id=47818 flags= frag=0 ttl=53 proto=icmp chksum=0xbd86 src=1.1.1.1 dst=10.6.1.137 |<ICMP  type=echo-reply code=0 chksum=0x0 id=0x0 seq=0x0 |<Padding  load='\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00' |>>>)

🌞 dhcp_starvation.py