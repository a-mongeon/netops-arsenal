# Ubika WAAP
##
[Ressources supplémentaires](https://github.com/ubikasec/ubika-waap-extra/tree/main)

## Debugger un tunnel Ubika :
Dans une brique "User Log" :
Afficher le contenu d'un header :
```
Header : ${http.request.headers['Host']}
```
Ou
```
User-Agent : ${string_of(http.request.headers['User-Agent'])}
```
