# Teórico: Máquinas de Turing - 2017

Este apunte es una guía para el docente.

## Disparador

* qué es una computadora? qué significa programar?
* qué puede calcular una computadora?
  hay cosas que *no* se pueden calcular con una computadora?
* sorprendentemente, hay gente que pudo contestar a
  esta útima pregunta pero sin tener ninguna computadora a mano
* de hecho contestó antes de que se fabricará la primera
  "computadora" (tal como las que conocemos hoy)

## Computadoras primitivas

* antes del siglo 20, se fabricaron unas "computadoras"
  en épocas distintas
* [Calculadora de Blas Pascal](https://es.wikipedia.org/wiki/Pascalina)
* [Mecanismo de Anticitera](https://es.wikipedia.org/wiki/Mecanismo_de_Anticitera)
* [El Turco](https://es.wikipedia.org/wiki/El_Turco)
* [Máquina Analítica de Babbage](https://es.wikipedia.org/wiki/M%C3%A1quina_anal%C3%ADtica)
* pero no son computadoras, son más bien automatas o
  calculadoras, porque hacen solo 1 tipo de cálculo
  o una acción, y no puede salir de esa función
* una computadora es una máquina programable que
  puede hacer cualquier cálculo
* hoy en día, los teléfonos celulares por ejemplos son computadoras
  porque les podemos instalar cualquier aplicación

## Alan Turing y sus máquinas

* matemático inglés
* en el 1936 publica el artículo: "Sobre los números calculables"
  ("On computable numbers").
* no había computadoras en esa época
* presenta sus "máquinas de cálculo"
* [Máquina de Turing](https://es.wikipedia.org/wiki/M%C3%A1quina_de_Turing)

## El Juego de Turing

Vamos a definir "programas" que también podemos llamar
"máquinas de Turing". Un programa se puede ejecutar.

Cuando una máquina se ejecuta, los efectos de esa ejecución
tienen consecuencias concretas.

Primero, la máquina tiene un estado interno, que puede
cambiar durante la ejecución. Es un valor que sirve para
representar en qué etapa del cálculo estamos.

Segundo, la máquina tiene acceso a una cinta donde puede
leer y escribir símbolos. Esa cinta es parecida una cinta
de papel, pero tiene diferencias importantes. Es constituida
de casillas, y solo se puede escribir un símbolo dentro de
cada casilla (un poco como en un formulario). También se puede
escribir un símbolo distinto en una misma casilla, en cual caso
el símbo anterior es reemplazado. Otra diferencia de esa cinta,
es que es *infinita* en las dos direcciones. No se olviden
que una máquina de Turing es un objeto matemático, así que
tenemos el derecho de decir que la cinta es infinita!

Para terminar ese recorrido, tenemos que hablar del *cabezal*
de la máquina. El cabezal
está siempre frente a alguna casilla. El cabezal se puede mover,
pero solamente a la casilla de al lado, hacia la izquierda o hacia la derecha.
El cabezal solo se entera del símbolo que está en la casilla que tiene al frente.
Y puede escribir algun símbolo en esa misma casilla.

Bien, ahora veamos las reglas del juego:

* fijar un conjunto de símbolos que vamos a usar,
  y decir con qué símbolo la cinta está rellenada inicialmente
* fijar un conjunto de estados internos de la máquina
* definir una máquina. una máquine es definida con reglas,
  que podemos presentar como una tabla (llamada "tabla de transiciones").

En esta clase los símbolos que usamos para escribir en la cinta son 0 y 1,
y la cinta está inicialmente rellenada de 0.

Vamos a empezar pensando en máquinas con solo 2 estados internos, "a" y "b",
despues vamos a agregar más estados.

Ahora, la tabla de transiciones es un conjunto de reglas de la forma siguiente:

* para cada símbolo leido en la cinta por el cabezal
* y para cada estado interno en el cual la máquina se encuentra
* entonces hay una única *instrucción* que la máquina debe ejecutar.

Hay dos tipos de instrucciones:

* Tipo 1: "FIN": la máquina termina su ejecución
* Tipo 2: hacer lo siguiente:
    * escribir un símbolo
    * mover el cabezal (a la izquierda o a la derecha)
    * modificar el estado interno
    * seguir la ejecución de la máquina

## Ejemplo

Esto es una máquina:

~~~
  | 0 | 1 |
a |1→b|1←a|
b |1←a|FIN|
~~~

Arrancamos con una cinta blanca, y vemos su ejecución (pizarrón).

## Cómo representar la ejecución de una máquina en hoja de papel

* la cinta es de tamaño infinito pero sabemos que es todo 0 así
  que no hace falta escribir mucho
* representamos la posición del cabezal con un triangulito
* escribimos el estado actual de la máquina abajo del triangulito
* siempre empezamos con cinta blanca y el estado "a":


~~~
...000...
    ^
    a
~~~

* escribamos cada configuración abajo de la otra:

~~~
...000...
    ^
    a
...0100...
     ^
     b 
...0110...
    ^
    a
...0110...
   ^
   a
..01110...
    ^
    b
FIN
~~~

## Escritura compacta de una traza

~~~
0a
10b
1a1
0a11
11b1
FIN
~~~

## Preguntas: máquinas que no terminan

1. ¿Qué podemos decir de una máquina que no usa
   la instrucción "FIN"?
2. ¿Qué podemos decir de una máquina que tiene
   instrucciones como sigue:

~~~
  | 0 | 1 |
a |1→a|...|
b |...|...|
~~~

3. Y la siguiente:

~~~
  | 0 | 1 |
a |..a|...|
b |...|...|
~~~

## Observación: Terminar o no terminar

* Se puede clasificar las máquinas en 2 familias:
  las que terminan en algun momento, y las que no
* Hay máquinas que no terminan por razones obvias
* Pero hay máquinas que no terminan sin que sea claro
  por qué (comportamiento complejo).

## La campeona de la categoría "4 estados" 

También, hay máquinas que terminan después de muchos
pasos, por ejemplo:

~~~
  | 0 | 1 |
a |1→b|1←b|
b |1←a|0←c|
c |FIN|1→d|
d |1→d|0→a|
~~~

Termina después de 107 pasos (es la máquina con
4 estados que tiene más aguante).

## La campeona de la categoria "5 estados"

~~~
  | 0 | 1 |
a |1→b|1←c|
b |1→c|1→b|
c |1→d|0←e|
d |1←a|1←d|
e |FIN|0←a|
~~~

Termina después de 47.176.870 pasos.

No se sabe si hay otra máquina terminante de 5 estados
más aguantadora. (Actualización: en el 2024
[se demostró que](https://www.quantamagazine.org/amateur-mathematicians-find-fifth-busy-beaver-turing-machine-20240702)
no había otra máquina más aguantadora, es decir esta es
la campeona de su categoría.)

## Máquinas que hacen cosas útiles

Las máquinas pueden hacer sumas, multiplicaciones, etc.
si ponemos en la cinta los datos de entrada. 

## Bien, ¿cuál es la relación con el resto de la materia?

* No vamos a usar máquinas de Turing para programar,
  sino un lenguaje de programación que se convierte
  automáticamente a instrucciones similares a las de
  máquinas de Turing
* Esas instrucciones son ejecutadas por
  las computadoras del laboratorio

~~~
+-----------------------------------+----------------------+
| editar código en lenguaje C       |  resultado visible   |
+-----------------------------------+----------------------+
| convertir código en instrucciones | resultado "invisible"|
+-----------------------------------+----------------------+
~~~


* Un programa común se representa con millones de instrucciones
  (nosotros jugamos con máquinas de hasta 8 instrucciones)
* Ya que es difícil analizar bien una máquina de Turing,
  es más difícil analizar una aplicación o software
* Por eso instalar aplicaciones desde fuentes seguras
  (evitar viruses o software con malas intenciones)

## Proxima etapa

* vamos a descubrir como usar la computadora
  (ya no vamos a programar sobre papel sino editar
   archivos en la computadora)

## Links útiles

* <https://turingmachinesimulator.com/> para mostrar animación de MT con input 
