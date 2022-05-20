# Notas

## Links

https://algoritmos-iii.github.io/

https://github.com/TomasSzeSirk/AyP3/issues

https://sites.google.com/view/cuis-university

## Recordatorios

• Categorizar mensajes.

• implementar mensajes abstractos con "self subclassResponsibility".

• Hacer explícitos los conceptos dentro del código para eliminar código repetido.

## Sacar Ifs

   1. Crear una jerarquía de clases con una clase por cada condición del if (si es que no existen).
   2. Mover el cuerpo del if de cada condición a cada abstracción del paso 1) utilizando un mensaje polimórfico.
   3. Nombrar el mensaje polimórfico.
   4. Nombrar las abstracciones generadas en el paso 1.
   5. Reemplazar el if por el envío del mensaje polimórfico.
   6. Buscar el objeto polimórfico (si es necesario)

## Switch dinámico

Es un mensaje de clase que se usa solo cuando no se sabe qué clase instanciar, luce de la siguiente manera:

> ^(self subclasses detect: [:subclass| subclass detectIfSubclassFitsRequirements: anObject ]) new.

También se puede asignar la subclase obtenida a una variable temporal, instanciarla y luego devolverla.

El detector dentro del closure es un mensaje polimorfico. Cada subclase devolverá true o false según cómo responde al objeto enviado.

*por ejemplo en el ejercicio de Stack, #detectIfItIsTheCorrectState: de OOLleno devolverá true si el stack está lleno, por lo que si esto se cumple el detect devolverá la subclase OOLLeno y posteriormente se podrá crear la instancia.

## Sobre el Parcial 2C2021

### Para el modelo:

• Si un NPC puede tener estados/roles, el estado es una clase a parte (con subclases que representen cada uno).

• Si queremos representar algo que no hace nada en nuestro modelo (porque lo queremos usar en nuestros tests, por ejemplo) podemos usar simbolos.

### Para los tests:

• Crear mensajes y asserts que faciliten la lectura de colaboraciones que tengan un significado.

  > 5 timesRepeat: [ mensaje := NPCJulian interactuarCon: jugadorPablo ] ^mensaje
 
  Se ve mucho peor que poner:
  
  > hacerInteractuar: 5 vecesA: NPCJulian con: jugadorPablo

  y utilizar la primer colaboración como método de este ultimo mensaje.

  Luego se podría crear un mensaje de assert que utilice este mensaje para verificar si la interacción es la correcta.
  
 • Para verificar que un Error sea el esperado se hace lo siguiente:
 
 > self 
		should: [ one / zero ]
		raise: Error
		withExceptionDo: [ :anError | self assert: Numero canNotDivideByZeroErrorDescription equals: anError messageText ]
