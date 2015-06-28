Orientación a Objetos 2 -Práctica 10
====================================



Ejercicio 1: Lea la bibliografía y responda
-------------------------------------


1. Lea la siguiente bibliografía (encontrará enlaces a las versiones online en el sitio de la materia) y los slides de
la clases de reuso y frameworks.

  - Roberts, Don, and Ralph Johnson. Evolving frameworks: A pattern language for developing object-oriented frameworks. Pattern languages of program design 3, 1996, pp. 471 a 486.

  - W. Pree, Hot-spot-driven framework development, in Summer School on Reusable Architectures in Object-Oriented software Development, 1995, pp. 123 a 127

  - M. E. Fayad, D. C. Schmidt, and R. E. Johnson, Building Application Frameworks: Object-oriented
  
  - Foundations of Framework Design. New York, NY, USA: John Wiley Sons, Inc., 1999. Capítulo 1 - Introducción
  
  
2. Responda a las siguientes preguntas:

  a) Desde la perspectiva de quien hace el framework, ¿qué implica optar por whitebox o blackbox? Piense
por ejemplo en las facilidades y las dificultades que encuentra en cada caso.


  b) Desde la perspectiva de quien usa el framework, ¿qué implica optar por whitebox o blackbox? Piense por
ejemplo en las facilidades y las dificultades que encuentra en cada caso.


  c) Los conceptos de template y hook (plantilla y ganchos) los encontramos en el template method, en el
marco de una relación entre una clase y sus subclases. También se lo puede encontrar en una relación de
composición. Ambas situaciones son comunes en los hotspots de un framework. ¿De qué manera afecta
cada una de esas alternativas (subclasificación o composición) al comportamiento runtime de las aplica-
ciones que instancia el framework/hostpot?




Ejercicio 2: Usar un framework de caja blanca
-------------------------------------

Sea el pequeño framework visto en las clases de teoría y que se provee como material adicional a esta práctica.
Este framework abstrae la funcionalidad para “monitorear el contenido del clipboard” y está compuesto por las
siguientes clases: ```ClipboardMonitor``` (clase abstracta que modela el monitoreo del contenido del clipboard y
lo consume) y ```TranscriptLoggingClipboardMonitor``` (subclase de la anterior que imprime el contenido
del clipboard al Transcript). Lea detenidamente los comentarios de ambas clases.
El objetivo de este ejercicio es utilizar este framework para construir la aplicación que imprima en el Transcript solamente cuando el contenido del clipboard cambia (```ChangeLoggingClipboardMonitor ```). Utilice los criterios de instanciación de frameworks de caja blanca vistos en la teoría y extienda la funcionalidad provista para escribir una nueva línea en el Transcript sólo cuando el contenido haya cambiado y almacene cada
contenido nuevo como elemento de una colección.

Tareas:

  - Responda:

    • ¿qué necesita conocer del framework para poder instanciarlo por herencia?
    • ¿En qué parte del framework se produce la inversión de control?
    • ¿Cuáles son los hotspots y frozenspots del framework?
  
  
  - Realice el diagrama de clases de la aplicación completa, incluyendo las clases del framework.

  - Implemente su aplicación

  - Instancie su aplicación en un workspace para monitorear el clipboard cada 10 segundos




Ejercicio 3: Framework de caja negra
-------------------------------------


En este ejercicio deberá extender el framework del ```ClipboardMonitor``` para que pueda ser utilizado como
caja negra.
Como vio en la teoría, al instanciar el framework como caja blanca necesitamos una nueva subclase para cada
tipo de consumo que queremos hacer del contenido. Para evitar eso, vamos a extender el framework con un
monitor configurable que pueda servir para todos los casos.

Tareas:

  - Responda

    • ¿cuáles son las diferencias con el ejercicio anterior respecto de lo que los desarrolladores de aplicaciones necesitarán conocer de su framework?

  - Agregue al framework la clase ```PluggableClipboardMonitor``` que puede ser instanciada y utilizada como monitor configurable. En la instanciación de un ```PluggableClipboardMonitor``` deberá poder
indicarse: el sujeto (a quién le tiene que avisar), una condición (para que no avise siempre), el selector
(qué mensaje tiene que enviar) y la frecuencia de chequeo del clibpoard.


  - Desarrolle la misma aplicación que en el ejercicio anterior para imprimir en el Transcript sólo cuando el
contenido del clipboard haya cambiado y almacenar cada nuevo contenido en una colección, pero ahora
utilice la versión caja negra del framework que acaba de crear.


  - Instancie en un workspace para chequear cada 10 segundos

