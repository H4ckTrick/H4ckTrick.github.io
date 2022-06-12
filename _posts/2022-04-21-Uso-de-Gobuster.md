---
layout: post
author: Conde
---

## Índice
- [Definición](#definición)
- [Parametros](#parametros)
- [Uso de Gobuster](#uso)

### Definición 
Gobuster es una herramienta de enumeración a traves de fuerza bruta, que nos permite buscar directorios es un dominio, 
enumeración de dns, enumeración de virtual host, etc. 

### Parametros 
- **-u** → Indicamos el dominio o la ip 
- **-w** → Indicamos el diccionario 
- **-x** → indicamos extensiones (-x html, php, etc)
- **-t** → Indicamos los hilos (Defecto: 10)
- **-r** → Aplica dirección
- **-n** → Oculta el código de respuesta
- **-q** → Oculta el banner 
- **-o** → Exportamos resultado 
- **-s** → Indicamos solos los códigos que queremos (200,300,401)
- **-e** → Devuelve el path completo 
- **-U** y **-P** → Podemos indicar usuarios y contraseña (User and Password)
- **-d** → Indicamos el dominio (Modo dns)

### Uso 
#### Busqueda de directorios en un servidor web 

```bash
gobuster dir -u http://192.168.0.11/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt 
```
#### Busqueda de directorios y documentos con hilos

```bash
gobuster dir -u http://192.168.0.11/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html -t 200 
```

#### Exportación de evidencias 
```bash
gobuster dir -u http://192.168.0.11/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o Fuzzing.txt
```
#### Búsqueda de subdominios 
```bash
gobuster vhost -u http://h4cktrick.com/ -w /usr/share/wordlists/subdomains.txt -t 100 -o SubDomains.txt 
```
