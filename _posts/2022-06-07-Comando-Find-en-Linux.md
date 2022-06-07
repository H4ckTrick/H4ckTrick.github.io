---
layout: post
author: Conde
---

## Índice
- [Definción](#definción)
- [Parámetros](#parámetros)
  - [Profundización en -type y -size](#Type-y-Size)
- [Ejemplos de uso](#ejemplos-de-uso)

### Definción 
Find, es un comando que nos permite realizar búsquedas de ficheros, directorios, enlaces y demás de una forma rápida. Este comando es muy potente, ya que nos permite realizar acciones sobre salidas de ficheros buscados, eliminar directorios vacios, patrones de busqueda, etc. 

### Parámetros 
- **-name** o **-iname** → Indicamos el nombre del fichero a buscar (-iname)
- **-exec** → comando a ejecutar para el recurso encontrado (Necesita usar {} \;)
- **-user** → Indicas el usuario al que pertenece el recurso
- **-group** → Indicas el grupo al que pertenece el recurso
- **-print** → Imprime por pantalla el resultado
- **-mtime** y **mmin** → Indicamos un periodo de tiempo 
- **-size** → Indica el tamaño del recurso
- **-delete** → Elimina el recurso de salida  
- **-readable** → Muestra el recurso que tenga el permiso de lectura
- **-writable** → Muestra el recurso que tenga el permiso de escritura
- **-executable** → Muestra el recurso que tenga el permiso de ejeccución
- **-type** → Tipo del recurso
- **-perm** → Permisos que debe tener el recurso
- **-and**, **-a** y **-not**, **-or** → Operadores and y or 

#### Type y Size
Dentro del parámetro **-type**, podemos encontrar los siguientes tipos. 
-  b → Bloque 
-  c → Carácter especial  
-  d → Directorio
-  f → Archivo
-  l → Enlace simbolico 
-  s → Socket 
-  D → Door (Solaris) 
-  p → FIFO 

Dentro del **-size** tambien podemos encontrar los siguientes tipos. 
-  b → 512-byte  
-  c → Bytes  
-  w → two-byte
-  k → KiB 
-  M → MiB
-  G → GiB

### Ejemplos de uso 
Buscar directorios vacios y eliminarlos. 
```bash
find . -type d -empty -delete -print
```

Buscar permisos SUID en el sistema, redirigimos el STDERR al /dev/null, para que no muestra errores por pantalla.
```bash
find / -perm /4000 2>/dev/null
```

Buscar ficheros txt con propietario y grupo.
```bash
find / -iname "*.txt" -user conde -group web 2>/dev/null
```

Eliminar todos los script de bash de nuestra carpeta actual.
```bash
find . -iname "*.sh" -type f -exec rm {} \;
```

Buscar archivos modificamos este ultimo día.
```bash
find / -mtime -1
```

Buscar archivos modificamos el los utlimos 5 minutos.
```bash
find / -mmin -300
```
