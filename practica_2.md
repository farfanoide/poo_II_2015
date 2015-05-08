Orientación a Objetos 2 – Práctica 2
====================================

Ejercicio 1: Patrón Adapter
-----------------------

Lea el capítulo 4 del libro Design Patterns de Gamma et al. y responda a las
siguientes preguntas:

1. ¿Qué es un patrón estructural?

2. El capítulo menciona dos formas de implementar el patrón Adapter: como
   patrón estructural de clase y como patrón estructural de objeto. ¿Cuáles son
   esas dos formas? ¿Cuál de ellas no es implementable en Smalltalk? ¿Por qué?

  > Los patrónes estructurales se ocupan de cóme se conbinan las clases y los
  > objetos para formar estructuras mas grandes.  Los patrónes estructurales de
  > CLASES hacen uso de la herencia para componer interfaces o
  > implementaciones.

2. El capítulo menciona dos formas de implementar el patrón Adapter: como
   patrón estructural de clase y como patrón estructural de objeto. ¿Cuáles son
   esas dos formas? ¿Cuál de ellas no es implementable en Smalltalk? ¿Por qué?.


  > Patrón estructural de clase:

    >  - Adapta una clase Adaptable a Objetivo, pero se refiere únicamente a
    >    una clase Adaptable concreta. Por tanto un, un adaptador de clases no
    >    servira cuando lo que queremos es adaptar una clase y todas sus
    >    subclaes.

    > - Permite que Adaptador redefina parte del comportamiento de Adapter, por
    >   ser Adaptador una subclase de Adaptable.

    > - Introduce un solo objeto, y no se necesita ningun puntero de
    >   información adicional para obtener el objeto adaptado.

  > Patrón estructural de objeto:

    > - Permite que un mismo Adaptador funcione con muchos Adaptables, es
    >   decir, con el Adaptable en si y todas sus subclases, en caso de que las
    >   tenga.  El Adaptador también ṕuede añadir funcionalidad a todos los
    >   Adaptables a a vez.

    > - Hace que sea mas dificil de redefinir el comportamiento de Adaptable.
    >   Se necesitará crear una sublclase de Adaptable y hacer que el Adaptador
    >   se refiera a la subclase en vez de a la clase Adaptable en si.


Ejercicio 2: Adapter
-----------------------

Ud. ha implementado un exitoso cliente desktop que permite publicar en Facebook
su estado de ánimo. En su sistema la clase Facebook implementa el mensaje
`#post:`, donde recibe un string (sin límite de longitud) para ser publicado.

Dada la popularidad de Twitter ahora ud. desea que su cliente también permita
publicar en dicha red social. Lamentablemente se encuentra con 2 problemas:

Los tweets son strings de a lo sumo 140 caracteres.

La clase Twitter no entiende el mensaje `#post:` sino `#publish:`. También
recibe como parámetro un String.
Además, como su software funciona correctamente ud. desea introducir el menor
número posible de modificaciones.
A la vez, la clase Twitter pertence a una libría de terceros y no debería
modificarla.

Tareas:

1. Diseñe la aplicación original.
2. Discuta con el ayudante la inclusión del soporte a Twitter
3. Explique cómo el patrón resuelve los problemas planteados.
4. Implemente en Smalltalk.

Dada la popularidad de Twitter ahora ud. desea que su cliente también permita
publicar en dicha red social. Lamentablemente se encuentra con 2 problemas:

  - Los tweets son strings de a lo sumo 140 caracteres.

  - La clase Twitter no entiende el mensaje `#post:` sino `#publish:`. También
    recibe como parámetro un String.

Además, como su software funciona correctamente ud. desea introducir el menor
número posible de modificaciones.
A la vez, la clase Twitter pertence a una libría de terceros y no debería
modificarla.

Tareas:

  1. Diseñe la aplicación original.
  2. Discuta con el ayudante la inclusión del soporte a Twitter
  3. Explique cómo el patrón resuelve los problemas planteados.

  > Solucion Fran:
  [Paquete Ejercicio 2](src/p2 francisco/P2E2.st)


Ejercicio 3: Topografía
-----------------------

Un objeto Topografía representa la distribución de agua y tierra de una región
cuadrada del planeta, la cual está formada por porciones de “agua” y de
“tierra”. La figura 1a muestra el aspecto de una topografía formada únicamente
por agua, otra formada sólamente por tierra (fig. 1b) y una topografía mixta
(fig. 1c).

Una topografía mixta está formada por partes de agua y partes de tierra
(4 partes en total). Éstas a su vez podrían descomponerse en 4 más y así
consecutivamente.

![Figura 1: Distintas topografías](img/p2/topografias.png)

Como puede verse en los ejemplos, hay una relación muy estrecha entre la
proporción de agua o tierra de una topografía mixta y la proporción de agua o
tierra de sus componentes (compuestas o no). Por ejemplo:

  - La proporción de agua de una topografía sólo agua (fig. 1a) es 1.
  - La proporción de agua de una topografía sólo tierra (fig. 1b) es 0.
  - La proporción de agua de una topografía compuesta está dada por la suma de
    la proporción de agua de sus componentes dividida por 4.

En la figura 1c, la proporción de agua es: 0 + 1/4 + 1/4 + 0 = 1/2. La
proporción siempre es un valor entre 0 y 1.

1. Implemente las clases necesarias para que sea posible:

  - crear Topografías
  - calcular su proporción de agua y tierra
  - comparar igualdad entre topografías (dada por igual proporción de agua y
    tierra e igual distribución).

2. Instancie la topografía compuesta del ejemplo y pruebe la funcionalidad
   implementada mediante test cases.

> Nota: sólo se descomponen topografías para conseguir combinaciones. No es
> correcto construir una topografía compuesta por cuatro topografías del mismo
> tipo.

> Solucion:
  [Paquete Ejercicio 3](src/p2/PooP2E3.st)

> Solucion Fran:
  [Paquete Ejercicio 3](src/p2 francisco/P2E3.st)

  Ejercicio 4: Modele comportamineto de un FileSystem
-----------------------

Un file system contiene un conjunto de directorios y archivos organizados
jerárquicamente mediante una relación de inclusión. De cada archivo se conoce
el nombre, fecha de creación y tamaño en bytes. De un directorio se conoce el
nombre, fecha de creación y contenido (el tamaño es siempre 32kb). Modele el
file system y provea la funcionalidad para consultar de un directorio:

Código 1: Interfaz a implementar

```smalltalk
#tamanoTotalOcupado
  "Retorna el espacio total ocupado en KB, incluyendo su contenido."
```

```smalltalk
#listadoDeContenido
  "Imprime en el Transcript el listado del contenido del directorio"
```

Imprime en el Transcript el listado del contenido del directorio siguiendo el
modelo presentado a continuacion:

```
- Directorio A

--- Directorio A.1

------ Directorio A.1.1   3 archivos

------ Directorio A.1.2   2 archivos

--- Directorio A.2

- Directorio B "
```



```smalltalk
#archivoMasGrande
 "Retorna el archivo con mayor cantidad de bytes en cualquier nivel del
 filesystem contenido por directorio receptor"
```



```smalltalk
#archivoMasNuevo
 "retorna el archivo con fecha de creacion mas recienteen cualquier nivel del
 filesystem contenido por directorio receptor"
```

Tareas:

  - Diseñe y represente un modelo UML de clases de su aplicacion, identifique
    el patrón de diseño empleado (utilice estereotipos UML para indicar los
    roles de cada una de las clases en ese patrón).


> El patrón de Diseño utilizado es el Estructural -> Composite


  - Implemente completamente en Smalltalk.

  - Diseñe, implemente y ejecute test cases para verificar el funcionamiento de
    su aplicación.


Ejercicio 5: Fórmulas con objetos
---------------------------------

Veremos que es sencillo modelar formulas aplicando los conocimientos de
patrones. Considerando las siguientes reglas modele e implemente las fórmulas

  - Las constantes son términos.

  - Las variables son términos.

  - Una función cuyos parámetros sean términos es un término.

A partir de una fórmula es necesario saber la cantidad de términos atómicos
(constantes o variables).

Implemente completamente en Smalltalk incluyendo los test cases.
