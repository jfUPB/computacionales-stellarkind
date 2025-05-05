## Solución a la quinta actividad
### Conversión de un programa de C++ a ensamblador, lectura usando punteros
```
@10
D=A
@a
M=D

@5
D=A
@b
M=D

@a
D=A
@p
M=D

@p
A=M
D=M
@b
M=D

@END
0;JMP
(END)
```
