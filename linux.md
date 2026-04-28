# Linux

## Ouvrir un port vers un serveur distant

```shell
cat < /dev/tcp/127.0.0.1/22
```

Tester une communication Syslog :
```shell
echo "<14>Test TCP syslog message" >> /dev/tcp/<target_hostname_or_ip_address>/514
```
## Tester si un port est ouvert :
```shell
curl -vv telnet://<ip>:<port>
```
Test communication UDP :
```shell
echo "<14>Test UDP syslog message" >> /dev/udp/<target_hostname_or_ip_address>/514
```
Test communication TCP :
```shell
echo "<14>Test TCP syslog message" >> /dev/tcp/<target_hostname_or_ip_address>/514
```
