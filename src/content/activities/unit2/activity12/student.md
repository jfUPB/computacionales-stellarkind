## Solución a la duodécima actividad
### Programa en C++: Cálculo de la Serie de Fibonacci:
``` cpp
#include <iostream>
using namespace std;

void printFibonacci(int n) {
    int first = 0, second = 1, next = 0;
    cout << "Fibonacci Series: ";
    for (int i = 0; i < n; i++) {
        if (i <= 1) {
            next = i;
        } else {
            next = first + second;
            first = second;
            second = next;
        }
        cout << next << " ";
    }
    cout << endl;
}

int main() {
    int n = 10;  // Número de términos de la serie de Fibonacci dará el programa
    printFibonacci(n);
    return 0;
}
```
### Equivalente del programa en ensamblador:
``` asm
@0
D=A
@16
M=D
@1
D=A
@17
M=D
@9
D=A
@19
M=D
@FIB_LOOP
0;JMP
(FIB_LOOP)
    @19
    D=M
    @END_LOOP
    D;JEQ
    @16
    D=M
    @17
    A=M
    D=D+A
    @18
    M=D
    @17
    D=M
    @16
    M=D
    @18
    D=M
    @17
    M=D
    @19
    M=M-1
    @FIB_LOOP
    0;JMP
(END_LOOP)
    @END_LOOP
    0;JMP
```
