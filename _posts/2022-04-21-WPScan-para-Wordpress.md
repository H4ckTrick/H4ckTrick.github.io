---
layout: post
author: Conde
---

## Índice
- [Definición](#definición)
- [Parametros](#parametros)
- [Uso de WPScan](#uso)

### Definición 
WPScan, es una herramienta que nos permite hacer una enumeración completa de WordPress.

### Parametros 
- **--url** ➜ Indicamos la url de la web
- **-e** o **\--enumeration** ➜ modo de enumeración
- **\--username** ➜ Indicamos nombre de usuario
- **-w** ➜ Wordlist a usar 
- **\--disable-tls-checks** ➜ Deshabilitar uso de SSL 
- **\--random-agent** ➜ Bypass a firewall 
- **\--no-banner** ➜ No muestra el banner 
- **\--stealthy** ➜ Este modo usa \--ramdon-user-agent, \--detention-mode y \--plugins-version-detection

### Uso 
#### Enumeración básica de wordpress

```bash 
wspcan --url http://prueba.com 
```

#### Enumeración de usuarios 
Dentro del modo de enumeración tenemos varios usos:
- vp ➜ Plugins vulnerables 
- ap ➜ Todos los plugins
- p ➜ Plugins populares
- vt ➜ Temas vulnerables
- at ➜ Todos los temas 
- t ➜ Temas populares 
- tt ➜ Timthums
- cb ➜ Backups
- dbe ➜ bases de datos
- u ➜ Usuarios
- m ➜ Media 

```bash 
wspcan --url http://prueba.com --no-banner -e u 
```

#### Fuerza bruta para usuarios

```bash 
wpscan -u http://prueba.com --username admin -w /usr/share/wordlists/rockyou.txt
```

#### Fuerza bruta haciendo bypass de firewall 
Este tipo de fuerza bruta evitara que nos banee.
```bash 
wpscan -u http://prueba.com --username admin -w /usr/share/wordlists/rockyou.txt --random-agent 
```

