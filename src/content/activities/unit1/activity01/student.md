### Solucion a la primer actividad  
#### Suma los número 60 y 9 y guarda el resultado en la posición de memoria 6:
```
@60
D=A       
@9
D=D+A     
@6
M=D       
@6
0;JMP   
```
#### Has que el programa vuelva a comenzar desde la posición 0 una vez almacene el resultado de la operación:
```
@60
D=A       
@9
D=D+A     
@6
M=D       
@0
0;JMP   
```
