# Solución a la segunda actividad:
## Predicción: antes de ejecutar el programa, predice la salida de cada función y explica el resultado.
R/ Se van a modificar las variables b y c dado que para los dos estás modificando directamente el valor almacenado, miientras a lo que hace es usar la variable dentro del contexto de la función, más no modificar el valor original. 
- **Valores iniciales (en main):**  
    - a = 10   
    - b = 15  
    - c = 15  
- **Llamando a modificarPorValor(a)**   
    - Dentro de la función:  
        - “Dentro de modificarPorValor, valor inicial: 10”   
        - El valor se modifica localmente a 15 (n += 5), por lo que imprime “Dentro de modificarPorValor, valor modificado: 15”.   
    - Al regresar a main, a sigue valiendo 10, ya que solo se modificó la copia local. Por lo tanto:  
        - “Después de modificarPorValor, valor de a: 10”  
- **Llamando a modificarPorReferencia(b)**  
    - Dentro de la función:  
        - “Dentro de modificarPorReferencia, valor inicial: 10”  
        - El valor se incrementa en 5, pasando a 15 (n += 5), así que imprime “Dentro de modificarPorReferencia, valor modificado: 15”.  
    - Al regresar a main, b cambia a 15, porque fue pasado por referencia (se modificó el original). Por lo tanto:  
        - “Después de modificarPorReferencia, valor de b: 15”  
- **Llamando a modificarPorPuntero(&c)**   
    - Dentro de la función:   
        - “Dentro de modificarPorPuntero, valor inicial: 10”  
        - El valor apuntado por n se incrementa en 5, pasando a 15 (*n += 5), así que imprime “Dentro de modificarPorPuntero, valor modificado: 15”.  
    - Al regresar a main, c cambia a 15, porque la función recibió la dirección de c y lo modificó directamente en memoria. Por lo tanto:  
        - “Después de modificarPorPuntero, valor de c: 15”  
## ¿Qué diferencias observas en el comportamiento de a, b y c tras cada llamada?  
R/ a (pasado por valor) permanece con el valor original (10) después de la llamada a la función, b (pasado por referencia) se modifica a 15 después de la llamada, pues la función altera directamente el valor origina y YA c (pasado por puntero) tammbién se modifica a 15 después de la llamada, puesto que la función recibe la dirección de c y cambia el valor que allí se almacena.  
## ¿Por qué ocurre esta diferencia?
R/ Básicamente por cómo se gestiona la memoria y si se está trabajando con una copia o con la dirección/alias de la variable original. Por eso b y c cambian después de las llamadas, mientras que a permanece con su valor inicial.  
## Código de las tres funciones de swap y el código de main() con las llamadas a las funciones:
``` cpp 
#include <iostream>
using namespace std;


void swapPorValor(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
    // Se muestran los valores intercabiados dentro de la función,
    // pero estos cambios se aplican solo a las copias locales.
    cout << "Dentro de swapPorValor: a = " << a << ", b = " << b << endl;
}

void swapPorReferencia(int& a, int& b) {
    int temp = a;
    a = b;
    b = temp;
    // Los cambios afectan directamente a las variables originales.
    cout << "Dentro de swapPorReferencia: a = " <<a<< ", b = " <<b<< endl;
}

void swapPorPuntero(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
    cout << "Dentro de swapPorPuntero: a = " <<*a<< ", b = "<<*b<< endl;
}

int main() {
    int x = 5, y = 10;
    cout << "Valores iniciales: x = " <<x<< ", y = " <<y<< endl;

    // Llamada a swapPorValor (no se espera que modifiquelas variables originales)
    swapPorValor(x, y);
    cout << "Despues de swapPorValor: x = " <<x<< ", y = " <<y<< endl;

    // Re-inicializamos x e y
    x = 5;
    y = 10;

    swapPorReferencia(x, y);
    cout << "Despues de swapPorReferencia: x = " <<x<< ", y = " <<y<< endl;

    // Re-inicializamos x e y
    x = 5;
    y = 10;

    // Llamada a swapPorPuntero (se modifican las variables originales)
    swapPorPuntero(&x, &y);
    cout << "Despues de swapPorPuntero: x = " <<x<< ", y = " <<y<< endl;
    return 0;
}

```
## Preguntas para Reflexionar:
### ¿Por qué la versión de swapPorValor no logra intercambiar los valores de x e y en el main()?
a función ```swapPorValor``` recibe copias de los valores de ```x``` e ```y```. Esto significa que al intercambiar los valores dentro de la función, únicamente se modifican estas copias locales. Las variables originales en ```main()``` permanecen sin cambios, ya que no se afecta su ubicación en memoria.
### ¿Cómo y por qué logran las otras dos funciones (por referencia y por puntero) modificar las variables originales?
- **Paso por referencia (```swapPorReferencia```):** La función recibe referencias a las variables originales. Una referencia es básicamente un alias que apunta a la misma ubicación de memoria que la variable original, por lo que cualquier cambio se refleja directamente en ella.
- **Paso por puntero (```swapPorPuntero```):** La función recibe las direcciones de memoria de las variables originales. Al usar el operador de indirección (*), se accede y modifica el valor almacenado en esa dirección, cambiando así la variable original.
### ¿Cuáles son las ventajas y consideraciones de usar referencias versus punteros en este caso?
- Referencias:
    - Ventajas:
        - Sintaxis más simple y natural (se usan como variables normales).
        - Menor riesgo de errores, ya que no pueden ser nullptr.
    - Consideraciones: Una vez inicializada, una referencia no puede cambiar para referirse a otra variable.
- Punteros:
    - Ventajas:
        - Mayor flexibilidad, ya que pueden apuntar a diferentes direcciones o incluso a arreglos y memoria dinámica.
    -  Consideraciones: Mayor complejidad en la sintaxis (necesidad de usar operadores * y &). También existe el riesgo de utilizar punteros nulos o no inicializados, lo que puede causar errores en tiempo de ejecución.
Entonces, para operaciones sencillas como el swap, las referencias suelen ser preferidas por su simplicidad y seguridad. Los punteros resultan útiles en contextos donde se requiere una manipulación más dinámica de la memoria.



