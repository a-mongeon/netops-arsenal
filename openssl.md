# OpenSSL

## TLS
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

<img width="954" height="710" alt="image" src="https://github.com/user-attachments/assets/d6537af4-d505-456e-8198-eb694abf6876" />

## Gestion de certificats
Afficher les informations d'un certificat :
```
openssl x509 -text -noout -in cert.pem
```
Vérifier une demande de signature :
```
openssl.exe req -text -noout -verify -in <file>.csr
```
