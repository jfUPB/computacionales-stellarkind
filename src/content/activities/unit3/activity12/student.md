## Solución a la duodécima actividad
### Sobre el ciclo de vida de objetos (Stack vs Heap)
Cuando creamos un objeto en el **stack**, _su ciclo de vida está claramente definido por el bloque en el que se declara_. 
Por ejemplo, al crear ```pBloque``` dentro del bloque ```{}```, se llama automáticamente al constructor al entrar al bloque y automáticamente al destructor al salir del bloque. 
El objeto es eliminado automáticamente de la memoria cuando termina ese bloque.

En cambio, al crear un objeto en el **heap** (como ```pDinamico``` usando ```new```), este objeto persiste en la memoria hasta que yo misma decida eliminarlo explícitamente con ```delete```. _Su ciclo de vida no depende del ámbito del bloque sino de mi manejo_.

### ¿El segundo código compila? ¿Por qué?
Este código **no compila** debido a que la variable ```pBloque2``` fue declarada dentro de un bloque, lo cual limita su visibilidad únicamente al interior de ese bloque. Al intentar usarla después de ese bloque:
```pBloque2->imprimir();``` el compilador da un error porque la variable ```pBloque2``` ya no existe fuera del bloque donde fue declarada.

### ¿Qué ocurre al declarar ```pBloque2``` fuera del bloque pero inicializarlo dentro? ¿Por qué?
Al modificar el programa declarando ```pBloque2``` por fuera del bloque e inicializándolo dentro, **el  programa compila correctamente y funciona sin problemas**. Esto sucede _porque aunque inicializo el objeto dinámicamente dentro del bloque, la variable que guarda la dirección (pBloque2) es visible desde fuera_, permitiéndome usarla después. El objeto creado dinámicamente no desaparece al terminar el bloque, solo desaparece cuando lo libero explícitamente con ```delete```.

### ¿Por qué el objeto ```pBloque``` se destruye al salir del bloque y ```pBloque2``` no? ¿Es ```pBloque2``` un objeto o una referencia a un objeto?
El objeto ```pBloque``` se destruye automáticamente porque fue creado en el stack. Su ciclo de vida está atado directamente al ámbito del bloque en que se declara. En cambio, ```pBloque2``` es un puntero que contiene la dirección del objeto real. La variable puntero está en el stack, pero el objeto al que apunta (creado con ```new```) está en el heap y no se destruye automáticamente al salir del bloque. Por eso sigue existiendo hasta que yo mismo decida destruirlo con ```delete```.

### ¿En qué parte de la memoria se almacenan ```pBloque2``` y el objeto al que apunta? 
- La variable ```pBloque2``` (el puntero) está almacenada en el stack (es una variable local).  
- El objeto al que apunta ```pBloque2```, creado dinámicamente con ```new```, está almacenado en el heap.
