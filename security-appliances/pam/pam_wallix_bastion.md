# Wallix Bastion
Quelques commandes utiles sur la solution PAM Wallix Bastion.
## Réplication SQL

Vérifier l'état de la réplication SQL :
```
bastion-replication --monitoring
```
```
bastion-replication --status
```

Resynchroniser les esclaves avec le maître :
```
bastion-replication --resync
```
Stopper/démarrer la réplication SQL :
```
bastion-replication --stop
```
```
bastion-replication --start
```
