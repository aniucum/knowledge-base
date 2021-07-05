- altlinux.org/Etcnet

- меняем hostname
```bash
/etc/sysconfig/network
  ```

systemctl reboot


/etc/net/ifaces/eth0/options

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

### Настройка ifplugd. Демон, который поднимает интерфейс при подключении кабеля.
- etcnet сам может конфигуририровать интерфейс, поэтому `ifplugd` вырубаем, а в `options` добавляем переменную `USE_IFPLUGD`
```bash
chkconfig ifplugd off
```
vi /etc/net/ifaces/eth0/options
```bash
USE_IFPLUGD=yes или USE_IFPLUGD=auto
```
