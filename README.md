# netops-arsenal
Commandes diverses pour du debug réseau (et un peu système)

## Stormshield Network Security


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
