#### Fecha: 2024-08-14 Hora: 09:36

Status: [[On Going]]

Tags:

# Learning the Unix Operating System CH 3

### The Unix File system
En Unix la unidad base de almacenamiento es un archivo $(file)$ la cual puede contener multiples tipos de datos, incluso programas mismos. Estos archivos se organizan mediante directorios $(directories)$ estos son un formato especial de los archivos en los cuales se guarda información acerca de otros archivos.

### The Directory Tree

![[Pasted image 20240814094233.png]]

### Relative V/S Absolute Path-names
Cuando estamos trabajando con Unix existen dos formas de referenciar los archivos a los que queremos apuntar, la primera forma es ocupar un Path-name absoluto, los path-names absolutos se caracterizan por iniciar siempre con "/" de esta forma nos referimos siempre inicialmente al directorio root como base, un ejemplo de path-name absoluto del esquema anterior seria "/users/john/work" siendo el primer "/" el directorio root. La segunda forma de referenciar archivos es mediante los path-names relativos. Los path-names relativos referencian los archivos a partir del directorio de trabajo actual, por lo que no inician con el caracter "/" ya que no necesariamente nos encontramos trabajando en el directorio root. Luego funcionan de la misma manera que un path-name normal, por ejemplo si estuviéramos en el directorio "users" en el diagrama anterior el path-name relativo hacia el directorio "work" seria únicamente "john/work". Por defecto al trabajar en Unix este asume que todos los path-names que ingresemos son del tipo relativo a menos que indiquemos lo contrario anteponiendo el "/"
