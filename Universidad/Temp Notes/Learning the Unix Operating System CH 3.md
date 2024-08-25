#### Fecha: 2024-08-14 Hora: 09:36

Status: [[On Going]]

Tags:

# Learning the Unix Operating System CH 3

### The Unix File system
En Unix la unidad base de almacenamiento es un archivo $(file)$ la cual puede contener multiples tipos de datos, incluso programas mismos. Estos archivos se organizan mediante directorios $(directories)$ estos son un formato especial de los archivos en los cuales se guarda información acerca de otros archivos.

### The Directory Tree

![[Pasted image 20240814094233.png]]
### Relative V/S Absolute Pathnames
Cuando estamos trabajando con Unix existen dos formas de referenciar los archivos a los que queremos apuntar, la primera forma es ocupar un pathname absoluto, los pathnames absolutos se caracterizan por iniciar siempre con "/" de esta forma nos referimos siempre inicialmente al directorio root como base, un ejemplo de path-name absoluto del esquema anterior seria "/users/john/work" siendo el primer "/" el directorio root. La segunda forma de referenciar archivos es mediante los pathnames relativos. Los pathnames relativos referencian los archivos a partir del directorio de trabajo actual, por lo que no inician con el caracter "/" ya que no necesariamente nos encontramos trabajando en el directorio root. Luego funcionan de la misma manera que un pathname normal, por ejemplo si estuviéramos en el directorio "users" en el diagrama anterior el pathname relativo hacia el directorio "work" seria únicamente "john/work". Por defecto al trabajar en Unix este asume que todos los pathnames que ingresemos son del tipo relativo a menos que indiquemos lo contrario anteponiendo el "/"
### Relative Pathnames up 
Para referenciar desde un archivo otro archivo que se encuentra anexado a un directorio posterior al que nos encontramos por ejemplo digamos que nos encontramos en /etc/apt/listados, pero también existe un directorio llamado /etc/apt/menus. Si nuestro directorio de trabajo actual es /etc/apt/listado, como podríamos referenciar de forma relativa el directorio menus? Para esto ocupamos la nomenclatura (..) antes del caracter "/" de esta forma cuando colocamos ../ nos estamos refiriendo relativamente al directorio padre del cual nos encontramos es decir si continuamos con el ejemplo anterior para referenciar /etc/apt/menus desde el directorio /etc/apt/listado bastaría con colocar ../menu ya que al referencia con doble punto al directorio padre equivaldría dicha expresión a apt/menu.
### Listado de Entradas

![[Pasted image 20240820160018.png]]

Si ingresamos el comando $ls -al$ obtendremos un resultado parecido dependiendo del directorio en el que nos encontremos trabajando. En una primera instancia nos encontramos el tipo de archivos este puede ser "d" para directorios o "-" para archivos. Existen en todo caso mas tipos de archivos. Luego vienen 9 caracteres seguidos estos caracteres se deividen en 3 grupos y cada caracter perteneciente a cada grupo indica los permisos que posee dicho grupo para el directorio o archivo. Es decir tendriamos los diez caraceteres (---------) sabiendo luego que el primero es para diferenciar el tipo de archivo podemos hacer la siguiente particion (-; --------) luego los nueve restantes los dividimos entre 3 de la siguiente forma  (-; ---; ---; ---;) ahora cada trio indica los permisos que tiene un grupo u persona sobre el archivo. El primer trio de letras indica los permisos que tiene el creador del archivo sobre el mismo. El segundo grupo indica los permisos que tienen los usuarios que pertenecen al mismo grupo que el creador. El tercer trio indica los permisos que tienen el resto de usuarios del sistema. Existen tres tipos de permisos cada uno demarcado por una letra, en una primera instancia tenemos la letra "r" la cual indica permisos de lectura sobre el archivo u directorio, luego "w" indica permisos de escritura y por ultimo "x" indica que el grupo puede ejecutar dicho archivo (executable). Los siguientes campos se explican por si mismos en la imagen.
### Comandos 
$cd$: Comando utilizado para cambiar el directorio de trabajo actual, recibe como argumento el pathname del directorio al cual nos queremos trasladar (si se introduce el comando $cd$ sin argumentos entonces por defecto iremos al directorio home)
$ls$: Comando utilizado para listar las entradas que se encuentran almacenadas en el directorio actual Opciones: -C para multicolumnado, -a para mostrar todos los archivos, incluido los ocultos, -l muestra un listado extendido de los archivos. -F para saber únicamente que archivos son ejecutables. -R busca en los directorios de forma recursiva 
$chmod$: Comando utilizado para cambiar los permisos de un archivo. T
