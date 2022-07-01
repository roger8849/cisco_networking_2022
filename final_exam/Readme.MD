
## Router 1

```
R1#sh running-config 
Building configuration...

Current configuration : 1285 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname R1
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
enable password 7 0822404F1A0A
!
no ip cef
no ipv6 cef
!
license udi pid CISCO1941/K9 sn FTX15242U23-
!
spanning-tree mode pvst
!
interface Loopback0
 ip address 1.1.1.1 255.255.255.255
!
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Serial0/0/0
 bandwidth 128
 ip address 192.168.12.1 255.255.255.252
 clock rate 128000
!
interface Serial0/0/1
 ip address 192.168.13.1 255.255.255.252
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 10
 router-id 11.11.11.11
 log-adjacency-changes
 passive-interface GigabitEthernet0/0
 network 192.168.1.0 0.0.0.255 area 0
 network 192.168.12.0 0.0.0.3 area 0
 network 192.168.13.0 0.0.0.3 area 0
!
ip classless
!
ip flow-export version 9
!
banner motd ^CUnauthorized access is prohibited^C
!
line con 0
 password 7 0822455D0A16
 login
!
line aux 0
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 password 7 0822455D0A16
 login
!
end
```

## Router 2

```
R2#sh running-config 
Building configuration...

Current configuration : 1232 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname R2
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
enable password 7 0822404F1A0A
!
no ip cef
no ipv6 cef
!
license udi pid CISCO1941/K9 sn FTX15248OAY-
!
spanning-tree mode pvst
!
interface Loopback0
 ip address 2.2.2.2 255.255.255.255
!
interface GigabitEthernet0/0
 ip address 192.168.2.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Serial0/0/0
 ip address 192.168.12.2 255.255.255.252
!
interface Serial0/0/1
 ip address 192.168.23.1 255.255.255.252
 clock rate 128000
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 10
 router-id 22.22.22.22
 log-adjacency-changes
 network 192.168.2.0 0.0.0.255 area 0
 network 192.168.12.0 0.0.0.3 area 0
 network 192.168.23.0 0.0.0.3 area 0
!
ip classless
!
ip flow-export version 9
!
banner motd ^CUnauthorized access is prohibited^C
!
line con 0
 password 7 0822455D0A16
 login
!
line aux 0
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 password 7 0822455D0A16
 login
!
end
```

## Router 3

```
R3#sh running-config 
Building configuration...

Current configuration : 1232 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname R3
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
enable password 7 0822404F1A0A
!
no ip cef
no ipv6 cef
!
license udi pid CISCO1941/K9 sn FTX1524XPAL-
!
spanning-tree mode pvst
!
interface Loopback0
 ip address 3.3.3.3 255.255.255.255
!
interface GigabitEthernet0/0
 ip address 192.168.3.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Serial0/0/0
 ip address 192.168.13.2 255.255.255.252
 clock rate 128000
!
interface Serial0/0/1
 ip address 192.168.23.2 255.255.255.252
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 10
 router-id 33.33.33.33
 log-adjacency-changes
 network 192.168.3.0 0.0.0.255 area 0
 network 192.168.13.0 0.0.0.3 area 0
 network 192.168.23.0 0.0.0.3 area 0
!
ip classless
!
ip flow-export version 9
!
banner motd ^CUnauthorized access is prohibited^C
!
line con 0
 password 7 0822455D0A16
 login
!
line aux 0
!
line vty 0 4
 password 7 0822455D0A16
 login
line vty 5 15
 password 7 0822455D0A16
 login
!
end
```