---
layout: post
author: Conde
---

## Índice
- [Netdiscover](#netdiscover)
- [Nmap]()
- [Bash]()
- [PowerShell]()

### Netdiscover
Podemos realizar un escaneo de la red, con esta herramienta, de la siguiente forma. 
```bash
netdiscover -i eth0
```

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
