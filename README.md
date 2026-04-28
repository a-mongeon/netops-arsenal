# netops-arsenal
Commandes diverses pour du debug réseau (et un peu système)

## OpenSSL

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
