# Linux

### Tester/Ouvrir un port vers un serveur distant :
#### Avec cat et les sockets :
```shell
cat < /dev/tcp/127.0.0.1/22
```
<img width="469" height="43" alt="image" src="https://github.com/user-attachments/assets/f6e5f9f5-545b-4cc6-9eb3-3c7bf6cc70b6" />

#### Avec curl :
```shell
curl -vv telnet://<ip>:<port>
```
### Tester une communication Syslog :
```shell
echo "<14>Test TCP syslog message" >> /dev/tcp/<target_hostname_or_ip_address>/514
```
Test communication UDP :
```shell
echo "<14>Test UDP syslog message" >> /dev/udp/<target_hostname_or_ip_address>/514
```
Test communication TCP :
```shell
echo "<14>Test TCP syslog message" >> /dev/tcp/<target_hostname_or_ip_address>/514
```
