#### Fecha: 2024-08-13 Hora: 09:49

Status: [[Complete]]

Tags:[[Unix]] [[Basics]] [[Shell]]

# Learning the Unix Operating System CH 1

## Shell
La consola tiene diversas formas de identificar quien esta operando la misma, normalmente ocupan caracteres especiales para identificar los permisos del usuario que se encuentra registrado, por ejemplo comúnmente un usuario con permisos básicos tendrá un caracter ($) en los $promps$ de la terminal mientras que un usuario que tenga permisos de $superuser$ probablemente tenga un caracter (#)
### Opciones
Las Opciones de los comandos por ejemplo $-a$ $-b$ suelen ser letras o prefijos ante puestos por un dash (-) uno puede introducir multiples comandos en una misma linea e incluso a veces se pueden unir en un mismo argumento de la forma $-ab$ aunque esto no suele ser usual o debe confirmase mediante la documentación del comando en cuestión. Hay ocasiones en los cuales los argumentos de las opciones pueden ser incluso palabras completas como es el caso de $--delete$ o $--confirm-delete$.
#### Comandos
Nota: el caracter (;) puede ser utilizado para introducir mas de un comando en una misma linea de consola
- $date$: Muestra la fecha y hora actual
- $who$: Muestra el usuario que se encuentra conectado, el numero de la terminal y el tiempo de login
- $ls$: Muestra una lista de los archivos
### Shortcuts:
- CTRL-H: "Control Character" permite borrar caracteres igual que la tecla DEL o BACKSPACE
- CTRL-U: Elimina toda la linea de entrada
- CTRL-S: Pausa la salida de un programa en ejecución en la terminal
- CTRL-Q: Reanuda la pausa después de utilizar CTRL-S
- CTRL-D: Utilizado normalmente para señalar un end-of-input, también puede ser utilizada para cerrar la terminal o salir del sistema Unix. Sirve de la misma forma que escribir $exit$ en la terminal
- 