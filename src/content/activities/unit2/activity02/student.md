## Solución a la segunda actividad  
En esta actividad, trabajé con el programa que suma los números del 1 al 100 y lo analicé paso a paso en el simulador Hack. Esta experiencia me permitió profundizar en el funcionamiento interno del ensamblador y 
comprender mejor cómo se gestionan las variables y se evalúan las condiciones a nivel de hardware.  
1. **Direcciones de memoria de las variable i, sum:**  
     - La variable i se implementa típicamente en la dirección 16, ya que  las variables definidas simbólicamente se asignan a direcciones de memoria a partir de la posición 16.  
     - La variable sum se asigna a la siguiente dirección disponible, es decir, la 17.  
2. **Diferencia entre la dirección de una variable y su contenido:**  
   La dirección de la variable es la ubicación física en la memoria donde se almacena la variable, mientras que el contenido de la variable es el valor o dato que se encuentra almacenado en esa dirección de memoria.  
3. **Implementación de la condición i <= 100**  
     La condición i <= 100 no se evalúa de forma directa en el ensamblador Hack. En cambio, se implementa de la siguiente manera:
   - Se carga el valor de i en el registro D con la instrucción D=M.  
   - Luego, se resta 100 al valor de i mediante D=D-A, lo que produce el resultado de i - 100.  
   - Se utiliza la instrucción D;JGT para realizar un salto condicional:  
     - Si el resultado (i - 100) es mayor que 0 (es decir, si i > 100), se salta a la etiqueta (END) para terminar el bucle.  
     - Si no se cumple esta condición, el programa continúa ejecutando el ciclo, implicando que i es menor o igual a 100 y se debe seguir sumando.
  
     Esta implementación en vez de preguntar "¿es i menor o igual a 100?", se pregunta "¿es i mayor que 100?" para decidir cuándo salir del ciclo, lo cual es una forma eficiente de controlar el flujo en el bajo nivel.
