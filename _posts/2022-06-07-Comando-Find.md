---
layout: post
author: Conde
---

## Índice
- [Definición](#definción)
- [Parámetros](#parámetros)


### Definión 
Find, es un comando que nos permite realizar búsquedas de ficheros, directorios, enlaces y demás de una forma rapida. Este comando es muy potente, ya que nos permite realizar acciones sobre salidas de ficheros buscados, eliminar directorios vacios, patrones de busqueda, etc. 


### Parámetros 
- -name o -iname → Indicamos el nombre del fichero a buscar (-iname )
- -exec → comando a ejecutar para el recurso encontrado (Necesita usar {} \;)
- -user → Indicas el usuario al que pertenece el recurso
- -group → Indicas el grupo al que pertenece el recurso
- -print → Imprime por pantalla el resultado
- -mtime → 
- -size → Indica el tamaño del recurso
- -delete → Elimina el recurso de salida  
- -readable → Muestra el recurso que tenga el permiso de lectura
- -writable → Muestra el recurso que tenga el permiso de escritura
- -executable → Muestra el recurso que tenga el permiso de ejeccución
- -type → Tipo del recurso
- -perm → Permisos que debe tener el recurso
- -and, -a y -not, -or →

#### Tablas
Dentro del parámetro -type, podemos encontrar los siguientes tipos. 
| Tipo | Letra |
| --- | --- | 
| b | Bloque | 
| c | Carácter especial | 
| d | Directorio |
| f | Archivo |
| l | Enlace simbolico |
| s | Socket |
| D | Door (Solaris) |
| p | FIFO |







