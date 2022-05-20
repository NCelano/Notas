# Notas

## Sobre el Parcial 2C2021

### Para el modelo:

• Si un NPC puede tener estados/roles, el estado es una clase a parte (con subclases que representen cada uno).

### Para los tests:

• Crear mensajes que faciliten la lectura de colaboraciones que tengan un significado

  > 5 timesRepeat: [ mensaje := NPCJulian interactuarCon: jugadorPablo ]
 
  Se ve mucho peor que poner
  
  > hacerInteractuar: 5 vecesA: NPCJulian con: jugadorPablo
