## Solución a la tercer actividad
1. **¿Por qué son equivalentes?**  
  Ambos realizan la misma operación:
    - **_Inicialización:_** Se asigna el valor 1 a la variable i y 0 a sum.
    - **_Condición:_** Se verifica que i sea menor o igual a 100.
    - **_Cuerpo del ciclo:_** Se suma el valor de i a sum.
    - **_Incremento:_** Se incrementa i en 1 al final de cada iteración.
2. **Traducción a Ensamblador**
  
    ``` java
    @sum
    M=0
  
    (LOOP_FOR)
    @i
    D=M
    @100
    D=D-A
    @END_FOR
    D;JGT
    
    @i
    D=M
    @sum
    M=D+M
    
    @i
    M=M+1
    
    @LOOP_FOR
    0;JMP
    
    (END_FOR)
    @END_FOR
    0;JMP
    ```
    Dado que el lenguaje ensamblador de la máquina Hack no tiene estructuras de control de alto nivel, la traducción del ciclo for se realiza de manera muy
   similar a la del ciclo while, pues aunque el for y el while sean conceptualmente diferentes en lenguajes de alto nivel, en el nivel de ensamblador
   se descomponen en las mismas operaciones básicas, lo que resalta la importancia de conocer el funcionamiento interno del sistema para optimizar y depurar programas de manera eficiente.
3. **Comparación entre las versiones en ensamblador (while vs. for)**
  - _**Estructura y Flujo de Control:**_ Ambas versiones (la obtenida del ciclo while y la del ciclo for) comparten la misma estructura: inicialización de variables, comprobación de la condición, ejecución del cuerpo del ciclo, incremento y salto incondicional para repetir el ciclo.
  - _**Equivalencia Semántica:**_ La diferencia en C++ entre un while y un for es meramente sintáctica. En ensamblador, donde no existen estructuras de control de alto nivel, la implementación de ambos ciclos resulta prácticamente idéntica.
  - _**Conclusión:**_ La conversión del ciclo for a ensamblador demuestra que, a nivel de hardware, las estructuras de control de flujo se implementan de manera similar. El ciclo for es simplemente una forma más compacta de escribir lo mismo que un ciclo while.
