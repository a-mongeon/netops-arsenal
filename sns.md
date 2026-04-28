# Stormshield Network Security

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
Voir sir le daemon charon est lancé :
```
dstat charon
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
Voir la charge du firewall :
```
top -CHPS
```
Voir la charge du firewall :
```
sfctl -s proaddr
```
```
sfctl -s protaddr
```
Forcer la récupération d'une CRL :
```
checkcrl -d -t 10
```
Forcer une interface en particulier pour le Syslog (depuis le CLI):
```
CONFIG COMMUNICATION SYSLOG PROFILE UPDATE index=0 BindAddr=Firewall_in
```


Pour une résolution d'un nom de domaine :
```
objectsync -4 -t google.com
```
