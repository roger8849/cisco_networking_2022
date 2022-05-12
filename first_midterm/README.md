# Midterm exam
# Table of contents

- [Midterm exam](#midterm-exam)
- [Table of contents](#table-of-contents)
- [Objectives](#objectives)
- [Switch Device_A](#switch-device_a)
- [Hub Device_B](#hub-device_b)
- [Switch Device_C](#switch-device_c)
- [Switch Device_D](#switch-device_d)
- [Switch Device_E](#switch-device_e)
- [Cisco commands](#cisco-commands)
  - [Misc](#misc)
  - [Enable config terminal mode](#enable-config-terminal-mode)
  - [Change device name](#change-device-name)
  - [Login banner](#login-banner)
  - [Enable secret](#enable-secret)
  - [Enable password](#enable-password)
  - [Enable console password](#enable-console-password)
  - [Enable VTY lines](#enable-vty-lines)
  - [Enable VLANs](#enable-vlans)
  - [Configure Switch Administration IP](#configure-switch-administration-ip)
  - [Configure fastEthernet ports to configured VLANs](#configure-fastethernet-ports-to-configured-vlans)
  - [Configure fastEthernet trunk ports](#configure-fastethernet-trunk-ports)
  - [Configure Spanning tree protocol STP](#configure-spanning-tree-protocol-stp)

# Objectives
[---back to top---](#table-of-contents)

Create VLAN Stuff

TODO



# Switch Device_A
[---back to top---](#table-of-contents)

Device_A full configuration

```
enable
config terminal

hostname Device_A

banner motd $Entorno Corporativo privado RED COLOMBIA FABRICA!...$

vlan 21
name CONTABILIDAD
exit
vlan 22
name EMPLEADOS
exit
vlan 23
name VENTAS
exit
vlan 24 
name VIP
exit
vlan 100
name MANAGEMENT
exit
vlan 999
name NATIVA
exit
```

# Hub Device_B
[---back to top---](#table-of-contents)

# Switch Device_C
[---back to top---](#table-of-contents)

# Switch Device_D
[---back to top---](#table-of-contents)

# Switch Device_E
[---back to top---](#table-of-contents)

# Cisco commands

## Misc
```
######## View/Write running configuration #########
show running-config
copy running-config startup-config

######## Show ip int brief ##############
show ip int brief

######## Show interfaces status #########
show interfaces status
```
## Enable config terminal mode
[---back to top---](#table-of-contents)
```
enable
config terminal
```

## Change device name
[---back to top---](#table-of-contents)
```
####### Device A #######
hostname Device_A

####### Device C #######
hostname Device_C

####### Device D #######
hostname Device_D

####### Device E #######
hostname Device_E
```
## Login banner
[---back to top---](#table-of-contents)
```
banner motd $Entorno Corporativo privado RED COLOMBIA FABRICA!...$
```
## Enable secret
[---back to top---](#table-of-contents)
```
enable secret cisco
```
## Enable password
[---back to top---](#table-of-contents)
```
enable password cisco1
```
## Enable console password
[---back to top---](#table-of-contents)
```
line console 0
password cisco
login
```
## Enable VTY lines
[---back to top---](#table-of-contents)
```
line vty 0 15
password cisco
login

service password-encryption
```
## Enable VLANs
[---back to top---](#table-of-contents)
```
vlan 21
name CONTABILIDAD
exit
vlan 22
name EMPLEADOS
exit
vlan 23
name VENTAS
exit
vlan 24 
name VIP
exit
vlan 100
name MANAGEMENT
exit
vlan 999
name NATIVA
exit
```

## Configure Switch Administration IP
[---back to top---](#table-of-contents)
```
############ Device A ##########
interface vlan 100
description IP ADMINISTRACION Device_A
ip address 70.0.0.2 255.0.0.0
no shutdown
ip default-gateway 70.0.0.1

############ Device B ##########
interface vlan 100
description IP ADMINISTRACION Device_B
ip address 70.0.0.3 255.0.0.0
no shutdown
ip default-gateway 70.0.0.1

############ Device C ##########
interface vlan 100
description IP ADMINISTRACION Device_C
ip address 70.0.0.4 255.0.0.0
no shutdown
ip default-gateway 70.0.0.1

############ Device D ##########
interface vlan 100
description IP ADMINISTRACION Device_D
ip address 70.0.0.5 255.0.0.0
no shutdown
ip default-gateway 70.0.0.1

############ Device E ##########
interface fastEthernet 0/0
ip address 10.0.0.1 255.0.0.0
no shutdown

interface fastEthernet 0/1
ip address 20.0.0.1 255.0.0.0
no shutdown

interface fastEthernet 1/0
ip address 30.0.0.1 255.0.0.0
no shutdown

interface fastEthernet 1/1
ip address 40.0.0.1 255.0.0.0
no shutdown

interface Ethernet 0/2/0
ip address 70.0.0.1 255.0.0.0
no shutdown

```

## Configure fastEthernet ports to configured VLANs
[---back to top---](#table-of-contents)
```
############ Device A ##########
interface fastEthernet 0/4
description CONECTA A PC-1 - VLAN CONTABILIDAD
switchport mode access 
switchport access vlan 21
no shutdown

interface fastEthernet 0/5
description CONECTA A PC-2 - VLAN EMPLEADOS
switchport mode access 
switchport access vlan 22
no shutdown

############ Device C ##########
interface fastEthernet 0/8
description CONECTA A PC-5 - VLAN VENTAS
switchport mode access 
switchport access vlan 23
no shutdown

interface fastEthernet 0/9
description CONECTA A SRV-6 - VLAN CONTABILIDAD
switchport mode access 
switchport access vlan 21
no shutdown

############ Device D ##########
interface fastEthernet 0/10
description CONECTA A SRV-7 - VLAN VIP
switchport mode access 
switchport access vlan 24
no shutdown

interface fastEthernet 0/11
description CONECTA A PC-8 - VLAN EMPLEADOS
switchport mode access 
switchport access vlan 22
no shutdown
```

## Configure fastEthernet trunk ports
[---back to top---](#table-of-contents)
```
############ Device A ##########
interface fastEthernet 0/12
description CONECTA A Device_B - Puerto TRUNK
switchport mode trunk 
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/13
description CONECTA A Device_C - Puerto TRUNK
switchport mode trunk 
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/14
description CONECTA A Device_D - Puerto TRUNK
switchport mode trunk 
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

############ Device B ##########

############ Device C ##########
interface fastEthernet 0/14
description CONECTA A Device_A - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/15
description CONECTA A Device_B - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/16
description CONECTA A Device_D - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/21
description CONECTA A Device_E - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/22
description CONECTA A Device_E - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/23
description CONECTA A Device_E - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/24
description CONECTA A Device_E - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface gigabitEthernet 0/1
description CONECTA A Device_E - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown


############ Device D ##########
interface fastEthernet 0/15
description CONECTA A Device_A - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/16
description CONECTA A Device_C - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

############ Device E ##########  DEVICE E es un 2811 con tarjetas nm-2e2w wic-1enet
interface fastEthernet 0/0
description CONECTA A Device_C - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/1
description CONECTA A Device_C - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 1/0
description CONECTA A Device_C - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 1/1
description CONECTA A Device_C - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface Ethernet 0/2/0
description CONECTA A Device_C - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown
```

## Configure Spanning tree protocol STP
[---back to top---](#table-of-contents)

CONTABILIDAD
21
EMPLEADOS
22
VENTAS
23
VIP
24
MANAGEMENT
100
NATIVA
999

```
##### ROOT Switch Device_D ######
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 21 priority 24576

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 22 priority 24577

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 23 priority 24578

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 24 priority 24579

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 100 priority 24580

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 999 priority 24581

##### SECONDARY ROOT Switch #######

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 21 priority 28672

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 22 priority 28673

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 23 priority 28674

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 24 priority 28675

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 100 priority 28676

spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 999 priority 28677

```
