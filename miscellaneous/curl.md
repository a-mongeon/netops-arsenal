# Curl

Quelques paramètres utiles pour Curl

## Récupérer une ressource HTTP avec Curl en spécifiant l'entête Host
```
curl https://www.domain.com/index.html -H 'Host: www.domain.com'
```
## Envoyer de multiples entêtes
```
curl https://www.domain.com/index.html -H 'Host: www.domain.com' -H 'Content-Type: application/json' -H 'Custom-Header: example'
```
## Récupérer seulement les entêtes HTTP
```
curl -I https://www.domain.com/index.html
```
## Désactiver la vérification TLS
```
curl -k https://www.domain.com/index.html
```
