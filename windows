# Windows 

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
