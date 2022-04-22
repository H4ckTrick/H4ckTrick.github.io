---
layout: post
author: Conde
---

## Índice
- [Definición](#definción)
- [Explicación](#explicación)
- [Enumeración](#enumeración)


### Definición
Cron, es un demonio que se ejecuta en el S.O en el arranque. Este nos permite programar
tareas que se realizaran en determinado periodo de tiempo, pero para es importante tener 
configurado correctamente la hora (NTP).

### Explicación 
Dependiendo de la distribución cron se inicia en algun directorio de los siguientes: 
- **/etc/rc.d/**
- **/etc/inid.d/** 

Una vez que este es arrancado comprueba constantemente los ficheros de las siguientes rutas: 
- /etc/crontab 
- /var/spool/cron

Cada usuario puede modificar su contrab, de la siguiente forma.
```bash
crontab -e 
```
Dentro de ese fichero, podemos configurarlo dependiendo de cuando queremos que se ejecuten
las tareas.
![CronJobs](https://github.com/H4ckTrick/H4ckTrick.github.io/blob/main/_posts/_images/cron.png)

<p align="center"> 
  <img src="https://github.com/H4ckTrick/H4ckTrick.github.io/blob/main/_posts/_images/cron.png">
</p>

### Enumeración
#### Ficheros de crontab 
Una vez que hemos visto lo básico para entender cron, vamos a comenzar haciendo una enumeración.
Podemos ver el fichero cron usando el siguiente comando (Necesitaremos permisos):

```bash
crontab -l 
```
Otra forma, viendo el contenido del fichero crontab

```bash
cat /etc/crontab 
```
Dentro de la ruta */var/spool/cron/crontabs/* podemos encontrar una lista de crontabs. 

```bash
ls -l /var/spool/cron/crontabs/
```

Una vez que visualizamos los existentes, podemos verlo. 

```bash
cat /var/spool/cron/crontabs/root
```
#### Logs y Procesos
##### Cronlog 
A parte de enumerarlos a traves de los fichero que aveces no tenemos permisos, tambien podemos hacerlo a traves de 
los logs. A traves del cronlog.

```bash 
cat /var/log/cronlog 
```

##### Syslog
Tambien podemos a traves del syslog

```bash 
cat /var/log/syslog | grep -i 'cron'
```

##### Bash 
Tambien podemos descrubrir procesos que se esten ejecutando en el sistema, como bien
puede ser las tareas cron. Tambien seria posible desarollar un script, que monitorize
los precesos que se estan ejecutando, con posibles tareas.

```bash 
ps -eo command | grep -v "kworker"
```
