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
- [Nmap]()
- [Bash]()
- [PowerShell]()

### Tarjetas 
#### Sys
Enumeración a tráves de los ficheros de sys.
```bash
cat /sys/class/net
```
#### Nmcli
Enumeración a tráves de la herramienta nmcli.
- -t ➜ Oculta el nombre del campo seleccionado
- -f ➜ Campo a mostrar (Device, Type,State, Connection)
- c ➜ Abreviautra de connection 
- s ➜ Abreviautra de show 
- \--active ➜ Tarjetas en estado activo
```bash
nmcli -t -f DEVICE c s --active
```
#### Ip 
Enumeración a tráves del comando ip.
- -c ➜ Formato colorizado
- a ➜ Abreviatura de addr
```bash
ip -c a 
```
#### Ifconfig
Enumeración a tráves del comando ifconfig.
```bash
ifconfig
```

### Netdiscover
Podemos realizar un escaneo de la red, con la herramienta netdiscover de la siguiente forma.
- -i ➜ Nombre de la interfaz a escanear
```bash
netdiscover -i eth0
```

### Nmap 
Nmap, a parte de escanear puertos tambien nos permite identificar que dispositivos estan conectados a la red
- -sn ➜ Deshabilitamos el modo escaneo de puerto y solo descubre equipos conectados
```bash
nmap -sn 192.168.0.0/24
```
Tambien podemos agregar el siguiente parametro, que es más seguro y evitamos que nos hagan spoofing. 
- -PS ➜ Este manda un paquete por defecto al puerto 80, para verficar con tasa de acierto que el pc esta activo
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
#!/usr/bin/pwsh
#Autor: Jose Conde

#Main
1..254 | ForEach-Object -Parallel {
    $status = Test-Connection 192.168.0.$_ -count 1 -Quiet 
    
    if ($status)
    {
        Write-Host "[!] Equipo: 192.168.0.$_" -ForegroundColor Yellow -NoNewline; Write-Host " - Encendido"  -ForegroundColor Green
    }
} -ThrottleLimit 100
```
