---
layout: post
author: Conde
---

## Índice
- [Enumerar tarjetas de red](#Tarjetas)
  - sys
  - nmcli
  - ip 
  - ifconfig
- [Netdiscover](#netdiscover)
- [Nmap]()
- [Bash]()
- [PowerShell]()

### Tarjetas 
#### Sys
```bash
cat /sys/class/net
```
#### Nmcli
- -t ➜ Oculta el nombre del campo seleccionado
- -f ➜ Campo a mostrar (Device, Type,State, Connection)
- c ➜ Abreviautra de connection 
- s ➜ Abreviautra de show 
- \--active ➜ Tarjetas en estado activo
```bash
nmcli -t -f DEVICE c s --active
```
#### Ip 
- -c ➜ Formato colorizado
- a ➜ Abreviatura de addr
```bash
ip -c a 
```
#### Ifconfig
```bash
ifconfig
```

### Netdiscover
Podemos realizar un escaneo de la red, con la herramienta netdiscover de la siguiente forma.
```bash
netdiscover -i eth0
```
El parametro **-i** indica la interfaz de red que debemos usar. Para ver nuestras tarjetas podemos usar, los siguientes comandos. 

### Nmap 
Nmap, a parte de escanear puertos tambien nos permite identificar que dispositivos estan conectados a la red
```bash
nmap -sn 192.168.0.0/24
```
Tambien podemos agregar el siguiente parametro. 
```bash
nmap -sn -PS 192.168.0.0/24
```

### Bash 
Podemos crearnos un pequeño script en bash, para identificar todos los equipos conectados a nuestra red 
```bash

```

### PowerShell 
De la misma forma que hemos hecho antes, tambien podemos hacerlo en powershell
```PowerShell 
Test-Conection 
```
