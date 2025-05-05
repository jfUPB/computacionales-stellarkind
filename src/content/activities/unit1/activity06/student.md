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
@100
D=A     
@10
M=D

@42
D=A
@10
A=M
M=D

@10     
A=M
D=M
@11     
M=D
```
En el ejemplo, después de la ejecución, la dirección 100 en memoria contendrá 42.
