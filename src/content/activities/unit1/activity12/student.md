## Solucion a la duodecima actividad  
### Línea horizontal se mueva a la derecha cuando se presionan las teclas de las flechas derecha e izquierda:
``` asm
@16384
M=-1
D=A
@10
M=D
@24576
D=M
@130
D=D-A
@17
D;JEQ
@2
D=D-A
@25
D;JEQ
@5
0;JMP
@10
A=M
M=0
A=A-1
M=-1
D=A
@3
0;JMP
@10
A=M
M=0
A=A+1
M=-1
D=A
@3
0;JMP
```
### Video
<video width="640" height="360" controls>
  <source src="https://github.com/jfUPB/computacionales-stellarkind/raw/refs/heads/main/src/assets/sc-u1-a12-v1.mp4" type="video/mp4">
  Tu navegador no soporta el elemento de video.
</video>

