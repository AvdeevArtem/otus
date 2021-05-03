
# VLAN
##  Задание:
1. [Базовая настройка устройств](https://github.com/AvdeevArtem/otus/tree/main/Network/Lab1.%20Vlan#1-%D0%B1%D0%B0%D0%B7%D0%BE%D0%B2%D0%B0%D1%8F-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-%D1%83%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%81%D1%82%D0%B2)
2. [Создание VLAN и конфигурирование портов коммутатора](https://github.com/AvdeevArtem/otus/tree/main/Network/Lab1.%20Vlan#2-%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D0%B5%D0%BC-vlan-%D0%B8-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B8%D1%80%D1%83%D0%B5%D0%BC-access-%D0%BF%D0%BE%D1%80%D1%82%D1%8B-%D0%BD%D0%B0-%D1%81%D0%B2%D0%B8%D1%82%D1%87%D0%B0%D1%85)
3. [Настройка trunk между коммутаторами](https://github.com/AvdeevArtem/otus/tree/main/Network/Lab1.%20Vlan#3-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B0%D1%86%D0%B8%D1%8F-trunk-%D0%BF%D0%BE%D1%80%D1%82%D0%BE%D0%B2-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-%D1%81%D0%B5%D1%82%D0%B5%D0%B2%D1%8B%D0%BC%D0%B8-%D1%83%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%81%D1%82%D0%B2%D0%B0%D0%BC%D0%B8)
4. [Настройка inter-Vlan routing на роутере](https://github.com/AvdeevArtem/otus/tree/main/Network/Lab1.%20Vlan#4-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D1%81%D0%B0%D0%B1-%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D1%84%D0%B5%D0%B9%D1%81%D0%BE%D0%B2-%D0%BD%D0%B0-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%82%D0%BE%D1%80%D0%B5-r1-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-inter-vlan-%D1%80%D0%BE%D1%83%D1%82%D0%B8%D0%BD%D0%B3%D0%B0)
5. [Проверка роутинга](https://github.com/AvdeevArtem/otus/tree/main/Network/Lab1.%20Vlan#4-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D1%81%D0%B0%D0%B1-%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D1%84%D0%B5%D0%B9%D1%81%D0%BE%D0%B2-%D0%BD%D0%B0-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%82%D0%BE%D1%80%D0%B5-r1-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-inter-vlan-%D1%80%D0%BE%D1%83%D1%82%D0%B8%D0%BD%D0%B3%D0%B0)

Таблица ip-адресов
| Device  | Interface  | IP Address  |  Subnet mask  | Default gateway |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| R1  | e0/0.3  | 192.168.3.1  |  255.255.255.0 | N/A |
|   |  e0/0.4 | 192.168.4.1  | 255.255.255.0 | |
|   | e0/0.8  | N/A | N/A | |
| S1  | VLAN 3 |  192.168.3.11 | 255.255.255.0 | 192.168.3.1 |
| S2  | VLAN3 | 192.168.3.12 | 255.255.255.0 | 192.168.3.1 |
| PC-A  | NIC | 192.168.3.3  | 255.255.255.0 | 192.168.3.1 |
| PC-B  | NIC | 192.168.4.3 | 255.255.255.0 | 192.168.4.1 |

Таблица VLAN
| VLAN | Name | Inteface Assigned |
|--------|--------|---------------------|
| 3 | Management | S1: VLAN 3, S2: VLAN 3, S1: e0/1 |
| 4 | Operations | S2: e0/1 |
| 7 | ParkingLot | All unused |
| 8 | Native | N/A|


 #### Схема сети
![Схема](https://github.com/AvdeevArtem/otus/blob/main/Network/Lab1.%20Vlan/VLAN.png)

### 1. Базовая настройка устройств
На всех устроствах необходимо настроить пароль для доступа через консоль, VTY и в привилигерованный режим, а так же настроить баннер.

Configure secret password for enable
```
(config)# enable secret PASSWORD
```

Configure password for console
```
(config)# line console 0
(config)# password PASSWORD
(config)# login
```

VTY
```
(config)# line vty 0 4 
(config)# password PASSWORD
(config)# login
```

Encrypt plaintext password
```
(config)# service  password-encryption
```

Configure Banner
```
Switch1(config)#banner motd #
Enter TEXT message. End with the character '#'.
This device is for authorized personnel only.
If you have not been provided with permission to
access this device - disconnect at once.
#
```

### 2. Создаем VLAN и конфигурируем access порты на свитчах
Суть задания в данном случае научиться создавать VLAN и привязывать их к определенным интерфейсам

Настраиваем VLAN на свитчах S1 и S2
```
(config)# vlan 3
(config)# name Management
(config)# vlan 4
(config)# name Operations
(config)# vlan 7
(config)# name ParkingLot
(config)# vlan 8
(config)# name Native
```

Просмотр информации о созданных VLAN
```
show vlan brief
```

Настраиваем менеджмент интерфейс VLAN3 для управления
**S1**
```
S1(config)# interface vlan 3
S1(config-if)# description Management
S1(config-if)# ip address 192.168.3.11 255.255.255.0
S1(config-if)# ip route 0.0.0.0 0.0.0.0 192.168.3.1
S1(config-if)# no shutdown
```

**S2**
```
S2(config)# interface vlan 3
S2(config-if)# description Management
S2(config-if)# ip address 192.168.3.12 255.255.255.0
S2(config-if)# ip route 0.0.0.0 0.0.0.0 192.168.3.1
S2(config-if)# no shutdown
```

Команды для проверки
```
show ip interface brief
```

Конфигурируем Access порты
**S1**
```
S1(config)# interface range ethernet 0/0 - 3
S1(config-if-range)# switchport mode access
S1(config-if-range)# switchport access vlan 7
S1(config-if-range)# shutdown
S1(config-if-range)# end
S1(config)# interface ethernet 0/1
S1(config-if)# description "PC-A"
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 3
S1(config-if)# no shutdown
```

**S2**
```
S2(config-if-range)# interface range ethernet 0/0 - 3
S2(config-if-range)# switchport mode access
S2(config-if-range)# switchport access vlan 7
S2(config-if-range)# shutdown
S2(config-if-range)# end
S2(config-if)# interface ethernet 0/1
S2(config-if)# description PC-B
S2(config-if)# switchport mode access
S2(config-if)# switchport access vlan 3
S2(config-if)# no shutdown
```
### 3. Конфигурация trunk портов между сетевыми устройствами

Конфигурация транковых портов на S1,S2
```
(config)# interface e0/3
(config-if)# description "to S1" or "to S2"
(config-if)# switchport trunk encapsulation dot1q
(config-if)# switchport trunk native vlan 8
(config-if)# switchport trunk allowed vlan 3,4,8
(config-if)# switchport mode trunk
(config-if)# no shutdown
```

Настраиваем транк между S1 и R1
**S1**
```
S1(config)# interface ethernet 0/0
S1(config-if)# description "to R1"
S1(config-if)# switchport trunk encapsulation dot1q
S1(config-if)# switchport trunk native vlan 8
S1(config-if)# switchport trunk allowed vlan 3,4,8
S1(config-if)# switchport mode trunk
S1(config-if)# no shutdown
```

Команды для проверки
```
show interface trunk
```

### 4. Конфигурирование саб-интерфейсов на маршрутизаторе R1. Настройка Inter-Vlan роутинга.
Пример настройки на маршрутизаторе **R1**. В этом примере создаются саб-интерфейсы для 3,4 и 8 вланов.
Перед тем как назначить адрес на интерфейс обязательно нужно включить инкапсуляцию для dot1q
```
R1(config)# interface ethernet 0/0
R1(config-if)# no shutdown
R1(config-if)# interface ethernet 0/0.3
R1(config-if)# description "Default gateway for VLAN 3"
R1(config-if)# encapsulation dot1Q 3
R1(config-if)# ip address 192.168.3.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# interface ethernet 0/0.4
R1(config-if)# description "Default gateway for VLAN 4"
R1(config-if)# encapsulation dot1Q 4
R1(config-if)# ip address 192.168.4.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# interface ethernet 0/0.8
R1(config-if)# description "Native VLAN 8"
R1(config-if)# encapsulation dot1Q 8
R1(config-if)# no shutdown
```


### 5. Проверка работы роутинга
#### PC-B trace и ping
```
PC-B> trace 192.168.3.3
trace to 192.168.3.3, 8 hops max, press Ctrl+C to stop
 1   192.168.4.1   0.522 ms  0.446 ms  0.465 ms
 2   *192.168.3.3   2.356 ms (ICMP type:3, code:3, Destination port unreachable)

PC-B> ping 192.168.3.3
84 bytes from 192.168.3.3 icmp_seq=1 ttl=63 time=0.967 ms
84 bytes from 192.168.3.3 icmp_seq=2 ttl=63 time=1.121 ms

PC-B> ping 192.168.3.12
84 bytes from 192.168.3.12 icmp_seq=1 ttl=254 time=0.991 ms
84 bytes from 192.168.3.12 icmp_seq=2 ttl=254 time=1.177 ms

PC-B> ping 192.168.3.11
84 bytes from 192.168.3.11 icmp_seq=1 ttl=254 time=1.425 ms
84 bytes from 192.168.3.11 icmp_seq=2 ttl=254 time=0.908 ms
```

