
задаём ip
```bash
echo 192.168.0.48/24 > /etc/net/ifaces/eth0/ipv4address
#второй интерфейс при его наличии
echo 10.0.2.148/24 >> /etc/net/ifaces/eth0/ipv4address
```
шлюз
```bash
echo default via 192.168.0.10 > /etc/net/ifaces/eth0/ipv4route
  ```
включаем интерфейс
```bash
ip link set eth0 up
  ```
перезапускаем сеть
```bash
service network restart
  ```

изменение IP, маски и шлюза командами ip addr {add|change|replace} ... и ip route { add | del | change }. Изменения не перманентны
```bash
ip addr replace 192.168.97.242/24 dev eth0
```
