# laboratorio No. 8 – Comandos básicos #2, I/O Redirection, monitoring system resources, Scripts con menú

#### Instrucciones:
Siga paso a paso los comandos en este documento y grabe un video de su servidor mientras realiza el laboratorio, suba su video a Youtube y entregue el link vía GES

### Creación de Scripts con menú

1. cree un nuevo script en su servidor llamado ```script.sh```
2. copie el siguiente código
```
#! /bin/bash
seg=true
while [ seg ]
do
	echo “”
	echo “(1) list files on actual directory”
	echo “(2) date”
	echo “(3) disk st”
	echo “(4) install updates”
	echo “(5) exit”
	echo “”

	echo “Ingrese una opción”
	read option
	echo “”
	
	if  [ $option -eq 1 ]
	then
		echo “Enlistando archivos en el directorio actual”
		sudo ls
	
	elif [ $option -eq 2 ]
	then
		echo “Fecha de hoy”
		sudo date

	elif  [ $option -eq 3 ]
then
echo “instalando actualizaciones”
sudo apt -get update
	
	elif  [ $option -eq 4 ]
	then
		echo “mostrando informacion de disco”
		sudo df -h

	elif  [ $option -eq 5 ]
	then
		echo “Adios”
		seg=false
		break
	fi
done
```
3. corralo y haga pruebas
4. pruebe modificar el script con otros comando

### Redirección

1. Corra el siguiente comando ```echo $(ls -l) > archivo.txt```
2. Explique que pasa si no se utilizarán los ‘$()’ al correr el comando.
  2.1  Investigue la diferencia entre correr ```ls``` y ```echo $(ls)```
3. Concatene el siguiente comando al archivo creado en el inciso anterior: ```netstat -n``` e indique que despliega dicho comando.
4. Corra el comando ```tail -n 5 archivo.txt``` e indique el output de dicho comando.
5. Corra el comando ```ls /asdaa > error.txt``` y documente el resultado.
6. Corra nuevamente ```ls /asdaa 2>error.txt```, explique el resultado.
7. Corra ```ls /usr/bin  /home/ &> error2.txt``` y explique que pasaría si se corriera del siguiente modo ```ls /usr/bin  /home/ 2> error2.txt```
8. Acceda a la siguiente dirección ```/var/log``` y corra el comando ```more syslog```
9. Corra seguido el siguiente comando ```less syslog /server``` e indique qué significa el ‘/server’ al final del comando, para esto quizás quiera primero leer ```less -help```
10. Asegúrese de estar en el path ```/var/log/``` y corra los siguientes comandos y documente sus resultados.
  ```wc -l syslog```
  ```wc -m syslog```
  ```wc -L syslog```
11. Corra el siguiente comando  ```cat /etc/passwd | grep /home | wc -l``` e indique que hace cada una de las partes del mismo.

### Monitoreo de recursos

1. corra el comando ```df - h``` para ver el espacio e información almacenada en su disco o partición
2. corra el comando ```free```
3. corra el comando ```cat /proc/meminfo``` y vea la información que despliega el comando
4. corra el comando ```cat /proc/cpuinfo```
5. corra el comando ```lsof``` para ver el listado de archivos abiertos en su servidor
6. por último, corra el comando ```netstat -a | more``` para ver información de los paquetes y estadísticas de las interfaces de su red.

Todos estos comandos le servirán para poder monitorear los recursos de sus servidores y así evitar fallos en seguridad y saturación.
