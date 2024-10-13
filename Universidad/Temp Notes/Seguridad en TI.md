#### Fecha: 2024-09-19 Hora: 14:13

Status: [[On Going]]

Tags:

# Seguridad en TI
### Semana 1
Los 6 ataques mas comunes que afectan a empresas e individuos son: 
- Ingeniería Social (Incluye Phising) : Vulnera datos y genera perdidas financieras, puede llevar a robo de identidad y fraudes financieros.
- Ransomware: Perdida de datos, interrupción de la operatividad de la empresa, también puede llevar al robo de datos personales.
- Denegación de Servicio Distribuido (DDoS): Interrupciones de servicios e insatisfacción del cliente, no disponibilidad del servicio. 
- Malware: Danos al sistema, acceso no autorizado, robo de datos
- Extorsión de datos: Robo y amenaza de exposición de datos privados, chantaje.
- Intermediario (MitM, Man in the Middle): Robo y acceso no autorizado a datos confidenciales
Los tres pilares de la ciberseguridad son la confidencialidad, la disponibilidad y la integridad

##### Elementos de la red
Por una lado esta primero Internet, este es representado como una red externa global y con forma de nube para poder distinguir su amplitud y diversidad de Hosts. Luego tenemos un router el cual interconecta nuestra red interna con Internet. Entre el router y nuestra red interna se posiciona un firewall encargado de la supervision de las interconecciones entre nuestra red interna e Internet. Luego del firewall se encuentra un switch el cual distribuye e interconecta los dispositivos dentro de nuestra red interna. 
- Internet
- Router
- Firewall
- Switch
##### Las 7 Capas del modelo OSI (Open Sistem Interconection Model)
1) Capa Física
2) Capa de Enlace
3) Capa de Red 
4) Capa de Transporte 
5) Capa de Sesión 
6) Capa de Presentación 
7) Capa de Aplicación
##### Familias de Protocolos de Red 
![[Pasted image 20240919142748.png]]

##### Herramientas de Monitoreo
- Grafana
- Elastic Stack 
	- Logstash
	- Elastich Search
	- Kibana
##### Herramientas de Observación
- WireShark
- TCPDump
- Ettercap
- Dsniff
#### Que hacer como respuesta a un Ataque de Denegación de Servicio (Dos)
Supongamos que nos encontramos bajo un ataque de denegación de servicio el cual tiene como propósito utilizar gran parte del ancho de banda de la red para ralentizar el trafico algunas buenas practicas serian: 
- Desconectar el servidor para disminuir la carga en la maquina
- Cambiar la configuración de firewall para bloquear las IPs que se encuentran realizando el ataques
- Spoofing consiste en cambiar la dirección de IP (por parte del atacante) para poder evitar bloqueos, se debe tener esto en consideración
- Levantar las alertas del ataque al equipo de trabajo

### Semana 2 
##### Anatomía de un ataque Informático
1) La primera fase o reconocimiento es aquella en la cual se escanea y se busca encontrar la mayor cantidad de información disponible de la victima sin alertar a esta misma. 
2) La segunda fase o Exploración es donde se trata de encontrar información detallada de la victima buscando vulnerabilidades las cuales puedan ser explotadas.
3) La tercera fase o la Obtención de Acceso es donde se consigue acceso no autorizado a los recursos o bien se explota alguna vulnerabilidad para poder acceder a informacion sensible. 
4) La cuarta fase es Mantener el Acceso en esta fase el atacante se asegura de poder reincidir en las vulneraciones al sistema y seguir comprometiendolo sin ser vulnerado 
5) La quinta fase es Borrar los Rastros el atacante elimina cualquier tipo de información que pueda relegar y evidenciar su ataque para que este no sea descubierto
##### Fases del Hacking Ético 
El hacking ético consiste en practicar ataques ciberneticos sobre un sistema de forma controlada de esta forma se pueden analizar las vulnerabilidades del sistema y se pueden aplicar parches en conforme a dichas vulnerabilidades para así poder mejorar el sistema y volverlo mas robusto frente a ciberataques. Sus fases son:
1) El Reconocimiento
2) El Escaneo
3) La Enumeración
4) El Análisis de Vulnerabilidades
5) La Explotación
6) Y el Reporte

##### Port Scanning
Es una practica que consiste en analizar que puertos de una maquina se encuentran disponibles o que servicio tienen asociado, para esto podemos utilizar herramientas como Nmap, normalmente al escanear un host detrás de un firewall este bloquearía el escaneo pero Nmap permite ocultar la fuente del escaneo evadiendo al firewall.