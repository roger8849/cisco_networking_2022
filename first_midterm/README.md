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
## Enable config terminal mode
[---back to top---](#table-of-contents)
```
enable
config terminal
```

## Change device name
[---back to top---](#table-of-contents)
```
hostname Device_A
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
interface vlan 100
description IP ADMINISTRACION Device_A
ip address 70.0.0.2 255.0.0.0
no shutdown
ip default-gateway 70.0.0.1

interface vlan 100
description IP ADMINISTRACION Device_B
ip address 70.0.0.3 255.0.0.0
no shutdown
ip default-gateway 70.0.0.1

interface vlan 100
description IP ADMINISTRACION Device_C
ip address 70.0.0.4 255.0.0.0
no shutdown
ip default-gateway 70.0.0.1

interface vlan 100
description IP ADMINISTRACION Device_D
ip address 70.0.0.5 255.0.0.0
no shutdown
ip default-gateway 70.0.0.1
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

interface fastEthernet 0/16
description CONECTA A Device_D - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

interface fastEthernet 0/21
description CONECTA A Device_D - Puerto TRUNK
switchport mode trunk
switchport trunk allowed vlan 21,22,23,24,100,999
switchport trunk native vlan 999
no shutdown

```

