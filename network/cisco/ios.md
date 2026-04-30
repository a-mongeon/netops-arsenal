# Cisco Catalyst IOS
## Remettre à 0 la configuration d'une interface :
En mode config :
```
default interface GigabitEthernet x/0/x
```
## Divers
Envoyer un firmware :
```
pscp -scp <file> <user>@<IP_of_switch>:flash:<file>
```
