---
layout: post
author: Conde
---

## Índice
- [Definición](#definción)
- [Instalación](#instalación)
- [Parámetros](#párametros)
- [Alias](#alias)
- [Cambiar el tema](#tema)
- [Posibles errores](#errores)

### Definción
Batcat, es un comando que nos permite visualizar el contenido de los ficheros de una forma más comoda, ya que reconoce
la sintaxis.

### Instalación 
En Debian, Ubuntu y derivadas
```bash
sudo apt-get install -y bat
```
En CentOS, RHEL y derivadas
```bash
sudo yum install -y bat
```
En Arch y derivdas
```bash
sudo pacman -Sy bat
```
En Mac OS
```bash
brew install bat
```

### Párametros
- **-l** ➜ Especificamos el lenguaje a utilizar
- **\--list-themes** ➜ Vemos los temas disponibles 
- **-L o \--list-languajes** ➜ Vemos los lenguajes disponibles a usar 
- **-r o \--line-range** ➜ Indicamos un rango de lineas a mostrar
- **-n o \--number** ➜ Muestra las lineas del fichero
- **-A o \--show-all** ➜ Muestra todo los caracteres (Imprimibles, como no imprimibles)

#### Ejemplos
Indicar lenguaje a utilizar
```bash
bat -l python script.py
```
Mostrar temas disponibles
```bash
bat --list-themes
```
Ver lenguajes disponibles
```bash
bat --list-languajes
```
Mostrar un rango de lineas 
```bash
bat -r 5:10 /etc/passwd
```
Mostrar número de linea 
```bash
bat -n /etc/passwd
```
Mostrar todos los caracteres 
```bash
bat -A /etc/passwd
```

### Alias
Como este comando es mucho mejor que cat, en mi opinión, lo que haremos en un alias permanente, 
para ello en nuestro fichero **~/.bashrc** o **~/.zshrc** agregamos el siguiente comando.
```bash
alias cat="bat"
```
Hecho eso, cerramos nuestra terminal para aplicar cambios o ejecutamos el siguiente comando, 
con el fichero de tu shell correspondiente.
```bash
source ~/.zshrc
```

### Tema
Cuando usamos el parametros **-L** o **\--list-themes**, no muestra todos los temas que tenemos para usar con batcat, si queremos
modificarlo por uno que nos guste más lo que debemos hacer es lo siguiente **(Hay dos formas)**.
#### Primera forma
Esta primera forma modificamos el tema con el propio comando batcat.
```bash
bat --theme=DarkNeon
```
#### Segunda forma
En esta segunda forma, hacemos lo mismo pero cambiando una variable de entorno que usa batcat.
```bash
export BAT_THEME="DarkNeon"
```
### Errores
Cuando intentamos instalar **bat** en nuestro sistemas nos puede dar diferentes errores.
- Error de dependencias ➜ Actualizar repositorios
- Error de paquete no encontrado ➜ En algunas versiones no es bat, es batcat 

Personalmente en Kali, Parrot siempre he usado **batcat**, ahora que uso arch es **bat**. 
