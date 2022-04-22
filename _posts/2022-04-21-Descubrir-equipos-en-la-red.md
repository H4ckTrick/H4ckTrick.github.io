---
layout: post
author: Conde
---

## Índice
- [Enumerar tarjetas de red](#Tarjetas)
  - [sys](#sys)
  - [nmcli](#nmcli)
  - [ip](#ip)
  - [ifconfig](#ifconfig)
- [Netdiscover](#netdiscover)
- [Nmap](#nmap)
- [Bash](#bash)
- [PowerShell](#powershell)

### Tarjetas 
#### Sys
Enumeración a tráves de los ficheros de sys.
```bash
cat /sys/class/net
```

#### Nmcli
Enumeración a tráves de la herramienta nmcli.
- -t ➜ Oculta el nombre del campo seleccionado.
- -f ➜ Campo a mostrar (Device, Type, State, Connection).
- c ➜ Abreviautra de connection.
- s ➜ Abreviautra de show.
- \--active ➜ Tarjetas en estado activo.

```bash
nmcli -t -f DEVICE c s --active
```
#### Ip 
Enumeración a tráves del comando ip.
- **-c** ➜ Formato colorizado.
- **a** ➜ Abreviatura de addr.
- **-br** ➜ brief

```bash
ip -c a | awk '{print $1}'
```
#### Ifconfig
Enumeración a tráves del comando ifconfig.
```bash
ifconfig
```

### Netdiscover
Podemos realizar un escaneo de la red, con la herramienta netdiscover de la siguiente forma.
- -i ➜ Nombre de la interfaz a escanear.

```bash
netdiscover -i eth0
```

### Nmap 
Nmap, a parte de escanear puertos tambien nos permite identificar que dispositivos estan conectados a la red
- -sn ➜ Deshabilitamos el modo escaneo de puertos y solo descubre equipos conectados.

```bash
nmap -sn 192.168.0.0/24
```
Tambien podemos agregar el siguiente parametro, que es más seguro y evitamos que nos hagan spoofing. 
- -PS ➜ Este manda un paquete por defecto al puerto 80, para verficar con tasa de acierto que el pc esta activo.

```bash
nmap -sn -PS 192.168.0.0/24
```

### Bash 
Podemos crearnos un pequeño script en bash, para identificar todos los equipos conectados a nuestra red.
```bash
#!/bin/bash
#Autor: Jose Conde

#Colours
Amarillo="\e[93m"
Normal="\e[m"
Verde="\e[32m"
Rojo="\e[91m"

#Exit ctrl + c 
trap ctrl_c INT

ctrl_c(){
	clear
	echo -e "${Amarillo}[-]${Rojo} Saliendo... ${Normal}"
	exit 1
}

echo -e "[*] Escaneando la red: ${Amarillo}192.168.0.0/24${Normal}"
for i in $(seq 2 254); do
	timeout 1 bash -c "ping -c1 192.168.0.$i" > /dev/null && echo -e "\t[*] Equipo 192.168.0.$i - Activo" &
done; wait
```

### PowerShell 
De la misma forma que hemos hecho antes, tambien podemos hacerlo en powershell.

```PowerShell 
#!/usr/bin/pwsh
#Autor: Jose Conde

#Main
1..254 | ForEach-Object -Parallel {
    $status = Test-Connection 192.168.0.$_ -count 1 -Quiet 
    
    if ($status)
    {
        Write-Host "[!] Equipo: 192.168.0.$_ - Activo" -ForegroundColor Green
    }
} -ThrottleLimit 100
```
