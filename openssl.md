<img width="458" height="61" alt="image" src="https://github.com/user-attachments/assets/fc6f1b82-2bc5-4c0c-988c-622bfd680109" /><img width="538" height="18" alt="image" src="https://github.com/user-attachments/assets/bc37e069-9652-48c0-9eef-fc49ec58561c" /># OpenSSL

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
### Afficher les informations d'un certificat :
```
openssl x509 -text -noout -in cert.pem
```
### Vérifier une demande de signature :
```
openssl req -text -noout -verify -in <file>.csr
```
### Vérifier qu'un certificat est bien signé par une autorité de certification :
```
openssl verify -verbose -CAfile cacert.pem  server.crt
```
### Vérifier la cohérence entre une clé privée, un demande de signature et un certificat :
Vérifier une demande de signature :
```
openssl req -noout -modulus -in mycsr.csr | openssl md5
```
Vérifier un certificat :
```
openssl x509 -noout -modulus -in mycert.crt | openssl md5
```
Vérifier une clée privée :
```
openssl rsa -noout -modulus -in server.key | openssl md5
```
Comparer ensuite les hashs MD5.

## Récupérer le numéro de série d'un certificat :
```
openssl x509 -in CERTIFICATE_FILE -serial -noout
```
## Récupérer le numéro de série d'un lot de certificat (sur Windows) :

```powershell
Get-ChildItem –Path ".\*.pem" | Foreach-Object { 
Write-Host "$($_.Name) :"
openssl x509 -in $_.FullName -serial -noout 
}
```

