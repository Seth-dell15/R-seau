# TP

```powershell
    🌞 Adresses IP de ta machine :

 ipconfig : 
Adresse IPv4. . . . . . . . . . . . . .: 10.33.78.236
 ipconfig /all :

    Carte Ethernet Ethernet :

    Statut du média. . . . . . . . . . . . : Média déconnecté
    Suffixe DNS propre à la connexion. . . :
    Description. . . . . . . . . . . . . . : Realtek PCIe GbE Family Controller
    Adresse physique . . . . . . . . . . . : 04-BF-1B-D5-82-4D


    🌞 Si t as un accès internet normal, d autres infos sont     forcément dispos...

 Carte réseau sans fil Wi-Fi :
    Passerelle par défaut. . . . . . . . . : 10.33.79.254
    Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
    Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254

    🌟 BONUS : Détermine s il y a un pare-feu actif sur ta machine: 

 PS C:\Users\hugoc> $FWService = (Get-Service | ?{$_.Name -eq "mpssvc"});
PS C:\Users\hugoc> $FWService | %{
>>     If($_.Status -eq "Running"){
>>         Write-Host "The $($_.DisplayName) service is running." -Foregroundcolor Green
>>         }Else{
>>         Write-Host "The $($_.DisplayName) service is stopped." -Foregroundcolor Red
>>         }
>>     };
The Pare-feu Windows Defender service is running.

    🌞 Envoie un ping vers...

ping  10.33.78.236

Envoi d une requête 'Ping'  10.33.78.236 avec 32 octets de données :
Réponse de 10.33.78.236 : octets=32 temps<1ms TTL=128
Réponse de 10.33.78.236 : octets=32 temps<1ms TTL=128
Réponse de 10.33.78.236 : octets=32 temps<1ms TTL=128
Réponse de 10.33.78.236 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.33.78.236:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms


ping 127.0.0.1

Envoi d une requête 'Ping'  127.0.0.1 avec 32 octets de données :
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms

    🌞 On continue avec ping. Envoie un ping vers...

ping 10.33.79.254

Envoi d une requête 'Ping'  10.33.79.254 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 10.33.79.254:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),

ping 10.33.76.111

Envoi d une requête 'Ping'  10.33.76.111 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 10.33.76.111:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),

ping www.google.com

Envoi d une requête 'ping' sur www.google.com [142.250.75.228] avec 32 octets de données :
Réponse de 142.250.75.228 : octets=32 temps=19 ms TTL=116
Réponse de 142.250.75.228 : octets=32 temps=16 ms TTL=116
Réponse de 142.250.75.228 : octets=32 temps=17 ms TTL=116
Réponse de 142.250.75.228 : octets=32 temps=17 ms TTL=116

Statistiques Ping pour 142.250.75.228:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 16ms, Maximum = 19ms, Moyenne = 17ms

    🌞 Faire une requête DNS à la main

PS C:\Users\hugoc> nslookup
Serveur par dÚfaut :   dns.google
Address:  8.8.8.8

PS C:\Users\hugoc> nslookup www.thinkerview.com
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.thinkerview.com
Addresses:  2a06:98c1:3121::7
          2a06:98c1:3120::7
          188.114.97.7
          188.114.96.7

PS C:\Users\hugoc> nslookup www.wikileaks.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    wikileaks.org
Addresses:  80.81.248.21
          51.159.197.136
Aliases:  www.wikileaks.org

nslookup www.torproject.org
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.torproject.org
Addresses:  2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
          2a01:4f9:c010:19eb::1
          2a01:4f8:fff0:4f:266:37ff:feae:3bbc
          2620:7:6002:0:466:39ff:fe7f:1826
          2620:7:6002:0:466:39ff:fe32:e3dd
          116.202.120.166
          95.216.163.36
          204.8.99.146
          204.8.99.144
          116.202.120.165
````
### 🌞 J attends dans le dépôt git de rendu un fichier ping.pcap

[Tous mes ping](./ping.pcapng)

### 🌞 Livrez un deuxième fichier : dns.pcap

[Tous mes ping dns](./dns.pcapng)

```powershell

    🌞 Effectue un scan du réseau auquel tu es connecté

nmap.exe -sn -PR 10.33.64.0/20

MAC Address: 7C:5A:1C:D3:D8:76 (Sophos)
Nmap scan report for 10.33.78.236
Host is up.
Nmap done: 4096 IP addresses (503 hosts up) scanned in 150.75 seconds

    🌞 Changer d adresse IP

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::ba7c:509b:25ce:10c0%17
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.70.118
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254

```
