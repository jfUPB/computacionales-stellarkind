## Solucion a la cuarta actividad  
### ¿Cuál es la función de cada tipo de instrucción?  
El lenguaje ensamblador de Hack define dos tipos de instrucciones: A y C. 
#### A-instructions (Instrucciones de Dirección):  
Cargan un valor en el registro A (A = valor), ese valor puede ser una dirección de memoria o un número constante. 
Las instrucciones de dirección se utilizan para preparar la memoria antes de ejecutar operaciones con M o realizar saltos (JMP).  
#### C-instructions (Instrucciones de Cómputo):  
Ejecutan operaciones aritméticas y lógicas, mueven datos entre registros y controlan el flujo del programa.
Están compuestas por tres partes:
##### comp: Operación a ejecutar en la ALU (como D+M, D-1, !A).
##### dest: Dónde se guarda el resultado (D, M, A o combinaciones como MD).
##### jump: Define un salto condicional (JGT, JEQ, JMP).  
### ¿Cómo se representa cada tipo de instrucción en binario?  
#### A-instructions (Instrucciones de Dirección): 
Una instrucción de dirección siempre comienza con un bit 0, seguido de un número de 15 bits.
Formato: 0 x x x x x x x x x x x x x x x  
#### C-instructions (Instrucciones de Cómputo):  
Una instrucción de cómputo siempre comienza con 111 en los 3 primeros bits.
Formato: 111 a c1 c2 c3 c4 c5 c6 d1 d2 d3 j1 j2 j3  
comp → Bits a y c1 - c6 definen la operación en la ALU.  
dest → Bits d1 - d3 indican dónde se guarda el resultado.  
jump → Bits j1 - j3 definen si hay un salto.  
### 3 Ejemplos de cada tipo de instrucción (Instrucción asm - Binario - Explicación):
#### A-instructions (Instrucciones de Dirección): 
```
@10 - 0000 0000 0000 1010 -	Guarda el número 10 en el registro A.
@R2 - 0000 0000 0000 0010 -	Apunta a la dirección R2 (registro virtual en RAM).
@SCREEN - 0100 0000 0000 0000 -	Apunta a la memoria de pantalla en la RAM (dirección 16384).
```
#### C-instructions (Instrucciones de Cómputo):  
```
D=A+1 -	1110 1101 1100 0000 - Suma 1 al valor de A y lo almacena en D.
M=D-1 - 1110 0111 0001 0000 - Resta 1 al valor de D y lo guarda en la dirección de memoria apuntada por A.
D;JGT -	1110 0001 1100 0001 - Salta a la dirección de A si D > 0.
```
