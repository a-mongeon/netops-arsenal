# Stormshield Network Security

* VPN IPsec
* Gestion de certificats
  * Afficher les routes
  * Obtenir la route pour une adresse IP en particulier
  * Filtrage
* Divers
 
## VPN IPsec

Pour réactiver toutes les politiques VPN IPSEC :
```
envpn -u
```
Pour débugger un tunnel VPN IPSEC :
```
swanctl -T
```
Forcer le daemon *charon* de recharger la configuration :
```
swanctl --reload-settings
```
Voir les tunnels montés ou qui essayent de se monter :
```
showSAD
```
Vérifier si le daemon *charon* est lancé :
```
dstat charon
```

## Gestion de certificats
```
PKI REQUEST CREATE type=server cn=<common_name> C=<country> ST=<state> L=<city> O=<company> OU=<IT> shortname=mycertname keytype=<RSA|SECP|Brainpool> size=<256,384,512,521,1024,2048 ou 4096 bits>
```

## Réseau
### Afficher les routes  :
```
netstat -rn
```
### Obtenir la route pour une adresse IP en particulier :
```
route -n get 192.168.1.1
```
## Filtrage
Monitorer une connexion :
```
sfctl -s conn -nv -T -H host=1.1.1.1 -H port=4500
```
Lister le contenu de la blacklist :
```
sfctl -s addrlist
```

## Divers
Tester si le firewall peut joindre une adresse IP en particulier :
```
telnet 192.168.1.1 22
```
Tester si le firewall peut joindre une adresse IP en particulier (et forcer une adresse IP source) :
```
telnet -s 192.168.1.254 192.168.1.1 22
```
Voir la charge du firewall :
```
top -CHPS
```
Voir la charge du firewall :
```
sfctl -s proaddr
```
Vérifier les adresses protégées :
```
sfctl -s protaddr
```
Forcer la récupération d'une CRL :
```
checkcrl -d -t 10
```
Forcer une interface en particulier pour le Syslog (depuis Serverd):
```
CONFIG COMMUNICATION SYSLOG PROFILE UPDATE index=0 BindAddr=Firewall_in
```


Pour une résolution d'un nom de domaine :
```
objectsync -4 -t google.com
```
