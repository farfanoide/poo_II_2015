Orientación a Objetos 2 -Práctica 9
====================================

Ejercicio 1: SUnit
------------------

En los prácticos anteriores hemos estado utilizando el framework SUnit para
desarrollar aplicaciones que nos permitan testear la funcionalidad de nuestro
código. Para realizar este ejercicio puede leer el artículo escrito por
S.Ducasse que se adjunta como material adicional y repasar el código de SUnit.

Revise el código de de SUnit y documente:

  - los hotspots y los frozenspots

    > Los hotspots que encontramos son: setUp y tearDown que no estan definidos
    > en la clase.

    > Los frozenspots son: son los metodos implementados en el mismo framework
    > como por ejemplo #cleanUpInstanceVariables.

  - dónde se produce la inversión de control

    > La inversion de control se produce en los hotsposts, cuando el framework
    > invoca nuestro código.

  - dónde se utiliza Template Methods en SUnit y su relación con los hotspots del framework.

    > El Template Methods en SUnit se utiliza en el metodo #runCase.  La
    > relación con los hotsposts es que los invoca provocando la inversion de
    > control.

  - qué parte del framework necesita conocer en profundidad para poder
      utilizarlo. Hay alguna parte del SUnit que no necesita conocer para poder
      utilizarlo?

  > La parte del framework que se necesita conocer en profundidad para poder
  > utilizarlo es, los metodos de la clase TestAsserter, que estan agrupados
  > por el protocolo asserting.

  > Las partes que no son necesarias conocer en el framework son los metodos
  > privados de SUnit o que no son hotspots.


Ejercicio 2: Aplicación para una Vending Machine
------------------------------------------------


Tomando como base el trabajo desarrollado para el ejercicio de la Vending
machine en el TP 03 realice las siguientes tareas:

  - Tome como base los diagramas de la teoría 1 de Frameworks (slides 26 a 30)
      y documente:

    • las librerías de clases que reutilizó para la implementación del modelo

    • el reúso del framework SUnit para la parte de la aplicación que testea el
    modelo. Indique qué parte de SUnit se hereda para su aplicación de testing.
    Qué hotspot utilizó? Hay otros que no utilizó? Cuáles? Por qué no los usó?


  - Realice un diagrama de secuencia donde se muestre cómo se ejecutan sus
      casos de prueba y cómo se produce la inversión de control por parte de
      SUnit.
