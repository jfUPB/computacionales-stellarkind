## Solución a la novena actividad
### Explica qué ocurre al copiar un objeto en C++ y en C#. ¿Qué diferencias encuentras?
Al copiar objetos en C++, se crea una copia independiente con una nueva dirección en memoria; por eso, modificar la copia no afecta al objeto original. En cambio, al usar un puntero en C++, se trabaja directamente sobre la ubicación en memoria del objeto original, por lo que modificarlo desde el puntero sí afecta al original. Por otro lado, en C#, copiar un objeto significa copiar la referencia al mismo objeto, así que cualquier modificación afecta al objeto original, ya que ambas variables apuntan exactamente al mismo lugar en memoria.

### ¿Qué es copia en C++ y en C#? ¿Es una copia independiente de original?
- En C++, la variable ```copia``` es una copia real y totalmente independiente del objeto original. Al copiar un objeto así, se crea una nueva instancia en memoria con los mismos valores iniciales, pero con diferente dirección de memoria. Por lo tanto, modificar esta copia no afecta al original.
- En C#, la variable ```copia``` es en realidad una referencia que apunta exactamente al mismo objeto que el original. Por esta razón, no es una copia independiente. Al modificar esta referencia, se afecta directamente al mismo objeto que la variable original.
