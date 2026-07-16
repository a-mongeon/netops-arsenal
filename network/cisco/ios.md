# Cisco Catalyst IOS
## Remettre à 0 la configuration d'une interface :
En mode config :
```
default interface GigabitEthernet x/0/x
```
## Mettre en place du port mirroring :
```
no monitor session 1
monitor session 1 source interface Gi1/0/17, Gi1/0/18, Gi2/0/17, Gi2/0/18
monitor session 1 destination interface Gi1/0/24 encapsulation replicate
end
```
> Testé sur des Catalyst 3650. Documentation disponible [ici](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst3650/software/release/3se/network_management/configuration_guide/b_nm_3se_3650_cg/b_nm_3se_3650_cg_chapter_0111.html).
.
## Divers
Envoyer un firmware :
```
pscp -scp <file> <user>@<IP_of_switch>:flash:<file>
```
