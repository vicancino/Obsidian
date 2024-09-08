#### Fecha: 2024-08-25 Hora: 18:28

Status: [[On Going]]

Tags:

# Xv6 Book CH2
### Organización del Sistema operativo
Un sistema operativo debe ser capas de completar 3 requerimientos: multiplexion, aislacion e interacción. Esto de la forma en la que se organizan los procesos, en una primera instancia el sistema operativo debe asegurar que a pesar de que existan mas procesos que hardware y CPUs disponible cada proceso tenga la posibilidad de ejecutarse (multiplexion) En una segunda instancia los procesos deben poder ser ejecutados de manera aislada, esto quiere decir que si ciertos procesos fallan durante se ejecución, estos no afecten a aquellos que no dependen de estos (aislacion) Por ultimo los procesos deben poder interactuar unos con otros (interacción)
### Abstracción de los recursos fiscos
Por que es necesario el sistema operativo en una primera instancia, si de hecho podríamos implementar en una aplicación una misma librería que interactuara con el hardware directamente, sin necesidad de utilizar llamadas a sistemas. Bueno para que esto ocurra y podamos implementar multiplexion la aplicación que toma el control de la CPU se debe comportar "correctamente" y dejar por ejemplo tiempo libre de CPU para que las siguientes aplicaciones tomen control de la misma. Otra forma es que funcionen de forma cooperativa, pero esto llevaría un gran problema con los Bugs que existan y afecten a otras aplicaciones. La idea principal del uso de un sistema operativo es poner a disposición los recursos de hardware a los usuarios mediante llamadas a sistema, de esta forma uno puede hacer la organización, estructuración y optimizacion de procesos sin requerir lo mismo de los procesos mismos.

### User mode, supervisor mode, system calls
Para asegurar la aislacion de los procesos el sistema operativo debe ser capaz de prevenir que distintas aplicaciones accedan entre si a sus espacios de memoria restringidos. Existen en RISC-V modelo CPU tres tipos de instrucciones de ejecución: en modo maquina, en modo supervisor y en modo usuario. El modo maquina se utiliza para configurar el computador. En modo supervisor, la CPU es capaz de ejecutar instrucciones privilegiadas. Si aplicaciones que no tienen privilegios intentan ejecutar instrucciones privilegiadas la CPU en modo supervision detiene dichos procesos. las aplicaciones no pueden llamar a funciones del kernel directamente, si no que hacen llamadas a sistema, luego la CPU en modo supervision procesa y valida las llamada de sistemas en el espacio del kernel. El software ejecutándose en el espacio del kernel o en modo supervision es llamado Kernel.

### Kernel Organization
Existen varios formatos de organizar el kernel de un sistema operativo, estas ideas nacen desde la perspectiva de pensar que tanto del sistema operativo debe operar con privilegios sobre la CPU y que tanto, por un lado están los modelos monolíticos donde la completitud del sistema operativo opera en modo privilegiado, la contra parte de dicha propuesta es que si ocurre algún fallo este probablemente cause un error en la maquina y el computador se detenga. Por otro lado se encuentra el concepto de microkernels, este concepto divide las utilidades del sistema operativo hacia el espacio del usuario donde luego dichos servicios que operan en el espacio de usuario pueden solicitar al kernel o el software que opera con privilegios mediante llamadas a sistema la interacción con la CPU. En el concepto de microkernels, los servicios del sistema operativo que operan como procesos en el espacio del usuario se conocen como servidores.

### Process overview
La unidad de isolacion de Xv6 se denominan processos, para garantizar la isolacion Xv6 utiliza direcciones de memoria virtuales y reales. De esta forma los programas se les asignan las direcciones de memoria virtuales, iniciando en v0 y terminando en vmax luego Xv6 mapea dichas direcciones a las direcciones de memoria reales. Esto permite que cada proceso se vea a si mismo como en una maquina aislada, ademas el kernel debe ser cuidadoso al crear la abstraccion del proceso ya que programas maliciosos podrian aprovechar dicha abastraccion para acceder a espacio de memoria de otros procesos. La forma en la que las direcciones de memoria se traducen es mediante unas tablas denominadas "page tables". Cada proceso posee su unica page table.

![[Pasted image 20240903094516.png]]

En la parte superior de la direccion de espacio Xv6 reserva una "page" para un $trampoline$ y una page para mappear el proceso mismo $trapframe$. Estas dos "pages" son utilizadas para transicionar hacia dentro y fuera del kernel, la page $trampoline$ contiene el codigo para la transicion mientras que al mapear el $trapframe$ es necesario para salvar el estado de un proceso del usuario. 

Para la ejecucion de un proceso se tiene un Hilo de ejecucion "thread" el cual ejecuta el proceso seleccionado, este puede ser pausado para luego ser resumido. Cuando el kernel alterna entre los threads que se encuentran en ejecucion detiene uno y resume otro conforme a su administracion. Cada proceso tiene dos stacks distintos. Un stack de Usuario y un stack de kernel, normalmente los procesos utilizan el stack de usuario, pero cuando realizan una llamada a sistema y las instrucciones entran al kernel, se empieza a utilizar el stack del thread, aqui se guardan todas las variables del estado del thread. De esta forma durante la ejecucion de un mismo proceso, se alterna entre el uso de su stack de usuario y su stack de kernel. 

A forma de resumen en un proceso se abstraen dos tipos de hardwares, una dirección virtual que da la impresión que el proceso posee su propia memoria física, y un thread el cual da la ilusion de que el proceso posee su propia CPU.

### Comandos
- $ecall$ : Esta instruccion realiza una llamada a sistema, y otorga privilegios de hardware al proceso en ejecucion, tambien cambia el contador del programa hacia un punto definido de entrada para el kernel.
- $sret$ : Esta instruccion se utiliza para salir del modo privilegiado del sistema.

