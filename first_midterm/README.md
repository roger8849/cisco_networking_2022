# Midterm exam
## Table of contents

- [Midterm exam](#midterm-exam)
  - [Table of contents](#table-of-contents)
  - [Objectives](#objectives)
  - [Cisco commands](#cisco-commands)
    - [Enable config terminal mode](#enable-config-terminal-mode)
    - [Login banner](#login-banner)
    - [Enable secret](#enable-secret)
    - [Enable password](#enable-password)
    - [Enable console password](#enable-console-password)
    - [Enable VTY lines](#enable-vty-lines)
    - [Enable VLANs](#enable-vlans)

## Objectives
Create VLAN Stuff

TODO

## Cisco commands
### Enable config terminal mode
```
enable
config terminal
```
### Login banner
```
banner motd $Entorno Corporativo privado RED COLOMBIA FABRICA!...$
```
### Enable secret
```
enable secret cisco
```
### Enable password
```
enable password cisco1
```
### Enable console password
```
line console 0
password cisco
login
```
### Enable VTY lines
```
line vty 0 15
password cisco
login

service password-encryption
```
### Enable VLANs
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

