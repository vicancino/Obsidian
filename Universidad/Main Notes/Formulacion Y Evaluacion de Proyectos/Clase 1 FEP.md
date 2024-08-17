#### Fecha 2024-08-12 Hora 13:41

Status: [[Complete]]

Tags: [[Economía]] [[FEP]]

# Clase 1 FEP

# Matemática Financiera 

## Valor del Dinero en el tiempo
"Un peso hoy vale mas que un peso manana" Los seres humanos tendemos a ser impacientes por lo que no preferimos postergar el consumo ya que si yo poseo el dinero de manera inmediata, lo puedo utilizar en diversas funciones en vez de esperar por el. Dado esto estamos dispuestos a hacer diversos "Trade-Offs" los cuales implican sacrificios en búsqueda de un objeto, esto se traduce a estar dispuesto a recibir una menor cantidad de dinero pero de forma inmediata a esperar cierta cantidad de tiempo X para obtener el monto total. De esta forma la matematica financiera cobra sentido ya que el valor del dinero es variable en el tiempo.

#### Coste de oportunidad
De esto recalcamos que tener el dinero en un determinado tiempo (situación) puede generar mayor valor. A este fenómeno le llamaremos costo de oportunidad. Definiremos entonces dicho concepto como: "el coste de oportunidad de un bien o servicio es la cantidad de otros bienes o servicios a los que se debe renunciar para obtenerlo, es decir el coste de la alternativa que se desecha cuando se toma una decision".

#### Tasa de Descuento
Denotaremos R como la tasa que representa el costo de oportunidad, como mencionamos anteriormente, esta se puede interpretar como la rentabilidad a la que se renuncia al invertir en el proyecto en lugar de invertir en alguna alternativa.

#### Interés Simple
Es el interés que se calcula sobra un capital que permanece constante en el tiempo, el interés ganado o pagado se acumula solo al termino de esta transacción. De esta forma tenemos la ecuación:
$$ \text{Monto Recibido - Capital Inicial = Interes} $$
De esta forma por ejemplo si tenemos un monto inicial de $1000 y una ganancia de $1200 sabremos que el interés recibido es igual a:

$$ $1200 - $1000 = $200$$
Generalicemos ahora de la siguiente manera un caso en el que nuestro capital  inicial sea $C_0 = \$100$ y la tasa de interés $r = 10\%$ Luego para calcular Capital final en el enésimo periodo tendremos la siguiente sucesión:
$$\begin{align}
	C_1&=C_0 + C_0*r \\
	C_2&=C_1 + C_0*r \\ 
	C_2&=C_0 + C_0*r + C_0*r \\
	C_2&=C_0 + 2*C_0*r \\
\end{align}$$
Finalmente factorizando y generalizando la sucesión llegamos a: 
$$\begin{align}
	C_n = C_0(1+ n*r)
\end{align}$$
#### Interés compuesto
El interés compuesto es aquel que se aplica sobre el capital invertido y se agrega al capital principal. Se gana interés sobre interés. Visto de otra forma se asume la re-inversion de los intereses de los periodos intermedios. Supongamos entonces que $C_0 = \$100$ y $r = 10\%$ Luego tendremos la siguiente sucesión para calcular el interés en el enésimo periodo: 
$$\begin{align}
	C_1&= C_0 + r*C_0\\
	C_2&= C_1 + r*C_1\\
	C_2&= C_0 + r*C_0 + r*(C_0 + r*C_0)\\
	C_2&= C_0(1+r)(1+r)\\
	C_2&= C_0(1+r)^2
\end{align}$$
Finalmente para calcular la sucesión en el enésimo periodo podemos concluir: 
$$C_n = C_0 * (1 + r)^n$$
O por defecto también el equivalente a:
$$C_n = C_{n-1} + r*C_{n-1}$$

#### Inflación
La inflación se define como el aumento generalizado y sostenido de los precios de los bienes y servicios de un país durante un periodo de tiempo determinado, comúnmente durante un año. Que un bien suba un cierto % no implica necesariamente un aumento en la inflación, ya que otro bien se puede contraer en el mismo % y equiparar el coste de vida. Esto se toma en cuenta a partir de cierta canasta de precios promedio de bienes y servicios. Esta canasta ayuda a medir la inflación a través del indice IPC (Indice Precio Consumidor) los cuales indican la evolución de los precios de la misma.

#### Tasa de Interés Nominal 
Una tasa de interés nominal es aquella que denota un crecimiento en el monto del dinero sin ajustar la moneda por al inflación. De esta forma la tasa de interés nominal no refleja necesariamente un aumento en el poder adquisitivo.

#### Tasa de Interés Real
Si denota un cambio en el poder adquisitivo, ya que es aquella tasa de interés que si toma en cuenta el reajuste de la moneda, es decir si se realiza un deposito, al cabo de un año debería tener el mismo poder adquisitivo que poseía en el momento que invertí. Esto quiere decir que se ajusta el monto monetario a la inflación de la moneda y luego se aplican las tasas de interés. Un ejemplo clásico de las tasas de interés real son aquellas que son tramitadas en UF mas cierto porcentaje  x% de interés.

#### Igualdad de Fisher 
La igualdad de fisher nos permite obtener la relación entre el interés real e interés nominal y calcular uno u otro a partir del que se nos entregue. Dicha igualdad se define como: 
$$ (1 + r_{nominal}) = (1+r_{real})* (1 + \pi)$$
En la ecuación anterior $\pi$ refiere a la inflación esperada, luego podemos utilizar la ecuación anterior para despejar las tasas de interés reales y nominales.

#### Conversion de Tasas
$$r_{nominal} = (1+ r_{real})*(1+\pi) - 1$$
$$i_s =\frac{(1+i_c)^n -1}{n}$$
$$(1+ r_{anual}) = (1 + r_{mensual})^{12}$$
#### Tasa Efectiva V/S Tasa Aparente (Vencidas o Anticipadas)
Las tasas vencidas son aquellas en las cuales el interés asociado a la misma tasa se paga al final del periodo establecido, es decir si tenemos un interés de un cierto porcentaje $x\%$ en un plazo de 30 días, este se pagaría en el día numero 30 del periodo es decir al final. Su contra parte serian las tasas anticipadas, dichas tasas se pagan al inicio del periodo, tomando como ejemplo el caso anterior en vez de pagar en el día 30 la tasa de interés, esta se pagaría en el día 1. 
\
Ahora bien las tasas Efectivas y Aparentes son aquellas en las cuales comparamos la tasa impuesta v/s las veces que la misma se capitaliza (se divide y cobra) es decir pongamos el ejemplo que tenemos una tasa aparente del 12% anual si cobraríamos dicha tasa 12 veces tomando como referencia cada mes del año tendremos que hacer el siguiente calculo:
$$ \frac{\text{Tasa de Interes en el periodo}}{\text{Cantidad de veces que se capitaliza}} = \text{Interes por Capitalizacion}$$
Notemos que también se puede reescribir la formula anterior de la forma: 
$$\frac{\text{Tasa de interes en el periodo}}{n} = r$$
Si tomamos los datos anteriores y lo aplicamos a la formula del interés compuesto dada por: 
$$C_n = C_0 * (1 + r)^n$$
Viendo únicamente la parte del interés $(1+r)^n$ tendremos lo siguiente:
$$\frac{12\%}{12}= 1\%$$
Luego reemplazando en la formula del interés compuesto tendremos
$$\begin{align}
	(1+0.01)^{12}&=x\\
	12\%&=x
\end{align}$$
Por lo tanto luego nuestra tasa aparente coincide con nuestra tasa efectiva. Pero ¿Que pasaría ahora, si en vez de capitalizar la tasa aparente 12 veces lo hiciéramos únicamente 3? Calculemos entonces la tasa efectiva al capitalizar únicamente 3 veces el interés: 
$$\frac{12\%}{3}=4\%$$
Luego apliquemos esto a la formula del interés compuesto:
$$\begin{align}
	(1 + 0.04)^{3}&=x\\
	12.48\%&=x
\end{align}$$
De esta forma podemos ver que al capitalizar un numero de veces distinta puede llevar a que la Tasa Aparente difiera de la Tasa real. Como nota para calcular el interés lo que realizamos es básicamente sacar el calculo de $(1+0.04)^3$ Lo que resulta en $1.1248$ luego tomamos en cuenta $1.1248 - 1 =0.1248$  lo que al pasar en porcentajes da el resultante $12.48\%$

