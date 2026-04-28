# NetOps Arsenal
Commandes diverses pour du debug réseau (et un peu système)

## Stormshield Network Security
* [Commandes relatives à la gestion/debug du VPN IPsec](https://github.com/a-mongeon/netops-arsenal/blob/main/README.md#vpn-ipsec).
* [Commandes relatives à la gestion/debug du filtrage](https://github.com/a-mongeon/netops-arsenal/blob/main/README.md#filtrage).

### VPN IPsec

Pour réactiver toutes les politiques VPN IPSEC :
```
envpn -u
```
Pour débugger un tunnel VPN IPSEC :
```
swanctl -T
```
Forcer le daemon charon to recharger la conf :
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

### Filtrage
Monitorer une connexion :
```
sfctl -s conn -nv -T -H host=188.231.45.9 -H port=4500
```
Lister le contenu de la blacklist :
```
sfctl -s addrlist
```
Forcer la récupération d'une CRL :
```
checkcrl -d -t 10
```
### Divers
Voir la charge du firewall :
```
top -CHPS
```
Voir la charge du firewall :
```
sfctl -s proaddr
```

sfctl -s protaddr
Afficher les routes  :
netstat -rn

Forcer une interface en particulier pour le Syslog
CONFIG COMMUNICATION SYSLOG PROFILE UPDATE index=0 BindAddr=Firewall_RRA-EXT



Pour une résolution d'un nom de domaine :
objectsync -4 -t google.com

## OpenSSL

### Afficher les SAN avec OpenSSL d'un serveur :
```bash
openssl s_client -connect website.example:443 </dev/null 2>/dev/null | openssl x509 -noout -text | grep DNS:
```

### Faire des requêtes HTTP avec un serveur web :

```bash
openssl s_client -connect website.example:443 -host <hostname.com>
```
*Une fois la connexion TLS établie :* 

```
GET / HTTP/1.1 <Entrée>
Host: <hostname.com> <Entrée>
<Entrée>
```
