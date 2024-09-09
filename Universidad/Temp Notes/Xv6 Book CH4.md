#### Fecha: 2024-09-08 Hora: 21:37

Status: [[On Going]]

Tags:

# Xv6 Book CH4
### Traps and System Calls 
Existen 3 tipos de eventos que pueden causar que una CPU cambie su forma ordinaria de ejecucion y otorgue control a cierto codigo especial que se encagara del evento asociado. La primera forma es una "Llamada a sistema" esta es cuando un programa ejecuta la instrucción $ecall$ para solicitar acceso al kernel. La segunda forma es una "Excepción" esta sucede cuando una llamada a sistema falla, tanto de manera intencional como no intencional. La tercera forma son las "Interrupciones" estas ultimas se levantan cuando los dispositivos necesitan atención. El código en C o en assembler que procesa las Traps y System Calls en Xv6 son comúnmente llamadas "Handlers", algunas veces incluso "Vectores".

