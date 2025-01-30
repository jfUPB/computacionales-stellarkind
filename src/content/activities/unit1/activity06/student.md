## Solucion a la sexta actividad  
### ¿Qué es el direccionamiento directo?  
El direccionamiento directo es un modo de acceso a memoria en el cual una instrucción especifica 
directamente la dirección de la memoria donde se encuentra un valor o donde se debe escribir un dato.
#### ¿Cómo se usa en el lenguaje ensamblador Hack?  
En Hack, las direcciones de memoria se representan mediante el registro A, se usa para acceder a una ubicación específica en la memoria de datos (RAM).
### ¿Qué significa M=D en lenguaje ensamblador Hack?  
M=D Guarda el valor de D en la memoria
#### ¿Y D=M?  
D=M Carga en D el valor almacenado en la memoria
### Concepto de “puntero” en el contexto de la memoria:  
Son direcciones almacenadas en memoria que permiten referenciar indirectamente otras ubicaciones.
#### Ahora, un ejemplo:  
```
@100    // Carga la dirección 100 en A
D=A     // Guarda 100 en D
@10     // Carga la dirección 10 en A
M=D     // Guarda el valor 100 en la dirección 10 (puntero en Mem[10])

@10     // Carga la dirección 10 en A (donde está almacenado el puntero)
D=M     // Carga en D el valor de Mem[10] (que es 100)
@D      // Carga la dirección almacenada en D (100) en A
M=42    // Guarda el valor 42 en la dirección de memoria 100
```
En el ejemplo, después de la ejecución, la dirección 100 en memoria contendrá 42.
