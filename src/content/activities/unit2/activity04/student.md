## Solución a la cuarta actividad
### Conversión de un programa de C++ a ensamblador
``` asm
@10
D=A
@a
M=D

@a
D=A
@p
M=D

@20
D=A
@p
A=M
M=D

@END
0;JMP
(END)
```
