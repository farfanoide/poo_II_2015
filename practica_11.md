
Orientación a Objetos 2 -Práctica 11
====================================



Ejercicio 1: Una Red Social
-------------------------------------

Sea la pequeña aplicación de red social que se utilizó en las clases teóricas. Además del modelo, la aplicación incluye
vistas web, utilizando el framework Seaside y un vista desktop desarrollada con el framework de GUIs Morphic. Esta
vista utiliza dependencias para actualizarse cada vez que se agregan nuevos usuarios en la red social vía la interfaz
web.

Instale la aplicación siguiendo los pasos que se detallan en las instrucciones de la teoría. Luego evalúe en un works-
pace la expresión ´´´SocialNetworkMorphicView new open´´´ para abrir la vista Morphic.

Tareas:


  1. Lea los comentarios de los métodos de ´´´Object´´´ contenidos en las categorías: dependencies y updating. Luego
implemente en papel y conteste:


    a)¿Mediante qué mensaje un objeto declara que es dependiente de otro?
    
    b)¿Con qué mensaje un objeto indica que ya no es dependiente de otro?
    
    c)¿Qué mensaje debe implementar para que un objeto actúe ante una notificación?
    
    d)¿En qué clases encuentra implementaciones de dichos mensajes? ¿En que difieren dichas implementaciones?
    
  2. Realice el diagrama de clases UML de la aplicación tal como se obtiene del repositorio.
  
  3. Analice el código y evalúe cómo debería extenderse para que la vista Morphic se actualice cada vez que en
la aplicación web se indica que un usuario pasa a ser seguidor de otro. Realice el diagrama de secuencia que incluya los cambios propuestos.

4. Implemente esos cambios y compruebe el funcionamiento.

5. Revise el funcionamiento de la aplicación cuando se hace clic en “Reset” en la interfaz web. La ventana de la
aplicación Morphic no se mantiene actualizada. ¿Qué cambios deberían realizarse para que la ventana Morphic
se mantenga actualizada cuando en la aplicación web se hace clic en “Reset”? Implemente en el código

6. Actualice el diagrama de clases si es necesario.




Ejercicio 2: Monitoreo del estado de una computadora
-------------------------------------

Se desea modelar un software que permita monitorear y visualizar distintos parámetros del funcionamiento de
una Computadora: temperatura de la CPU, velocidad de los coolers, espacio disponible en los discos rígidos, etc.
Para realizar la medición de los valores, cada componente actualiza de forma automática una instancia de la clase
´´´Computadora´´´ donde existen diferentes variables de instancia con sus correspondientes accessors para cada uno de
los parametros medidos. Por otro lado, para la visualización de los datos se dispone de un conjunto de Widgets que
se describen a continuación:

Estas clases no pueden ser modificadas ya que pertenecen a una libreria que no es mantenida por usted.
En base a lo mencionando anteriormente, para el monitoreo se requiere diseñar el concepto de ´´´Tablero´´´ responsable
de coordinar la sincronización de las actualizaciones que subre la instancia de la computadora con los Widgets.

Tareas:


1. Diseñe una solución donde los cambios de los datos en la clase ´´´Computadora´´´ sean percibibles mediante los
Widgets mencionados.

2. Realice un diagrama de clases UML donde se documente claramente la relación entre los componentes, los
valores medidos y las representaciones visuales para los mismos.

3. Realice un diagrama de secuencia para el caso en que hay 2 vistas (un ´´´Label´´´ y un ´´´Velocímetro´´´) de la
temperatura de la CPU y ésta cambia.


