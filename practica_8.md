Orientación a Objetos 2 -Práctica 8
====================================

Ejercicio 1: Lea la bibliografía y responda
-------------------------------------


1. Lea la siguiente bibliografía (encontrará enlaces a las versiones online en el sitio de la materia) y los slides de la clase 1 de reuso y frameworks.

  - Fayad, Mohamed, and Douglas C. Schmidt. Object-oriented application frameworks. Communications of the ACM 40.10 (1997): 32 a 38.
  - Johnson, Ralph E., and Brian Foote. Designing reusable classes. Journal of object-oriented programming 1.2 (1988): 22 a 35
  - Sommerville, Ian. Software Engineering. Addison-Wesley; 9 edition (March 13, 2010). Capítulo 16.
  
  
2. Responda a las siguientes preguntas:


#a) Reuso

  1) Cuáles son los diferentes tipos de reúso citados en la bibliografía de referencia y revisados en las clases teóricas?

   > Se reusan aplicaciones completas (se adaptan o reusan por completo), componentes (se invocan), diseños o estrategias de diseño (se impletan o imitan), conceptos o ideas funcionales.
  
  2) Cuando aplicamos patrones de diseño: qué estamos reusando? De qué manera los patrones de diseño atacan las dificultades del reúso? Encuentre al menos dos ejemplos en los trabajos prácticos realizados
hasta ahora.

   > Se reusan aplicaciones completas (se adaptan o reusan por completo), componentes (se invocan), diseños o estrategias de diseño (se impletan o imitan), conceptos o ideas funcionales.

  3) Cuando utilizamos librerías de clases: qué estamos reusando? Describa dos ejemplos de los trabajos
prácticos anteriores en los que utilizó librerías de clases indicando qué dificultades de reúso pudo
resolver.



#b) Frameworks


  1) Cuando utilizamos frameworks orientados a objetos: qué estamos reusando? De qué manera atacan
los frameworks las dificultades de reúso?

   > Reusamos clases concretas o abstractas. Los frameworks tiene diseñados e implementados objetos para hacer clases reusables, de tal manera que sirve para cualquier aplicación futura que utilice el frameworks.

  2) De acuerdo con el tipo de problema que atacan, cómo se clasifican los frameworks? De ejemplo de cada categoría.

	> - Infraestructura: 
	. Ataca problemas generales de desarrollo de software, generalmente no captados por el usuario de la aplicacion (resuelven problemas de los programadores no de los usuarios).
	. Se enfica en interfaces de usuario (desktop, web , moviles), seguridad, contenedores de app, etc.
	. Proveen infraestructura portable y eficiente sobre la cual construir una gran variedad de app.
	
	> - Integración: Se utilizan para integrar componentes de aplicación distribuidos. Se diseñan para aumentar la capacidad de los desarrolladores de reusar, modularizar, y extender su infraestructura de software.
	   
	> - Enterprice...

  3) A que nos referimos con los términos hot spot y frozen spot?
    
   	> Hostpost: Son la parte del framework donde acurre la adaptación, es decir, es donde nosotros escribimos nuestro código para transformar un framework en una aplicación.
   
	> whitebox (caja blanca): Si ocurre por clasificacion.
	
	> blackbox (caja negra): si ocuure por composicion.
	
	> Frozenpost: Son partes del framework que no cambian, se mantienen igual para todos las aplicaciones que lo usan
  
  4) A qué nos referimos con instanciar un framework ? Qué sería instanciar un hostpot?
  
   > Instanciar un framework es completar/configurar sus hostpost para obtener una aplicacion en particular. A estas modificaciones se las llama incrementos.
  
  5) En qué se diferencia un framework blackbox de uno whitebox? Un framework, cae exclusivamente en
una de esas categorías? De ejemplos

   	> Los whitebox proveen extensibilidad dependiendo de las caracteristicas OO como la herencia y el binding dinámico. (herencia y redefiniar metodos gancho, hock). En este caso los programadores deben conocer la estructura interna del framework

	> Los blackbox soportan la extensibilidad vía la deficinicion de interfaces para componentes que pueden ser añadidos al framework por composicion de objetos.(definiendo componentes que cumplen con una interface determinada y luego integrandolos al framework.). Los blackbox usan delegacion y composicion en lugar de herencia, se requiere estudiar librerias de componentes y sus configuraciones.

	> Los black box son mas faciles de usar pero mas dificiles de desarrollar, y por lo general menos flexibles.
