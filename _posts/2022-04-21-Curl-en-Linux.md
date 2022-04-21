---
layout: post
author: Conde
---

## Índice
- [Definición](#definción)
- [Instalación](#instalación)
- [Parámetros](#párametros)
- [Pentesting con curl](#pentesting)

### Definción
Curl, es un comando que nos permite realizar peticiones a páginas web, subir o descargar archivos tantos de servidores
web como de servidores ftp, etc. 

### Instalación 
En Debian, Ubuntu y derivadas
```bash
sudo apt-get install -y curl
```
En CentOS, RHEL y derivadas
```bash
sudo yum install -y curl
```
En Arch y derivdas
```bash
sudo pacman -Sy curl
```
En Mac OS
```bash
brew install curl
```

### Párametros
- **-s o \--silent** ➜ Modo silencioso
- **-X o \--request** ➜ Nos permite realizar peticiones (Post y Get)
- **-L o \--location** ➜ Aplica redirección 
- **-w o \--write-out** ➜ Indicamos contenido a ver, por ejemplo mostrar el codigo de estado (-w "%{http_code}\n")
- **-K o \--insecure** ➜ No aplicamos certificado SSL 
- **-I o \--head** ➜ Vemos las cabezeras enviadas
- **-d o \--data** ➜ Nos permite enviar data a una dirección
- **-T o \--upload-file** ➜ Permite subir un archivo, por ejemplo a FTP
- **-o o \--output** ➜ Permite almacenar el output en un fichero, se puede redirigir al /dev/null, tambien se puede usar -O o el signo mayor '>'
- **-H o \--header** ➜ Permite enviar una cabezera personalizada
- **-U o \--user** ➜ Indicamos el usuario y contraseña (Por ejemplo si tenemos que loguearnos en FTP)
- **-A o \--user-agent** ➜ Permite modificar el User-Agent (Información sobre el navegador que usamos)
- **-x o \--proxy** ➜ Permite indicar la dirección de un proxy, para que el realize la petición 

#### Ejemplos
Ver codigo de estado de la página 
```bash
curl -L -s -w "%{http_code}\n" -o /dev/null http://h4cktrick.github.io
```
Ver cabezeras enviadas 
```bash
curl -I -L -s http://h4cktrick.github.io -o /dev/null
```
Subir archivo a ftp anonimo
```bash
curl -s -T "secret.txt" ftp://127.0.0.1 --user anonymous:null
```
Descargar un archivo 
```bash
curl -O /dev/null http://h4cktrick.github.io/script.py
```

### Pentesting
Ahora veremos pequeños scripts con curl, desarollados por mi, para realizar pentesting básico. 
```bash

```
