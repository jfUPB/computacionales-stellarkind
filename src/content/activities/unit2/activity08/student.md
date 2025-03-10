## Solución a la octava actividad
El ejercicio "¿Quién cometió el crimen?" implica que el "crimen" es el cambio de comportamiento del programa debido a la modificación de valores en ciertas direcciones de memoria. Este cambio es dirigido por quien 
maneja el programa, usualmente el programador. Por lo tanto, en un sentido metafórico, el programador "cometió el crimen" al diseñar un programa que cambia radicalmente de comportamiento bajo ciertas condiciones controladas.  
La primera instrucción carga la constante 16384 y, tras un par de pasos, se almacena ese valor en la dirección 16.  
Más adelante, el programa carga la dirección 24576 y obtiene el contenido de esa posición de memoria.  
Luego, en se realiza un salto condicional:  
- Si el valor leído (desde 24576) es distinto de cero, el programa salta a la instrucción ubicada en la dirección 19.  
- En cambio, si es cero, el programa continúa su ejecución de forma “normal”.

Dependiendo de la condición que se haya leído inicialmente, el programa puede terminar en un bucle infinito o reiniciar con nuevas instrucciones, en este caso, el ejemplo tal y como está queda en un bucle infinito.
