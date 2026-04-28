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
(Get-LocalUser -name a422350t).SID.Value
```
## Filtrer de manière avancée le journal Windows :
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
