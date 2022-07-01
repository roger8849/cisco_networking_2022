


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

```