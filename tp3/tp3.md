```powershell

☀️ Avant de continuer...

Wi-Fi      10-91-D1-24-98-E8

☀️ Affichez votre table ARP

Get-NetNeighbor

ifIndex IPAddress                                          LinkLayerAddress      State       PolicyStore
------- ---------                                          ----------------      -----       -----------
7       ff15::efc0:988f                                    33-33-EF-C0-98-8F     Permanent   ActiveStore
7       ff02::1:ff9c:4d                                    33-33-FF-9C-00-4D     Permanent   ActiveStore
7       ff02::1:ff74:9600                                  33-33-FF-74-96-00     Permanent   ActiveStore
7       ff02::1:3                                          33-33-00-01-00-03     Permanent   ActiveStore
7       ff02::1:2                                          33-33-00-01-00-02     Permanent   ActiveStore
7       ff02::fb                                           33-33-00-00-00-FB     Permanent   ActiveStore
7       ff02::16                                           33-33-00-00-00-16     Permanent   ActiveStore
7       ff02::2                                            33-33-00-00-00-02     Permanent   ActiveStore
7       ff02::1                                            33-33-00-00-00-01     Permanent   ActiveStore

☀️ Déterminez l'adresse MAC de la passerelle du réseau de l'école

Adresse physique . . . . . . . . . . . : 10-91-D1-24-98-E8

☀️ Supprimez la ligne qui concerne la passerelle

 Remove-NetNeighbor -InterfaceIndex 17 -IPAddress 10.33.79.254

☀️ Prouvez que vous avez supprimé la ligne dans la table ARP

17      10.33.79.254                                       00-00-00-00-00-00     Unreachable ActiveStore

☀️ Wireshark
```
[arp1.pcap](./arp1.pcap)

☀️ Déterminer

Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.4(préféré)
Adresse physique . . . . . . . . . . . : 10-91-D1-24-98-E8

☀️ DIY

Adresse IPv4. . . . . . . . . . . . . .: 172.20.10.7

☀️ Pingz !

ping 172.20.10.9

Envoi d’une requête 'Ping'  172.20.10.9 avec 32 octets de données :
Réponse de 172.20.10.9 : octets=32 temps=480 ms TTL=128
Réponse de 172.20.10.9 : octets=32 temps=17 ms TTL=128
Réponse de 172.20.10.9 : octets=32 temps=4 ms TTL=128
Réponse de 172.20.10.9 : octets=32 temps=32 ms TTL=128

Statistiques Ping pour 172.20.10.9:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 4ms, Maximum = 480ms, Moyenne = 133ms

☀️ Affichez votre table ARP !

[pingco.pcap](./pingco.pcap)

Il ne s'agit pas de mes pings mon powershell me mettait défaillance générale quand je faisait des pings.

☀️ Capture arp2.pcap


