Orientación a Objetos 2 -Práctica 3
====================================

Ejercicio 1: Adaptadores de recorrido
-------------------------------------

A diferencia del paradigma estructurado, en la programación orientada a objetos las estructuras como los árboles o los grafos no se suelen modelar explícitamente, sino que surgen como resultado de las relaciones de conocimiento entre objetos.A modo de ejemplo, tomemos el caso de un FileSystem. 

En Pharo un File System es accedido por medio de la clase
FileReference, que implementa el mensaje ```#children```. Este mensaje retorna una colección con los nombres de archivos y subdirectorios del objeto receptor.
Luego, a pesar de que un File System tiene una estructura de árbol, no es necesario modelar una clase "Arbol" ya que la estructura se deriva de las relaciones entre los objetos. En este ejercicio usted deberá implementar la
clase TreeCollector. 

Un TreeCollector se utiliza para recorrer cualquier red de objetos que posea una estructura de árbol subyacente. Para esto un TreeCollector se instancia con el mensaje ```#block:aBlock``` y reconoce los mensajes: ```#preOrderCollect:aTree```, ```#inOrderCollect:aTree``` y ```#postOrderCollect:aTree```. 
Cada uno de estos mensajes recorre la estructura de árbol (siguiendo los algoritmos correspondientes de pre-order, in-order y post-order) y al pasar por cada nodo evalúa el bloque con el nodo actual como parámetro. Cada mensaje retorna una colección, con el resultado de evaluar el bloque en cada nodo del árbol. Por ejemplo, el código para pre-order pueder
algo similar a:

```smalltalk
TreeCollector>>preOrderCollect: aTree
  result:= OrderedCollection new.
  self preOrderCollect:aTree with:result.
  ^result

TreeCollector>> preOrderCollect:aTree with:result
  result add: (self block value: aTree).
  aTree contents do: [:subtree| self preOrderCollect: subtree with:result] .
```


   1. Implemente los test cases para la clase TreeCollector que verifiquen el
   buen funcionamiento del protocolo público. Para independizarse del caso
   concreto en el que el TreeCollector vaya a ser aplicado, cree una clase
   MockTree que entienda el mensaje #children retornando una colección
   (probablemente vacía) de árboles hijos y donde cada nodo tenga asociado un
   valor numérico. Esto último le permitirá testear el orden en el que se
   realizan los recorridos.

   2. Implemente la clase TreeCollector.

   3. Aplique el pattern Adapter para poder utilizar un TreeCollector sobre el árbol que representa la jerarquía de clases de Smalltalk, empezando por Object. Para obtener las subclases de una clase, se le envía el mensaje
   ```#subclasses```. Por ejemplo, Collection subclasses retorna las subclases directas de la clase Collection.

   4. Aplique el pattern adapter para poder utilizar un TreeCollector sobre la
   estructura de directorios a partir de c:/temp.


Ejercicio 2: Vending machine
----------------------------

Considere una máquina vendedora de botellas de agua sin gas. La misma conoce el
precio de la botella y tiene un cierto stock (cantidad de botellas). La máquina
acepta monedas de 0.50, 1 y 2 pesos y también puede dar vuelto. Su
funcionamiento es muy sencillo:

  - El cliente indica la cantidad de botellas que desea comprar.
  - Si la cantidad excede al stock la máquina lo informa y termina la venta.
  - Caso contrario, la máquina informa el monto total y espera a que el cliente
    ingrese el dinero.
  - El cliente ingresa las monedas hasta igualar o superar el monto total.
  - Si el monto supera al monto total, la máquina calcula el vuelto que debe
    entregar.
  - Si no dispone del cambio necesario, devuelve las monedas al cliente y
    finaliza la venta.
  - Caso contrario, entrega los productos y el vuelto.

Tenga en cuenta que el cliente puede cancelar la compra en todo momento y la
máquina devuelve el dinero ingresado. Además, considere las siguientes
situaciones:

  - La máquina no acepta dinero antes de que se indique la cantidad de botellas
    que se desean comprar.
  - La máquina no acepta indicar la cantidad de botellas a comprar cuando está
    aceptando dinero.

Considere que la máquina posee un display (para nuestro caso el Transcript) y
los anuncios lo hace a través del mismo. Preste atención a los siguientes
métodos y respecto de la funcionalidad de entregar las botellas y el vuelto,
solo actualice el stock y dinero que posee la máquina.

```smalltalk
  #comprar: cantidadDeBotellas
    "Define la cantidad de botellas que el cliente desea comprar. Devuelve true
    si es posible hacer la compra, false caso contrario. "
```

```smalltalk
  #costoTotal
    "Devuelve el monto total que el cliente debe pagar."
```

```smalltalk
  #ingresar: unaMoneda
    "El cliente ingresa en la máquina una moneda de la denominación indicada.
    Devuelve true cuando alcanzó o superó el costo de la compra, false en caso
    contrario."
```

```smalltalk
  #dineroRestante
    "Devuelve el dinero que aún resta por pagar."
```

```smalltalk
  #poseeVuelto
    "Retorna si la máquina posee el dinero suficiente para dar el vuelto."
```

```smalltalk
  #confirmarCompra
    "Una vez que el dinero fue ingresado, el cliente confirma que desea hacer
    la compra. La máquina actualiza el stock y el dinero. "
```
```smalltalk
  #cancelarCompra
```

Tareas:

   1. Analice los cambios de estados y en que estado tienen sentido las operaciones indicadas.
   2. Diseñe la solución para proveer la funcionalidad descripta.
   3. Diseñe casos de prueba.
   4. Implemente la clase VendingMachine y los casos de prueba
   


> Solucion Fran:
  [Paquete Ejercicio 2](src/p3 francisco/P3E2.st)



Ejercicio 3: Calculadora
------------------------


Sea la clase Calculadora con los siguientes mensajes:

```#resultadoParaMostrar ```
que retorna el valor acumulado en la operación actual de la calculadora en forma de String (los números entienden el mensaje printString).

```#borrar ```
vuelve a cero el valor acumulado.

```#valor: unValor```
asigna el valor acumulado.

```#mas``` provoca que la calculadora espere un nuevo valor. Si a continuación se le envía el mensaje #valor: la
calculadora sumará el valor recibido como parámetro al valor actual acumulado y guardará el resultado en esta
última.

Si la calculadora está esperando un valor y se le envía cualquier otro mensaje, entonces pasará a un estado de error.
Sólo saldrá de ahí si se le envía el mensaje ```#borrar```. Los mensajes ```#menos```, ```#dividido``` y ```#por``` actúan de manera similar al mensaje ```#mas```.
Cuando la calculadora está en estado de error, el mensaje ```#resultadoParaMostrar``` retorna el string Error. La
calculadora también entra en este estado si se intenta dividir por cero.

Tareas:

   1. Analice los cambios de estado y documéntelos mediante un diagrama de estados UML.
   2. Diseñe la aplicación calculadora para proveer la funcionalidad antes descripta. Utilice un diagrama de clases

       completo indicando qué patrón aplica para que el diseño quede extensible, claro y modificable. Indique lo roles
       de las clases mediante estereotipos.
   3. Realice un diagrama de secuencia para el mensaje #valor: con la calculadora en estado de espera de un valor
       para efectuar una suma.
   4. Implemente en Smalltalk completamente




Ejercicio 4: Patrón State
-------------------------------------


Lea el capítulo del patrón State en el libro Design Patterns y responda:

   1. ¿Cuándo es necesario usar el patrón State?
   2. ¿Qué representa el contexto dentro del patrón State?
   3. ¿Puede el estado concreto acceder al contexto?
   4. ¿Quién define las transiciones entre estados?




Ejercicio 5: Lea el pattern Template Method y ...
-------------------------------------


(Puede leer el patrón desde el archivo templateMethod.pdf) .

   1. Responda:
              ¿Dónde se define el esqueleto del algoritmo?
              ¿Se puede redefinir el esqueleto?
              ¿Qué es lo que se puede redefinir?
              ¿Qué es un hook method?

   2. Busque un ejemplo de aplicación del pattern en:
              Clase #Magnitude categoría #comparing
              Clase #Collection categoría #accessing

   3. Busque dos ejemplos más de uso del patrón en Smalltalk.
   4. Para cada uno de los cuatro ejemplos de los dos ejercicios anteriores, realice un diagrama de clase indicando:

              La clase abstracta.
              El template method.
              Al menos 2 clases concretas.
              Los hook methods.




Ejercicio 6: Template hasta en la sopa (o el café)
-------------------------------------


Mucha gente no puede vivir sin su café o su té matinal, ni hablar del chocolatada de la tarde. El proceso de pre-
paración de cada uno es:

       ¿Cómo preparar un café? Calentar agua, poner café en la taza, agregar azúcar y leche, verter el agua en una
       taza.
       ¿Cómo preparar un té? Calentar agua, poner el saquito de té en la taza, agregar azúcar y limón, verter el agua
       en una taza
       ¿Cómo preparar una chocolatada? Calentar la leche, poner cacao en la taza, agregar azúcar, verter la leche en
       una taza.

   1. Defina 3 clases: Café, Té y Chocolatada e implemente en cada una de ellas el método #preparar.
   2. Vea que el proceso de preparación es muy común para todas. Cree una clase abstracta de la cual extienden las

       3 clases definidas anteriormente y factorice en la clase abstracta todo el código que le sea posible.




Ejercicio 7: Fábrica de vehículos
-------------------------------------

Independientemente de si el vehículo va por aire, agua o tierra, posee básicamente la misma línea de construcción.

       Auto: a un chasis se le incorpora una planta motriz y una dirección.
       Avión: a un fuselaje se le incorporan turbinas y alerones.
       Velero: a un casco se le incorporan los mástiles de las velas y un timón

   1. Defina 3 clases: Auto, Avión y Velero e implemente en cada una de ellas el método #construir, factorizando
       en la clase Vehículo el código que sea posible.

   2. Indique que otros elementos forman parte de estos vehículos. Por ejemplo: freno, freno de estacionamiento,
       anclas, etc.

   3. Extienda el la solución para incorporar los elementos indicados en el punto anterior.
