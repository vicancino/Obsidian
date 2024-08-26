#### Fecha: 2024-08-13 Hora: 12:02

Status: [[Complete]] 

Tags: [[Basics]] [[Unix]] [[OS]]

# Learning the Unix Operating System CH 2

### Windowing
El sistema principal de windowing de Unix X es el encargado del manejo de la sesiones y ventanas que se presentan en el programa, existen distintos Windows Managers entre ellos por ejemplo "eye candy" el Window Manager define como se vera la computadora, este puede verse tanto como un Mac como un equipo Windows dependiendo del diseño del mismo. Después de los windows managers están los $desktop$ $environment$ estos proveen aun mas funcionalidades, entre ellos existen dos muy famosos y comunes GNOME y KDE, los $desktop$ $environment$ utilizan windows managers para el manejo de las ventanas y GUI.

### Background Task
Uno puede dejar sesiones de X y programas funcionando en background, como por ejemplo el programa $xcalc$ lo podemos correr en una terminal de Unix con el comando: $\$xcalc~\&$ con el símbolo $\&$ podemos ejecutar el proceso y dejarlo trabajando en background, de esta forma liberamos al consola, el retorno de dicho comando devuelve el numero del proceso asociado al comando ejecutado, luego la linea de comando queda liberada y no tenemos que esperar o interrumpir el proceso para seguir utilizándola.

### Comandos
- $pwd$: Muestra el directorio actual en el cual nos encontramos trabajando