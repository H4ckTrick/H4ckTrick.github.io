---
layout: post
author: Conde
---

## Índice
- [Instalación](#instalación)
- [Parametros](#parametros)
- [Uso de NMAP](#uso)

### Instalación
En Debian, Ubuntu y derivadas
```bash
sudo apt-get install -y nmap
```
En CentOS, RHEL y derivadas
```bash
sudo yum install -y nmap
```
En Arch y derivdas
```bash
sudo pacman -Sy nmap
```

### Parametros
- **-sT** ➜ Escaneo TCP
- **-sU** ➜ Escaneo UDP
- **-sY** ➜ Escaneo SCTP
- **-sS** ➜ Escaneo TCP/SYN
- **-sn** ➜ Solo hace descrubrimiento de red
- **-Pn** ➜ Deshablita la resolución ARP
- **-n** ➜ Quita la resolción DNS
- **-PS** ➜ Envia un paquete TCP SYN a un puerto (Por defecto el 80)
- **\--top-port** ➜ Escaneo los top ports 
- **\--open** ➜ Solo muestra puertos abiertos
- **-f** ➜ Fragmenta las cabezeras (Bypass Firewall)
- **-mtu** ➜ Fragmenta las cabezeras igual ()
- **-D** ➜ Permite falsificar la ip que hace el escaneo 
- **-S** ➜ Falsificación de 
- **\--source-port** ➜ Falsificar el puerto que envia el paquete
- **\--min-rate** ➜ Permite indicar la velocidad de los paquetes
- **-T** ➜ Permite modificar la plantilla de temporizado 
- **-sV** ➜ Detención de versión de lo servicios
- **-sC** ➜ Uso de script básicos de nmap 
- **-O** ➜ Detención de S.O 
- **-p** ➜ Indicamos el puerto a escaneo (- indica todos)
- **-oX, oG, oN** ➜ Guardamos el resultado del comando
- **-v** ➜ Verbose

###  Uso 

#### Evasión de Firewall, IDS ... 
Vemos un primer ejemplo de evasión. 
- **-ff** y **-mtu 16** es lo mismo
- **ME** indica que es nuestro equipo quien hace el escaneo 

```bash
nmap --top-port 100 --open --mtu 16 -D 192.168.20.10, 192.168.20.11, ME -sS -n -Pn 192.168.20.100
```
#### Escaneo rápido para nuestro entorno 

```bash 
nmap -p- --open --min-rate 5000 -n -Pn -sS 192.168.20.100
```
#### Descubrir equipos de nuestra red

```bash 
nmap -sn -PS 443 192.168.20.0/24
```
#### Detectar servicios, versión ... 
- -sCV ➜ Fusión de parámetros **-sC** y **-sV**

```bash 
nmap -O -SCV 192.168.20.0/24
```
