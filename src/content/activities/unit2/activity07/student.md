## Solución a la septima actividad
### Conversión de un programa de C++ a ensamblador, arreglos
``` asm
@1
D=A
@16
M=D

@2
D=A
@17
M=D

@3
D=A
@18
M=D

@4
D=A
@19
M=D

@5
D=A
@20
M=D

@6
D=A
@21
M=D

@7
D=A
@22
M=D

@8
D=A
@23
M=D

@9
D=A
@24
M=D

@10
D=A
@25
M=D

@0
D=A
@26
M=D

@16
D=A
@27
M=D

@10
D=A
@28
M=D

(LOOP)
@28
D=M
@END
D;JEQ

@27
A=M
D=M

@26
M=D+M

@27
M=M+1

@28
M=M-1

@LOOP
0;JMP

(END)
@END
0;JMP
```
