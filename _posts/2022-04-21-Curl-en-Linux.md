---
layout: post
author: Conde
---

## Índice
- [Definición](#definción)
- [Instalación](#instalación)
- [Parámetros](#párametros)
- [Pentesting con curl](#pentesting)
  - [Descubrimiento de directorios y archivos](#fuzzing)
  - [Descubrimiento de subdominios](#subdominios)


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
En Arch y derivadas
```bash
sudo pacman -Sy curl
```
En Mac OS
```bash
brew install curl
```

### Párametros
- **-s o \--silent** ➜ Modo silencioso
- **-X o \--request** ➜ Nos permite realizar peticiones
- **-L o \--location** ➜ Aplica redirección 
- **-w o \--write-out** ➜ Indicamos contenido a mostrar
- **-K o \--insecure** ➜ No aplicamos certificado SSL 
- **-I o \--head** ➜ Vemos las cabezeras enviadas
- **-d o \--data** ➜ Nos permite enviar data a una dirección
- **-T o \--upload-file** ➜ Permite subir un archivo
- **-o o \--output** ➜ Permite almacenar el output
- **-H o \--header** ➜ Permite enviar una cabezera personalizada
- **-U o \--user** ➜ Indicamos el usuario y contraseña 
- **-A o \--user-agent** ➜ Permite modificar el User-Agent 
- **-x o \--proxy** ➜ Permite indicar la dirección de un proxy

#### Ejemplos
Ver codigo de estado de la página 
```bash
curl -L -s -w "%{http_code}\n" -o /dev/null http://h4cktrick.github.io
```
Ver cabezeras enviadas 
```bash
curl -I -L -s http://h4cktrick.github.io
```
Subir archivo a ftp anonimo
```bash
curl -s -T "secret.txt" ftp://127.0.0.1 --user anonymous:null
```
Descargar un archivo 
```bash
curl -O https://h4cktrick.github.io/script.py
```

### Pentesting
Ahora veremos pequeños scripts con curl, desarollados por mi, para realizar pentesting básico. 
#### Fuzzing
Este script para descubrir directorios y archivos, por defecto utiliza un dicionario situado en la ruta **/usr/share/rockyou.txt**. 
Para que funcione solo es necesario indicar el host **(-h)** y el diccionario **(-w)**.
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

#Parameters
while getopts "h:w:" opc; do
    case $opc in
        h) host=$OPTARG ;;
        w) dic=$OPTARG ;;
    esac
done
 
#Main
fuzz(){
echo -e "[+] Escaneando: ${Amarillo}$host${Normal}"
echo -e "[*] Dicionario: ${Amarillo}${dic-/usr/share/rockyou.txt}${Normal}\n"
for i in $(cat ${dic:-/usr/share/rockyou.txt}); do
    estado=$(curl -s -L -w "%{http_code}\n" http://$host/$i -o /dev/null &)
 
    if [[ $estado -eq 200 ]]; then
        echo -e "\t[*] ${Amarillo}$i${Normal} (Reply: ${Verde}$estado${Normal})"
    fi
    sleep 0.5
done }
 
#Help Panel
helpPanel(){
    echo -e "[?] Uso: $0 -h <host> -w <diccionary>"
    echo -e "\t-h) Host (ej. 127.0.0.1)"
    echo -e "\t-w) Diccionary (ej. /usr/share/worlist/rockyou.txt)"
    exit 0
}
 
#Arguments
[[ $# -eq 0 ]] && helpPanel || fuzz
```
#### Subdominios
Ahora con otro script muy sencillo vamos a descubrir subdominios de un dominio que le indiquemos por parametro.
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

if [ $1 ] && [ $2 ]; then
    echo -e "[!] Escaneando: ${Amarillo}$1${Normal}"
    echo -e "[!] Diccionario: ${Amarillo}$2${Normal}"
    for p in "http://" "https://"; do
        for host in $(cat $2); do
            subdomain=$(curl -s -L -w "%{http_code}\n" "$p$host.$1" -o /dev/null -k)
            if [[ subdomain -eq 200 ]]; then
                echo -e "\n\t[+] ${Verde}$p$host.$1${Normal}"
            fi
        done
    done
else
    echo -e "Uso $0 <domain> <dicionario>"
fi
```
