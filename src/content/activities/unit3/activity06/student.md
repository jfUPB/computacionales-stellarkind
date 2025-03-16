## Solución a la sexta actividad:
### Experimento 5: variables locales estática vs no estática:
- **¿Qué ocurre? ¿Por qué?**
  Cada vez que llamamos a ```funcionSinStatic```, la variable local ```var_no_estatica``` imprime siempre en la consola el valor 100. sto pasa porque esta variable local normal se crea nuevamente en cada llamada, y se destruye inmediatamente al salir de la función, perdiendo cualquier cambio que se le haya hecho. En cambio, la función ```funcionConStatic``` muestra un comportamiento diferente: la variable ```var_estatica``` empieza en 100 pero aumenta en 1 con cada iteración. Esto ocurreporque es una variable estatica local, que se inicializa solo en la primera ejecución y mantiene su valor entre todas las llamadas posteriores a la función.
- **Ves alguna diferencia entre las variables locales estáticas y no estáticas? Qué pasa con las variables cada que entras y sales de la función?**
  Sí, hay una diferencia y es quelas variables locales no estáticas se crean cada vez que entras a la función y se destruyen al salir, perdiendo su valor; por eso, siempre empiezan con el mismo valor inicial. En contraste, las variables locales estáticas se crean y se inicializan únicamente la primera vez que entras a la función, persistiendo en memoria durante todo el tiempo que dure la ejecución del programa, manteniendo sus valores incluso después de que la función finaliza. Esto permite que las variables estáticas puedan recordar su estado anterior, mientras que las no estáticas no.
  
### Experimento 6: modificar el segmento de heap: 
- **¿Qué ocurre? ¿Por qué?**
  Inicialmente el programa funciona bien, reserva memoria dinámica en el heap con new, asigna valores y los muestra correctamente. Pero, después de liberar la memoria con ```delete[] arrayHeap```, intenta acceder nuevamente a ```arrayHeap[0]``` lo que provoca un comportamiento indefinido y un error ```Se produjo una excepción:infracción de acceso de lectura. arrayHeap fue 0x8123.```
- **Comenta la línea de genera el error y analiza las siguientes preguntas:** _```cout << arrayHeap[0] << endl;``` es la linea con el error_  
  - **¿Qué diferencias notas entre el comportamiento y la gestión del Heap en comparación con el Stack?**
    - Comparado con el stack, el heap permite reservar memoria de forma manual con ```new``` (liberándola con ```delete```), mientras que el stack se gestiona automáticamente al entrar y salir de lasfunciones.
    - Las variables en stack se crean y destruyen automáticamente, por el contrario en heap se tiene la responsabilidad directa de asignar y liberar memoria, y las variables permanecen activas hasta que explícitamente se liberan. Aparte la memoria heap es másamplia, pero su mala gestión da muchos errores.
  - **¿Qué consecuencias tendría no liberar la memoria reservada con new?**
    Si no se libera la memoria, la memoria reservada se queda ocupada hasta que programa termina, consumiendo recursos innecesariamente. En programas pesados esto puede agotar los recursos disponibles del sistema.
