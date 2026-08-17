# Práctico: Máquinas de Turing

## 1. Ejecución de Máquinas de Turing

![cantidad de participantes](group64.png){width=1cm} De 1 a 3 participantes.

Ejecutar las máquinas siguientes. Cuál es el estado final de la cinta?
Cuántos pasos dura la ejecución?

1. 
~~~
  | 0 | 1 |
a |1>b|1<a|
b |1<a|FIN|
~~~

2.
~~~
  | 0 | 1 |
a |1>b|0<a|
b |FIN|0<a|
~~~

3.
~~~
  | 0 | 1 |
a |0>b|1<a|
b |1<a|FIN|
~~~

4.
~~~
  | 0 | 1 |
a |1>b|1<a|
b |0<a|FIN|
~~~

5.
~~~
  | 0 | 1 |
a |1>b|1<a|
b |1>c|0>c|
c |1<a|FIN|
~~~

6.
~~~
  | 0 | 1 |
a |1>b|0<c|
b |0>c|1>c|
c |1<a|FIN|
~~~

7.
~~~
  | 0 | 1 | 2 |
a |1>b|1<b|FIN|
b |2<a|2>b|FIN|
~~~


## 2. Máquinas Extrañas


![cantidad de participantes](group64.png){width=1cm} De 1 a 3 participantes.

Ejecutar las máquinas siguientes. Qué problema tienen?
Pueden describir lo que pasa en cada caso?

1.
~~~
  | 0 | 1 |
a |1>b|1>b|
b |1>a|FIN|
~~~

2.
~~~
  | 0 | 1 |
a |1>a|0<b|
b |1<a|FIN|
~~~

3.
~~~
  | 0 | 1 |
a |1>b|0>b|
b |0<a|FIN|
~~~

4.
~~~
  | 0 | 1 | 2 |
a |1>b|1<b|FIN|
b |2<a|2>b|1<b|
~~~

## 3. Escritura compacta de ejecución

![cantidad de participantes](user64.png){width=1cm} 1 participante.

Como en el ejercicio 1, ejecutar las máquinas siguientes, pero
usando la escritura compacta de la traza de ejecución.

1.
~~~
  | 0 | 1 |
a |1>b|1<c|
b |1>c|FIN|
c |1<a|0<b|
~~~

2.
~~~
  | 0 | 1 |
a |0>b|FIN|
b |0<c|1>a|
c |1>b|1<c|
~~~

## 4. Escritura compacta de ejecución.. infinita

![cantidad de participantes](user64.png){width=1cm} 1 participante.

Estas máquinas tienen una ejecución infinita.

Escribir la traza de ejecución de cada una
hasta que quede claro que la ejecución no termina nunca.

1.
~~~
  | 0 | 1 |
a |1>b|FIN|
b |0>c|0>a|
c |1<a|FIN|
~~~

2.
~~~
  | 0 | 1 |
a |1>b|1<a|
b |1<a|1>c|
c |FIN|1>a|
~~~

3.
~~~
  | 0 | 1 | 2 |
a |1>b|1<a|2>b|
b |0<a|2>a|FIN|
~~~
