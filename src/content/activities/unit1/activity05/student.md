## Solución a la quinta actividad  
### Tabla que documenta el ciclo Fetch-Decode-Execute:
```
| #  | PC | Instrucción | Decodificación  | Ejecuta                         | Cambios           |
|----|----|-------------|-----------------|---------------------------------|-------------------|
| 1  | 0  | @60         | A = 60          | Carga 60 en el registro A       | A = 60            |
| 2  | 1  | D=A         | D = A           | Copia el valor de A en D        | D = 60            |
| 3  | 2  | @9          | A = 9           | Carga 9 en el registro A        | A = 9             |
| 4  | 3  | D=D+A       | D = D + A       | Suma D + A (60 + 9)             | D = 69            |
| 5  | 4  | @6          | A = 6           | Carga 6 en el registro A        | A = 6             |
| 6  | 5  | M=D         | M[A] = D        | Guarda D en la dirección 6      | Mem[6] = 69       |
| 7  | 6  | @0          | A = 0           | Carga 0 en el registro A        | A = 0             |
| 8  | 7  | 0;JMP       | PC = A          | Salta a la dirección 0          | PC = 0            |

```
