Orientación a Objetos 2 -Práctica 5
====================================

Ejercicio 1:  Refactoring
-------------------------------------

Indique si cada una de las siguientes aseveraciones es verdadera o falsa. Explique.

  1. Cuando un código es refactorizado cambia su comportamiento agregando más funcionalidad.
  
  2. Si el código está bien refactorizado no es necesario testearlo.
  
  3. Después de ser refactorizado, la estructura interna del código permanece igual que antes.
  
  4. La refactorización del código se hace en un sólo paso en el que se unen todos los cambios
  



Ejercicio 2: Software con olores
-------------------------------------


Responda:

  1. Qué significa la expresión “código con mal olor” según lo visto en la teoría?.
  
  2. Encuentre tres casos de los “malos olores” explicados en la teoría en su propio código de los prácticos anteriores.
  
  3. Indique tres razones por las cuales es importante hacer refactoring.
  
  
  
Ejercicio 3: Algo huele mal
-------------------------------------

Indique en los siguientes ejemplos la presencia de malos olores.

  1. El diagrama de la figura 1 muestra que existen dos métodos en diferentes subclases que realizan algunos pasos
similares en el mismo orden, aunque los pasos difieren entre sí. Aplicando lo que ya conoce de patrones, ¿cómo
puede mejorar el diseño y el código? Realice el nuevo diagrama de clases.

Utilice el código que se entrega en el material adicional de la práctica. Verifique que el código original, que res-
ponde al diagrama de clases de la figura pasa exitosamente los test cases. Haga las modificaciones que se piden
al diseño, implemente los cambios al codigo de las clases Inmueble, ViviendaUnica y CasaFinDeSemana.
Verifique que el nuevo código también pasa exitosamente los tests.




  2. La clase Cliente tiene el siguiente protocolo público. ¿Cómo puede mejorarlo?
  
# lmtCrdt devuelve el límite de crédito del cliente.

# mtFcE: unaFecha y: otraFecha devuelve el monto facturado al cliente desde unaFecha hasta otraFecha

# mtCbE: unaFecha y: aux devuelve el monto cobrado al cliente desde unaFecha hasta otraFecha


  3. Al revisar el siguiente diseño inicial (figura 2), se decidió realizar un cambio para evitar lo que se consideraba
un mal olor. El diseño modificado se muestra en la figura 3. Indique qué tipo de cambio se realizó y si lo
considera apropiado. Justifique su respuesta.




  4. Analice el código que se muestra a continuación. Indique qué defectos encuentra y cómo pueden corregirse.
  
  
  ```
  # imprimirValores
    |totalEdades promedioEdades totalSalarios|
    totalEdades := 0.
    totalSalarios := 0.
    personal do: [ :empleado | totalEdades := totalEdades + empleado edad.
                              totalSalarios := totalSalarios + empleado salario].
    promedioEdades := totalEdades / personal size.
    Transcript show: ’Edad promedio: ’ , promedioEdad printString ,’ - Total de salarios: ’ , totalSalarios         printString.
  ```

