---
layout: post
author: Conde
---

## Indice
- [Definición](#definción)
- [Instalación](#instalación)
- [Parámetros](#párametros)
- [Alias](#alias)
- [Cambiar el tema](#tema)

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
- **-A o \--show-all** ➜ Muestra todo los carazteres (Imprimibles, como no imprimibles)

Si tenemos un script en ptyhon por ejemplo, podemos indicarle que el lenguaje que va a utilizar sea python, 
aun que lo coge por defecto en algunas ocasiones, cuando lanzamos un curl por ejemplo no lo detecta.
```bash
batcat -l python script.py
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

## Tema
Cuando usamos el parametros **-L** o **\--list-themes**, no muestra todos los temas que tenemos para usar con batcat, si queremos
modificarlo por uno que nos guste más lo que debemos hacer es lo siguiente **(Hay dos formas)**.
### Primera forma
Esta primera forma modificamos el tema con el propio comando batcat.
```bash
bat --theme=DarkNeon
```
### Segunda forma
En esta segunda forma, hacemos lo mismo pero cambiando una variable de entorno que usa batcat.
```bash
export BAT_THEME="DarkNeon"
```
