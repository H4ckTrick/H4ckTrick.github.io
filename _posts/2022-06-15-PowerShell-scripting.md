---
layout: post
author: Conde
---


## Índice
- [Definición](#definción)
- [Ayuda](#ayuda)
- [Alias](#alias)
- [Variables](#variables)
- [Redirecciones](#redirecciones)

### Definición 
PowerShell es un shell de comandos moderno que incluye las mejores características de otros shells populares. A diferencia de la mayoría de los shells que solo aceptan y devuelven texto, PowerShell acepta y devuelve objetos .NET. El shell incluye las siguientes características:

- Un historial de línea de comandos sólido.
- Finalización con tabulación y predicción de comandos (vea about_PSReadLine).
- Admite alias de comando y parámetro.
- Canalización para encadenar comandos.
- Sistema de ayuda en la consola, similar a las páginas man de UNIX.

### Ayuda
Para pedir ayuda en PowerShell, podemos utilizar el siguiente cmdlet: 
```powershell 
Get-Help <cmdlet-name>
```

Tambien podemos actualizar la ayuda (Debemos estar como administrador), para ello: 
```powershell 
Update-Help
```

### Alias
Los alias, no son más que otra forma de ejecutar el mismo cmdlet, esto ocurre al igual en Linux. Mis Alias favoritos y más usados son: 
- **?** ➜ Where-Object
- **%** ➜ ForEach-Object
- **gc** ➜ Get-Content
- **cp** ➜ Copy-Item 
- **fl** ➜ Format-List
- **rm** ➜ Remove-Item 
- **sls** ➜ Select-String
- **diff** ➜ Compare-Object
- **sort** ➜ Sort-Object
- **sleep** ➜ Start-Sleep

Para crear nosotros nuestros alias usaremos en siguiente cmdlet: 
```powershell 
Set-Alias -Name pwd -Value Get-Location
```

para ver los alias por defecto de PowerShell, usaremos el siguiente cmdlet: 
```powershell 
Alias
```

### Variables 
Dentro de PowerShell, tenemos varias variables que son muy útiles a la hora de hacer nuestros script, que son: 
- **$_** ➜ Está variable se acutaliza constantemente dependiendo de los campos que haya en la condición indicada
- **$?** ➜ Mustra el codigo de salida del comando al igual que en linux (0 es true, 1 es false)
- **$IsLinux** ➜ Indica true si el S.O es Linux
- **$IsWindows** ➜ Indica true si el S.O es Windows
- **$IsMacOS** ➜ Indica true si el S.O es Mac OS
- **$null** ➜ Con esta variable podemos indicar si algo es nulo, o si por ejemplo queremos redirigir salidas 

Para nosotros crear una variables solo debemos indicar en consola o script la siguiente sintaxis: 
```powershell 
$variable="Conde"
```

### Redirecciones  
Al igual que en Linux, nostros podemos realizar redirecciones tanto del STDIN, STDOUT y STDERR. Veamos todos los ejemplos posibles: 

Redireccionamos el STDOUT al fichero ruta.txt
```powershell 
pwd > ruta.txt
```
Agregamos contenido a mayores del ya existente con la doble flecha. 
```powershell 
pwd >> ruta_ayer.txt
```
Redireccionar STDERR, para que no se vea en consola. 
```powershell 
pwd 2> logs.txt
```
Redireccionar warnings. 
```powershell 
pwd 3> warnings.txt
```
Redireccionar verbose 
```powershell 
pwd 4> verbose.txt
```
Redireccionar mensajes de depuración
```powershell 
pwd 5> debug.txt
```
Para redireccionar todo los visto usaremos el "\*". 
```powershell 
pwd *> all.txt
```

En resumen: 
-  \* ➜ Todo el  output
-  1 ➜ STDOUT
-  2 ➜ STDERR
-  3 ➜ Warning 
-  4 ➜ Verbose 
-  5 ➜ Debug 

### Mensajes por pantalla 
Al igual que en batch, bash, python y demás podemos mostrar mensajes por terminal. Para hacerlos con powershell, usaremos el siguiente cmdlet: 
```powershell 
Write-Host
```
Yo lo suelo usar mucho, y concretamente le agrego 3 parámetros muy interesantes. 
- -nonewline ➜ No hace salto de linea 
- -ForegroundColor ➜ Cambiamos el color de la letra 
- -BackgroundColor➜ Cambiamos el color de fondo del mensaje 

Otra cosa muy curiosa, es que para realizar saltos de linea, tabulaciones y demás no se usa "\n", "\t", etc, se usa lo siguiente: 
- \`n ➜ Salto de linea 
- \`t ➜ Tabulación 

Ejemplo completo: 
```powershell 
Write-Host -ForeGroundColor Yellow "Hola Jose `n" 
```
