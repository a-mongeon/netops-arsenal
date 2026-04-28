# Windows 

## Active Directory

Lister les métriques des interfaces :
```bash
netsh int ip show interface
```
Modifier métrique interface :
```bash
netsh int ip set interface interface="LAN CONNECTION NAME" metric=15
```

Récupérer un attribut d'un objet AD :
```powershell
(Get-LocalUser -name <name>).SID.Value
```
## Divers
### Filtrer de manière avancée le journal Windows :
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
certutil -url http://cdp.arquus-defense.fr/prod.ca.revoke.arquus-defense.crl
```
*Cliquer sur "Extraire" :*
<img width="520" height="339" alt="image" src="https://github.com/user-attachments/assets/310aedcf-fa9d-4452-ba35-6edaeacdc601" />
