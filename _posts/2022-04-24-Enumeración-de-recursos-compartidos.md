---
layout: post
author: Conde
---

## Índice
- [Definición](#definción)
- [Explicación](#explicación)
- [Enumeración de recursos](#enumeración)
  - [smbclient](#smbclient) 
  - [smbmap](#smbmap)
  - [nmap](#nmap)
  - [enum4linux](#enum4linux)
  - [crackmapexec](#crackmapexec) 
  - [rpcclient](#rpcclient)
  - [metasploit](#metasploit)

### Definición 
Cuando hablamos de enumeración de recursos compartidos, nos referimos como bien indica el nombre, a visualizar todos los recursos
compartidos en el equipo que vamos a realizar un test. Esto lo hacemos para encontrar toda la información posible sobre el equipo
que vamos a comprometer. 

### Explicación
Cuando compartimos recursos en la red utilizamos un procolo que recibe el nombre de **samba**, abreviado **smb**. Este protocolo utiliza
dos puertos: 
- **Puerto 139** ➜ En este puerto corre el protocolo **NetBIOS**, para comunicarse con la red. 
- **Puerto 445** ➜ En este puerto corre el protocolo **SMB**. 

**NetBIos**, es un protocolo de la capa de sesión del modelo OSI que es *independiente* de SMB. Pero a diferenencia **SMB**, *necesita* NetBIOS
para la comunicación con dispositivos que no admiten el alojamietno de smb sobre TCP/IP. Tambien podemos encontrarnos NetBIOS, corriendo en otros 
puertos proximos: 
- Puerto 137, 138 (UDP) 
- Puerto 137 (TCP) 

A mayores samba, a parte de compartir recursos en red, nos permite crear un controlador de dominio simulando AD DC. 
- Samba 3 ➜ Antes de la salida de samba-ad-dc (samba4) se utilizaba junto LDAP, para crear un dominio y podemos unir clientes windows y Linux 
- Samba 4 ➜ Con la salida de samba4, samba3 dejo de ser utilizado, samba4 tiene mucha potencia similar a AD, por lo que nos permite realizar todo, unir clientes windows y linux, uso de GPOS, relaciones de confianza, etc. 


### Enumeración 
#### Smbclient
Podemos comenzar haciendo una emueración de los recursos, con una sessión null con smbclient, de la siguiente forma.
- **-L** ➜ Lista los recursos
- **-N** ➜ Omite contraseña 

```bash
smbclient -L 192.168.10.123 -N 
```

#### Smbmap 
Tambien podemos usar esta herramienta, que ya es escpecializada en la enumeración de SMB.
- **-H** ➜ IP de objetivo
- **-u** ➜ Usuario (% usuario actual del sistema)

```bash
smbmap -H 192.168.10.123 -u%
```

#### Nmap 
- **-p** ➜ Indicamos puerto 
- **\--script** ➜ Indicamos el script a usar

```bash
nmap -p 139,445 --script smb-enum-shares 192.168.10.123
```

#### Enum4linux
- **-S** ➜ Listar recursos compartidos
- **-u** ➜ Indicar usuario
- **-p** ➜ Indicar contraseña 

```bash
enum4linux -S -u -p 192.168.10.123
```

#### Crackmapexec
- -u ➜ Usuarios
- -p ➜ Contraseña 
- \--shares ➜ Enumerar recursos
```bash
crackmapexec smb 192.168.10.123 -u '' -p '' --shares
```

#### Rpcclient 
- **-U** ➜ Indicamos usuario
- **-c** ➜ Comando de rpcclient a ejecutar

```bash
rpcclient -U '' 10.10.11.152  -c "netshareenum"
```

#### Metasploit 
Como explicamos en otro post, hacemos los mismos pasos que siempre. 
1. msfconsole
2. use auxiliary/scanner/smb/smb_enumshares 
3. set rhosts 192.168.10.123
4. exploit

```bash
use auxiliary/scanner/smb/smb_enumshares 
set rhosts 192.168.10.123
exploit
```
