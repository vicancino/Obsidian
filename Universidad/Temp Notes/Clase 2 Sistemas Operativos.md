#### Fecha: 2024-08-23 Hora: 09:00

Status: [[On Going]]

Tags:

# Clase 2 Sistemas Operativos

Los procesos son abstracciones de los programas en ejecución. 
La memoria se puede subdividir en almenos 4 espacios. El código, la data, el heap y el stack. 
En el código se guardan punteros que apuntan a donde se encuentran las instrucciones del código, ya que el area para el código es fija para todos los procesos.
Cuando las llamadas a funciones que se almacenan en el stack superan el espacio de memoria asignado para el proceso, se produce el stack overflow. Las llamadas se van guardando en el stack para tener una linealidad en la ejecución así el sistema operativo sabe a que operación volver una vez una función termina su ejecución.

### Ejecución de un proceso
- Program Counter
	- Instruction Pointer
- Instruction Register
- Stack pointer
Cuando se llama a una función se crea un stack frame donde se almacenan variables locales, direcciones de retorno, y otros datos de la función. Al terminar la función este stack muere. Es por esto que no podemos llamar a variables dentro de funciones desde otras funciones. No obstante si definimos las variables con malloc estas se almacenan en el heap por lo que persisten incluso después de que el stack frame se destruya.

Cuando la CPU ejecuta varios procesos distintos, cada vez que la ejecución de un proceso se interrumpe, se actualiza el PCB del mismo para guardar el estado de ejecución actual. Esto se conoce como context switch.

### Creación de un proceso
Formas de carga: Eargerly el sistema operativo carga datos y código a pesar de que el proceso no necesariamente se vaya a ejecutar. Lazily el sistema operativo espera a que el sistema este en ejecución para cargar los datos y código.

### Fork
Crea una copia del PCB del proceso inicial (padre) y lo inicializa (hijo) este nuevo proceso es una copia del padre en termino de registro código y data, lo que cambia para poder diferenciar a el PCB padre del hijo es el valor de retorno de función 


