


## Router 1

```
enable
config terminal

hostname R1
banner motd $Unauthorized access is prohibited$

enable secret cisco
enable password class
line console 0
password cisco
login
line vty 0 15
password cisco
login

service password-encryption

interface gigabitEthernet0/0
ip address 192.168.1.1 255.255.255.0

interface serial0/0/0
ip address 192.168.12.1 255.255.255.252

interface serial0/0/1
ip address 192.168.13.1 255.255.255.252

copy running-config startup-config
```

## Router 2

```
enable
config terminal

hostname R2
banner motd $Unauthorized access is prohibited$

enable secret cisco
enable password class
line console 0
password cisco
login
line vty 0 15
password cisco
login

service password-encryption

interface gigabitEthernet0/0
ip address 192.168.2.1 255.255.255.0

interface serial0/0/0
ip address 192.168.12.2 255.255.255.252

interface serial0/0/1
ip address 192.168.23.1 255.255.255.252

copy running-config startup-config
```

## Router 3

```
enable
config terminal

hostname R3
banner motd $Unauthorized access is prohibited$

enable secret cisco
enable password class
line console 0
password cisco
login
line vty 0 15
password cisco
login

service password-encryption

interface gigabitEthernet0/0
ip address 192.168.3.1 255.255.255.0

interface serial0/0/0
ip address 192.168.13.2 255.255.255.252

interface serial0/0/1
ip address 192.168.23.2 255.255.255.252

copy running-config startup-config
```