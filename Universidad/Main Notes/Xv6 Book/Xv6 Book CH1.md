#### Fecha: 2024-08-25 Hora: 15:26

Status: [[Complete]]

Tags: [[OS]] [[Unix]] [[Shell]] [[Basics]]

# Xv6 Book CH1
### Kernel
El kernel es un tipo especial de programa que provee de servicios para otros programas. A cada programa en ejecución se le denomina proceso, cada proceso posee su propias, instrucciones, memoria, data y stack.  Las instrucciones implementan la computación del programa. La data son las variables sobre las cuales actúa la computación. El stack organiza las llamadas a los procedimientos que realiza el programa. Cuando un proceso necesita algún servicio del kernel este lo llama mediante una "system call" o llamada a sistema, esta llamada entra en el kernel realiza un servicio y se retorna. De esta forma los procesos alterna su ejecución entre el entorno del usuario y el del kernel. 
![[Pasted image 20240825153539.png]]
### Procesos y memoria
Un proceso consiste de un espacio de memoria asignada en el espacio de usuario este contiene instrucciones, data y stack. Xv6 internamente maneja la disponibilidad de la CPU alternando entre los procesos que se encuentran disponibles para la ejecución. Cuando un proceso no se esta ejecutando Xv6 guarda la información del proceso actual para cuando este necesite ser ejecutado nuevamente. Cada proceso posee su propio PID, el cual es el identificador del mismo.

- Fork: Fork es una llamada a sistema que crea un nuevo proceso el cual es una copia exacta de la memoria del proceso que llamo dicha función. La relación entre un proceso que llama a fork y el proceso creado suele ser la del $parent$ y $child$
- Exit: Exit es una llamada a sistema que causa que un proceso detenga su ejecución y libere recursos como memoria y archivos abiertos. 
- Wait: Wait es una llamada a sistema que retorna el PID de algún proceso hijo que haya salido "Exit" o que fue terminado. Luego Wait copia el estado de salida del proceso hijo a la dirección entregada a wait

La ejecución de los procesos $parent$ y $child$ no siempre es secuencial, ya que depende de como la CPU haya administrado sus proceso y cual de ellos haya llegado primero a una llamada a sistema. De esta forma pueden a veces salir las llamadas en orden distinto. 

Cambiar las variables en tanto el padre como el hijo no afectan el uno al otro ya que a pesar de ser uno la copia del otro estos se estan ejecutando en distintos espacios de memoria y registros. 

- Exec: Exec es una llamada a sistema que remplaza la memoria del proceso que la llama por una imagen cargada en un archivo guardado en el file system. Este archivo posee un formato especial para indicar que parte del mismo son las instrucciones, data, con que instrucción iniciar entre otros.

Fork reserva la memoria necesaria para crear una copia de la memoria del padre, mientras que exec reserva la memoria necesaria para alojar una file de tipo ejecutable. Si un proceso requiere mas memoria durante su ejecucion, este puede usar la llamada a sistema $sbrk(n)$ para agrandar su espacio de memoria por $n$ bytes. 

### I/O y descriptores de archivos
Un descriptor de archivo es un valor numérico pequeño que representa un objeto administrado por el kernel donde los procesos pueden escribir o leer. El objeto al cual referencia el descriptor de archivo es un archivo. Este lo hace ver, independientemente de su formato, como un stream de bytes.

Cada proceso tiene su espacio privado de descriptores de archivos, estos empezando numéricamente por el 0. Por conveniencia un proceso lee desde el descriptor de archivo 0 (standard input) y escribe sobre el descriptor de archivo 1 (standard output) mientras que los mensajes de error se envían al descriptor de archivo 2 (standard error)
- Read: El comado Read y también Write, llaman a la lectura/escritura de bytes hacia los archivos abiertos por los descriptores de archivos. los comandos se estructuran de la siguiente forma $read(fd,buf,n)$ esto indica que se leen los $n$ bytes desde el archivo que describe el descriptor de archivo $fd$, los cuales se almacenan en $buf$, luego a función retorna el numero de bytes leídos. Cuando no existen mas bytes para leer, la función retorna 0.
- Write: el comando Write funciona de la misma manera que mencionamos anteriormente y se estructura como $write(fd,buf,n)$ donde estamos diciendo que se escriban los $n$ bytes de data desde $buf$ hacia el archivo que describe el descriptor de archivo $fd$.

Por defecto tanto $read$ como $write$ poseen un offset, este offset funciona para que podamos movernos hacia adelante en el archivo que estamos leyendo y/o escribiendo de esta forma cada vez que se hace una lectura/escritura se avanza en el offset y se leen los siguientes byes.
- Close: La llamada a sistema Close libera el descriptor de archivo seleccionado y lo deja libre para posibles usos en el futuro.
Fork puede hacer redireccion de I/O facilemente debido a que cuando se copia la memoria del padre también se copia la tabla con los descriptores de archivo del padre. De esta forma el hijo posee los mismo archivos abiertos que el padre. Mientras que por otro lado Exec también puede hacer redireccion de archivos, ya que si bien se remplaza la memoria del proceso que llama Exec, se preserva la tabla de descriptores de archivo. 

Dos descriptores de archivos comparten el mismo offset dentro del mismo archivo si ambos derivan del mismo descriptor de archivo original, es decir si fueron creados mediante alguna secuencia de Forks o mediante llamadas a sistemas $dup$ las cuales duplican un descriptor de archivo. 

### Pipes
Una tubería o pipe es un pequeño buffer de kernel expuesto a los procesos como un par de descriptores de archivos. Uno para escribir otro para lectura. Mientras escribimos data en un extremo de la tubería esta puede ser leída en el extremo contrario. De esta forma las tuberías son una manera en la cual nosotros podemos comunicar procesos.
![[Pasted image 20240825172155.png]]

En el ejemplo de código anterior podemos ver como se comunica un proceso padre con su proceso hijo. Primero instanciamos un arreglo de enteros P el cual contiene los números asociados a los descriptores de archivos. Luego mediante $pipe(p)$ guardamos los descriptores de archivos asociados a la lectura y escritura en $p$. Luego de hacer el fork en el proceso hijo "fork == 0" liberamos primero el descriptor de archivo 0 asociado a la lectura (standard input), luego duplicamos el descriptor de archivo que se encuentra en $p[0]$ y cerramos tanto $p[0]$ como $p[1]$ luego se ejecuta el comando exec con los argumentos wc y 0. Mientras tanto en el padre lo que hacemos es cerrar $p[0]$ y escribimos en $p[1]$ la palabra de 12 bytes "hello word" para luego cerrar el descriptor de archivo. De esta forma cuando en "wc" leamos lo que entra por el descriptor de archivo en $dup$ el cual era una copia de $p[0]$ leeremos lo que se introduzca en la tuberia. 
### File system
En Xv6 los archivos se estructuran mediante un árbol, al igual que en la mayoría de sistemas Unix. Estos se estructuran en directorios y en archivos dependiendo de su tipo. El nombre de un archivo es distinto de un archivo en si mismo. El archivo como tal se define como un $inode$ este $inode$ puede tener multiples nombres, llamados $links$. Cada link representa una entrada en un directorio, esta a su vez contiene el nombre del archivo y la referencia hacia el $inode$. El $inode$ contiene metadata acerca del archivo en cuestión, incluyendo a su vez el tipo, la longitud, la ubicación del contenido del archivo en disco y el numero de links asociados al archivo.
- fstat: Fstat es una llamada a sistema que recupera al información del $inode$ asociado a un descriptor de archivo. 
- link: Link es una llamada a sistema que crea un nuevo nombre de archivo que referencia a un $inode$ existente. 
- unlink: Unlink remueve un nombre del archivo del sistema de archivos. Los contenidos del $inode$ en el disco se liberan únicamente cuando no existen mas $links$ apuntado al $inode$ de esta forma el archivo deja de existir.