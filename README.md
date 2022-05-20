# Notas

## Recordatorios

• Categorizar mensajes.

• implementar mensajes abstractos con "self subclassResponsibility".

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
