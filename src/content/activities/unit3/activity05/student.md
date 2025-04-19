## Solución a la quinta actividad
### Experimento 3: modificar el segmento de datos (variables globales):
- **¿Qué ocurre?**   
  R/ El código funciona correctamente, sin errores, en la consola primero muestra los valores en que se inicializaron las variables luego el programa modifica los mismos y muestra en consola los valores modificados.
- **¿Por qué?**  
  R/ Porque ambas son variables globales que se almacenan en una sección especial de la memoria que no tiene restricciones de acceso, por lo que sepueden leer y modificar libremente. 
### Experimento 4: modificar la variable local estática de una función por fuera de ella:    
- **¿Qué ocurre?**  
  R/ Al intentar depurar el programa, sale error de compilación. No compila. El error se da en la linea ```var_estatica = 42;```, indicando que la variable no fue declarada en ese contexto. 
- **¿Por qué?**  
  R/ Se da porque la variable ```var_estatica``` la declaramos como local estática en la función ```funcionConStatic()``` entonces su contexto se limita solo a esa función y consecuentemente no es visible desde otras funciones, en este caso ```main()```.
- **¿Qué pasa con las variables cada que entras y sales de la función?**  
  R/ Cuando entras en una función, las variables locales no estáticas se crean automáticamente en el stack y viven únicamente durante la ejecución de esa función, por lo que al salir de ella estas variables se destruyen y se pierde su valor. En cambio, las variables locales estáticas tienen una característica especial: se crean solo una vez la primera vez que llamas a la función y permanecen en memoria hasta que el programa termina. Esto significa que su valor persiste entre múltiples llamadas, aunque solamente pueden ser accedidas desde el interior de esa función específica.
- **En relación a la pregunta anterior ¿Qué pasa con las variables locales estáticas?**  
  R/ Las variables locales estáticas se inicializan solo una vez, cuando llamas por primera vez a la función, asignándoseles una ubicación fija en memoria (segmento de datos). Luego permanecen allí, manteniendo su valor entre llamadas sucesivas a la función, sin reiniciarse ni destruirse. Sin embargo, aunque su tiempo de vida es el mismo que el del programa completo, solo son visibles dentro del ámbito de la función donde fueron declaradas, por lo que no puedes acceder a ellas directamente desde otras partes del programa.
