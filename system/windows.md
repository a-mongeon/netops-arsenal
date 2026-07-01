# Windows 

## Active Directory
Récupérer un attribut d'un objet AD :
```powershell
(Get-LocalUser -name <name>).SID.Value
```
## Divers
### Exécuter un programme en tant que SYSTEM
Avec l'outil PsExec disponible dans les [PsTools](https://learn.microsoft.com/fr-fr/sysinternals/downloads/pstools), il est possible d'exécuter un processus en tant que SYSTEM :
```
psexec -i -s cmd.exe
```
### Calculer la somme de contrôle d'un fichier
```
certutil.exe -hashfile filename.iso SHA256
```
Et comparer :
```
type filename.iso.sha256
```
### Décoder un fichier encodé en base64
```
certutil -decode InFile OutFile
```
### Décoder un fichier encodé en hexadécimal
```
certutil -decodehex InFile OutFile
```
### Gérer les métriques des interfaces
#### Lister les métriques des interfaces :
```
netsh int ip show interface
```
#### Modifier métrique interface :
```
netsh int ip set interface interface="LAN CONNECTION NAME" metric=15
```
### Installer un package depuis PowerShell en tant qu'administrateur :
Pour installer un package en tant qu'administrateur et éviter des blocages éventuels sur des serveurs durcis, il est possible de passer par PowerShell :
```powershell
$pkg = ".\EverTrust WinHorizon.2.1.0.msi"
Start-Process msiexec -ArgumentList "/i `"$pkg`""
```
### Filtrer de manière avancée le journal Windows :
Il n'est pas possible de filtrer par défaut des évènements du journal Windows sur certains critères, comme celui de l'utilisateur par exemple. Il est en revanche possible de le faire par une requête XML :
```xml
<QueryList>
  <Query Id="0" Path="Security">
    <Select Path="Security">
      *[
        EventData[Data[@Name='LogonType']='2']
        and
        EventData[Data[@Name='TargetUserName']='john.doe']
        and
		EventData[Data[@Name='SubjectUserName']='john.doe']
		and
        System[(EventID='4624')]
      ] 
    </Select>
  </Query>
</QueryList>
```
### Tester une CRL sur Windows :
```
certutil -url http://www.cert.fnmt.es/crls/ARLFNMTRCM.crl
```
*Cliquer sur "Extraire" :*

<img width="520" height="339" alt="image" src="https://github.com/user-attachments/assets/310aedcf-fa9d-4452-ba35-6edaeacdc601" />

### Déchiffrer du trafic TLS
Pour déchiffrer du traffic TLS, il est nécessaire de créer une variable exportant la clé privée du navigateur, ce qui permet ensuite de déchiffrer le traffic avec WireShark par exemple :

<img width="620" height="291" alt="image" src="https://github.com/user-attachments/assets/95ade978-15e9-4dd5-9c78-51062b544723" />

