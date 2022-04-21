---
layout: post
author: Conde
---

## Indice
- [Definición](#Definción)
- [Instalación](#Instalación)
- [Parámetros](#Párametros)
- [Alias](#Alias)

### Definción
Batcat, es un comando que nos permite visualizar el contenido de los ficheros de una forma más comoda, ya que reconoce
la sintaxis.

### Instalación 
```bash
sudo apt-get install -y batcat
```
### Párametros
- -l 
- --list-themes
- -L o --list-languajes
- -r o --line-range
- -n o --number
- -A o --show-all 

Si tenemos un script en ptyhon por ejemplo, podemos indicarle que el lenguaje que va a utilizar sea python, aun que lo coge por defecto en algunas ocasiones, cuando
lanzamos un curl por ejemplo no lo detecta.
```bash
batcat -l python script.py
```
### Alias
Como este comando es mucho mejor que cat, en mi opinión, lo que haremos en un alias permanente, para ello en nuestro fichero ~/.bashrc o ~/.zshrc agregamos.
lo siguiente
```bash
alias cat="batcat"
```
Hecho eso, cerramos nuestra terminal para aplicar cambios o ejecutamos el siguiente comando, con el fichero de tu shell correspondiente.
```bash
source ~/.zshrc
```



