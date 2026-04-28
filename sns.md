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
