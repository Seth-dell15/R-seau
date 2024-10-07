```powershell
🌞 Prouvez que votre configuration est effective

Get-NetIPAddress -InterfaceAlias "Ethernet"


IPAddress         : fe80::539a:66ab:d7b5:6fca%11
InterfaceIndex    : 11
InterfaceAlias    : Ethernet
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 10.111.222.223
InterfaceIndex    : 11
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

🌞 Tester que votre LAN + votre adressage IP est fonctionnel

 ping 10.111.222.202

Envoi d une requête 'Ping'  10.111.222.202 avec 32 octets de données :
Réponse de 10.111.222.202 : octets=32 temps=2 ms TTL=128
Réponse de 10.111.222.202 : octets=32 temps=4 ms TTL=128
Réponse de 10.111.222.202 : octets=32 temps=4 ms TTL=128
Réponse de 10.111.222.202 : octets=32 temps=4 ms TTL=128

Statistiques Ping pour 10.111.222.202:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 2ms, Maximum = 4ms, Moyenne = 3ms

```
🌞 Capture de ping

[Ping.pcapng](./ping.pcapng)

🌞 Sur le PC serveur

./nc64.exe -l -p 3333

🌞 Sur le PC serveur toujours

netstat -a -b -n

Connexions actives

 TCP    0.0.0.0:3333           0.0.0.0:0              LISTENING
 [nc64.exe]

🌞 Sur le PC client

.\nc64.exe 10.111.222.202 9999

🌞 Echangez-vous des messages

.\nc64.exe 10.111.222.202 9999
cc
bonsoir sale
gentil
???
ta du ping
toi meme
oui
99999999ms

🌞 Utilisez une commande qui permet de voir la connexion en cours

netstat -an | findstr 9999
  TCP    10.111.222.202:9999    10.111.222.223:39962   ESTABLISHED

🌞 Faites une capture Wireshark complète d'un échange

[netcat1](./netcat1.pcapng)

🌞 Inversez les rôles

[netcat2](./netcat2.pcapng)

🌞 Utilisez Wireshark pour capturer du trafic HTTP

[Mon site http](./wirehttp.pcapng)

🌞 Pour les 5 applications

[Opera](./opera.pcap)

[Discord](./discord.pcapng.)

[Opera2](./Opera2.pcap)

[Opera3](./opera3.pcap)

[Opera4](./opera4.pcap)

