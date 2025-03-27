## Solución a la septima actividad
- **¿Qué ocurre al observar los valores hexadecimales 0a y 14?**
    - Al colocar la dirección de memoria del objeto p en la ventana de memoria, aparecen valores hexadecimales como 0a y 14. Al convertir estos valores desde hexadecimal a decimal, se obtiene que _0a → 10_ y _14 → 20_. Números que coinciden exactamente con los valores que se le asignaron al objeto ```(Punto p(10, 20))```.
- **¿Qué observas acerca del orden de almacenamiento de bytes?**
    - En la memoria, el byte menos significativo osea con el valor más pequeño, por ejemplo, _0a_ se guarda primero en la dirección más baja, seguido del byte más significativo. Lo que se le llama little-endian.  
### 1. ¿Cuál es la diferencia entre un constructor y un destructor en C++?
- Un **constructor** es una función especial que se llama automáticamente cuando se crea un objeto para inicializar sus atributos.
- Un **destructor** es otra función especial que se ejecuta automáticamente cuando un objeto se destruye (cuando sale del ámbito o cuando se libera explícitamente), y sirve para liberar recursos que el objeto haya utilizado.
### 2. ¿Cuál es la diferencia entre un objeto y una clase en C++?
- Una **clase** es como una plantilla que describe las características y comportamientos que tendrán los objetos creados a partir de ella.
- Un **objeto** es una instancia concreta de una clase, que ocupa un espacio real en la memoria y posee valores específicos para sus atributos definidos en la clase.
### 3. ¿Qué diferencia notas entre el objeto Punto en C++ y C#?
- En **C++**, al escribir un ```Punto p(10,20)```;, se crea un objeto directamente en el stack. El objeto se destruye automáticamente al salir del ámbito.
- En **C#**, cuando se escribe ```Punto p = new Punto(10,20)```;, se crea un objeto en la memoria dinámica. Además, C# maneja automáticamente la memoria y la destrucción del objeto.
### 4. ¿Qué es p en C++ y qué es p en C#?
- En **C++**, p es directamente un objeto concreto almacenado en el stack.
- En **C#**, p es una referencia que apunta a un objeto que está almacenado en la memoriaq dinámica (heap).
### 5. ¿En qué parte de memoria se almacena p en C++ y en C#?
- En **C++**, el objeto ```p``` está almacenado en el stack.
- En **C#**, el objeto al que apunta ```p``` está almacenado en el heap, mientras que la referencia ```p``` se guarda en el stack.
### 6. ¿Qué observaste con el depurador acerca de p? Según lo que observaste, ¿Qué es un objeto en C++?
- ```p``` en **C++** es un bloque de memoria con valores almacenados consecutivamente (como 10 y 20). Los valores son visibles claramente en formato hexadecimal, lo que confirma que un objeto es simplemente un conjunto estructurado de datos almacenado en la memoria.
_Por lo que en C++, un objeto es una región concreta de memoria que contiene los valores de los atributos definidos por su clase, además de métodos que operan sobre estos datos._

