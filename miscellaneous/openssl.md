# OpenSSL
Quelques commandes utiles à utiliser avec OpenSSL pour débugger du TLS ou gérer du certificat.
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
### Créer une clé privée et une demande de signature de certificat sous EDCSA
```
openssl ecparam -name prime256v1 -genkey -noout -out /etc/pki/tls/private/pk_JJMMAAAA.key
```
```
openssl req -new -key /etc/pki/tls/private/pk_JJMMAAAA.key -out /etc/pki/tls/certs/csr_JJMMAAAA.csr
```
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
### Lire une CRL :
```
openssl crl -inform DER -text -noout -in mycrl.crl
```
### Extraire des éléments d'un .p12 :
```
openssl pkcs12 -info -in INFILE.p12 -nodes
```
### Pour extraire la clé privée au format PEM :
```
openssl pkcs12 -in INFILE.p12 -out OUTFILE.key -nodes -nocerts
```
### Pour extraire la clé publique, concaténée avec la chaine de certification, au format PEM :
```
openssl pkcs12 -in INFILE.p12 -out OUTFILE.crt -nokeys
```
### Pour extraire la clé publique, sans la chaîne de certification : 
```
openssl pkcs12 -in INFILE.p12 -out OUTFILE.crt -nokeys -clcerts
```

### Vérifier la cohérence entre une clé privée, une demande de signature et un certificat basés sur RSA :
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
Comparer ensuite les hashs MD5 du modulus, qui doit être strictement identique.

### Vérifier la cohérence entre une clé privée et un certificat basés sur ECDSA :
Extraire la clé publique du certificat
```
openssl x509 -in certificat.pem -pubkey -noout > pub_cert.pem
```
Dériver la clé publique depuis la clé privée
```
openssl ec -in cle_privee.pem -pubout > pub_privee.pem
```
Comparer les deux fichiers (doit retourner aucune différence)
```
diff pub_cert.pem pub_privee.pem
```

### Récupérer le numéro de série d'un certificat :
```
openssl x509 -in CERTIFICATE_FILE -serial -noout
```
### Pour aller plus loin avec Powershell
#### Récupérer le numéro de série d'un lot de certificats :

```powershell
Get-ChildItem –Path ".\*.pem" | Foreach-Object { 
Write-Host "$($_.Name) :"
openssl x509 -in $_.FullName -serial -noout 
}
```
#### Récupérer la date de fin de validité d'un lot de certificats :
```powershell
Get-ChildItem -Path ".\*.pem" | Foreach-Object {
Write-Host "$($_.Name) :"
openssl x509 -in $_.FullName -enddate -noout
}
```
#### Récupérer la date de signature d'un lot de certificats :
```powershell
Get-ChildItem -Path ".\*.pem" | Foreach-Object {
Write-Host "$($_.Name) :"
openssl x509 -in $_.FullName -startdate -noout
}
```
#### Récupérer tous les SANs d'un lot de certificats :
```powershell
Get-ChildItem -Path ".\*.pem" | Foreach-Object {
Write-Host "$($_.Name) :"
openssl x509 -text -noout -in $_.FullName -certopt no_subject,no_header,no_version,no_serial,no_signame,no_validity,no_issuer,no_pubkey,no_sigdump,no_aux | Select-String -Pattern "DNS:"
Write-Host ""}
```
