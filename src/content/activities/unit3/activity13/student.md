## Solución a la decimotercer actividasd
### Código de mi ejemplo:
``` cpp
#include <iostream>
#include <string>
using namespace std;

class Cuenta {
public:
    string nombre;
    int saldo;
    static int totalCuentas;

    // Constructor
    Cuenta(string _nombre, int _saldo) : nombre(_nombre), saldo(_saldo) {
        totalCuentas++;
        cout << "Constructor: Cuenta de " << nombre << " creada con saldo " << saldo << endl;
    }

    // Destructor
    ~Cuenta() {
        totalCuentas--;
        cout << "Destructor: Cuenta de " << nombre << " destruida." << endl;
    }

    // Método que modifica el saldo (por valor)
    void modificarSaldoValor(int nuevoSaldo) {
        nuevoSaldo += 100;
        cout << "(por valor) nuevoSaldo modificado dentro de la funcion: " << nuevoSaldo << endl;
    }

    // Método que modifica el saldo (por referencia)
    void modificarSaldoReferencia(int &nuevoSaldo) {
        nuevoSaldo += 100;
        cout << "(por referencia) nuevoSaldo modificado dentro de la funcion: " << nuevoSaldo << endl;
    }

    void mostrar() {
        cout << "Cuenta: " << nombre << ", saldo: " << saldo << endl;
    }
};

// Inicialización del miembro estático
int Cuenta::totalCuentas = 0;

int main() {
    cout << "Inicio del programa." << endl;

    // Objeto creado en el stack
    Cuenta cuentaStack("Stack", 500);
    cuentaStack.mostrar();

    int saldoExtra = 200;
    cuentaStack.modificarSaldoValor(saldoExtra);
    cout << "saldoExtra despues de modificarSaldoValor: " << saldoExtra << endl;

    cuentaStack.modificarSaldoReferencia(saldoExtra);
    cout << "saldoExtra despues de modificarSaldoReferencia: " << saldoExtra << endl;

    // Objeto creado en el heap
    Cuenta* cuentaHeap = new Cuenta("Heap", 1000);
    cuentaHeap->mostrar();

    cout << "Total cuentas creadas: " << Cuenta::totalCuentas << endl;

    // Puntero y referencia
    Cuenta& refCuentaStack = cuentaStack;
    refCuentaStack.saldo += 50;
    cout << "saldo cuentaStack despues de modificar via referencia: ";
    cuentaStack.mostrar();

    Cuenta* punteroCuentaHeap = cuentaHeap;
    punteroCuentaHeap->saldo += 100;
    cout << "saldo cuentaHeap despues de modificar via puntero: ";
    cuentaHeap->mostrar();

    delete cuentaHeap;

    cout << "Total cuentas al final: " << Cuenta::totalCuentas << endl;
    cout << "Fin del programa." << endl;

    return 0;
}

```
### Sobre la aplicación de los Conceptos en el Código de mi ejemplo:

**Clases y Objetos:**   
-  **Clase:** Se define la plantilla ```class Cuenta { ... };```. Una clase es un tipo de dato definido por el usuario que sirve como plano o modelo para crear objetos. En este caso, ```Cuenta``` define la estructura de una cuenta bancaria (nombre, saldo) y el comportamiento asociado (constructor, destructor, métodos para modificar/mostrar saldo).  
- **Objetos:** Se crean instancias de la clase ```Cuenta```.  
    - ```Cuenta cuentaStack("Stack", 500);``` crea un objeto llamado ```cuentaStack```.  
    - ```Cuenta* cuentaHeap = new Cuenta("Heap", 1000);``` crea un objeto llamado ```cuentaHeap``` (cuentaHeap es un puntero que apunta al objeto real). Los objetos son las entidades concretas que existen en la memoria durante la ejecución del programa, basándose en la definición de la clase.

**Paso de Parámetros por Valor y por Referencia:**
- **Por Valor:** El método ```void modificarSaldoValor(int nuevoSaldo)``` recibe el parámetro ```nuevoSaldo``` por valor. Cualquier modificación que se haga a ```nuevoSaldo``` dentro de ```modificarSaldoValor``` solo afectará a esa copia local, no a la variable ```saldoExtra``` en main. La salida del programa demuestra esto claramente.  
- **Por Referencia:** El método ```void modificarSaldoReferencia(int &nuevoSaldo)``` recibe el parámetro nuevoSaldo por referencia (indicado por el &). Esto significa que ```nuevoSaldo``` dentro de la función es un alias o un nombre alternativo para la variable original que se pasa desde ```main``` (```saldoExtra```). Cualquier modificación que se haga a ```nuevoSaldo``` dentro de ```modificarSaldoReferencia``` sí afecta a la variable original (```saldoExtra```) en main. La salida del programa también muestra este efecto.

**Constructores y Destructores:**
- **Constructor:** ```Cuenta(string _nombre, int _saldo) : nombre(_nombre), saldo(_saldo) { ... }```. Esta función especial se llama automáticamente cuando se crea un nuevo objeto de la clase ```Cuenta```. Se encarga de inicializar los miembros de datos (```nombre``` y ```saldo```) ye incrementa el contador estático ```totalCuentas``` y muestra un mensaje informativo.
- **Destructor:** ```~Cuenta() { ... }```. Esta función especial se llama automáticamente cuando un objeto de la clase ```Cuenta``` es destruido. Se encarga de realizar tareas de limpieza antes de que el objeto deje de existir. En este código, decrementa el contador estático ```totalCuentas``` y muestra un mensaje al destruir cada cuenta. Se llama automáticamente para ```cuentaStack``` al final de main y explícitamente para ```cuentaHeap``` cuando se llama a ```delete```.

**Métodos y Atributos:**
- **Atributos:** ```string nombre;```, ```int saldo;```, ```static int totalCuentas;```. Son las variables que almacenan el estado de un objeto o de la clase (en el caso del estático). Representan las propiedades de una cuenta.
- **Métodos:** ```modificarSaldoValor```, ```modificarSaldoReferencia```, ```mostrar```. Son las funciones que definen el comportamiento de los objetos de la clase. Operan sobre los atributos del objeto (o sobre atributos estáticos en el caso de acceder a ```totalCuentas```).

**Objetos en el Stack y en el Heap:**
- **Stack:** ```Cuenta cuentaStack("Stack", 500);``` crea el objeto ```cuentaStack``` directamente en la pila de ejecución de la función ```main```. Los objetos en la pila tienen una vida útil automática; se crean cuando se declara la variable y se destruyen automáticamente cuando la variable sale de ámbito (en este caso, cuando ```main``` termina).
- **Heap:** ```Cuenta* cuentaHeap = new Cuenta("Heap", 1000);``` utiliza el operador ```new``` para asignar memoria dinámicamente en el heap y construir un objeto ```Cuenta``` ahí. ```cuentaHeap``` es un puntero que almacena la dirección de memoria donde reside el objeto real en el heap. Los objetos en el heap deben ser gestionados manualmente: se crean con ```new``` y deben ser destruidos explícitamente con ```delete``` para liberar la memoria. Si no se usa ```delete```, ocurre una fuga de memoria.

**Punteros y Referencias:**
- **Puntero:** ```Cuenta* cuentaHeap; y Cuenta* punteroCuentaHeap;```. Un puntero es una variable que almacena una dirección de memoria. ```cuentaHeap``` almacena la dirección del objeto creado en el heap. ```punteroCuentaHeap``` también apunta a la misma dirección. Se accede a los miembros de un objeto a través de un puntero utilizando el operador flecha (```->```).
- **Referencia:** ```Cuenta& refCuentaStack = cuentaStack;```. Una referencia es un alias para un objeto existente. Una vez inicializada, una referencia no se puede "re-enlazar" a otro objeto. Se accede a los miembros del objeto a través de una referencia utilizando el operador punto (```.```), igual que si fuera el objeto original. Las referencias se usan como parámetros de función para pasar objetos de manera eficiente para permitir que una función modifique el objeto original que se le pasó. En este caso, ```refCuentaStack``` permite modificar directamente el objeto ```cuentaStack```.

**Variables Estáticas:**
- ```static int totalCuentas;```. Un miembro de datos static pertenece a la clase en sí misma, no a un objeto de la clase. Existe solo una copia de ```totalCuentas``` compartida por todos los objetos ```Cuenta```. Se inicializa fuera de la clase (```int Cuenta::totalCuentas = 0;```). Se usa aquí para llevar un registro global del número de objetos ```Cuenta``` que existen en cualquier momento.

**Depuración de Programas:**
- Aunque el código no incluye herramientas de depuración formal (como usar un depurador paso a paso), las sentencias ```cout``` distribuidas en los constructores, destructores y métodos sirven como un mecanismo de trazabilidad básico. Imprimir mensajes en puntos clave de la ejecución ayuda a seguir el flujo del programa, ver cuándo se crean y destruyen objetos, y observar cómo cambian los valores de las variables (```saldoExtra``` en ```main```). Esto es una técnica común utilizada durante la fase de depuración para entender qué está pasando.

### Análisis Detallado de la Memoria
1. **Segmento de Código (o Texto):** Contiene las instrucciones ejecutables compiladas del programa. Este segmento suele ser de solo lectura.  
Incluye:
- Las instrucciones máquina correspondientes a la función ```main()```.
- Las instrucciones máquina correspondientes a todos los métodos de la clase ```Cuenta```: constructor, destructor, ```modificarSaldoValor()```, ```modificarSaldoReferencia()```, ```mostrar()```.
- Cualquier otra función o código global del programa.

2. **Segmento de Datos Inicializados (o Datos):** Contiene variables globales y estáticas que han sido inicializadas explícitamente con un valor no cero.
Incluye:
- Las cadenas literales utilizadas en las llamadas a ```cout``` (ej: ```"Inicio del programa.\n"```, ```"Constructor: Cuenta de "```, ```"Destructor: Cuenta de "```, etc.). Aunque a veces se colocan en un segmento de solo lectura separado dentro del área de datos.

3. **Segmento BSS (Block Started by Symbol):** Contieene variables globales y estáticas que no han sido inicializadzs explícitamente o han sido inicializadas a cero.
Incluye:
- La variable miembro estática ```Cuenta::totalCuentas```. Como se inicializa a 0 (```int Cuenta::totalCuentas = 0;```), por lo general reside aquí.

4. **Segmento de Stack (Pila):** Se utiliza para almacenar variables locales dentro de las funciones, parámetros de función, direcciones de retorno de llamadas a funciones y, en C++, objetos creados directamente sin ```new```.
Durante la ejecución de ```main```, incluye:
- La variable local ```cuentaStack```. Dado que es un objeto completo en la pila, sus miembros de datos (```nombre```, ```saldo```) se almacenan dentro de este espacio en la pila.
- La variable local ```saldoExtra```.
- El puntero local ```Cuenta* cuentaHeap```. Estee puntero está en la pila, pero la memoria a la que apunta está en el heap.
- La referencia local ```Cuenta& refCuentaStack```. Internamente, una referencia a menudo se implementa como un puntero constante, por lo que ocupa un espacio en la pila (el tamaño de un puntero).
- El puntero local ```Cuenta* punteroCuentaHeap```.
- Durante las llamadas a métodos (ej. ```cuentaStack.mostrar()```, ```cuentaStack.modificarSaldoValor(saldoExtra)```), los parámetros pasados (si se pasan por valor) y las variables locales de esos métodos, así como la dirección de retorno para volver a main, se colocan temporalmente en la pila. Cuando ```modificarSaldoValor``` se llama, el parámetro ```int nuevoSaldo``` se almacena en la pila dentro del marco de esa función.

5. **Segmento de Heap (Montículo):** Se utiliza para la asignación dinámica de memoria en tiempo de ejecución, usando operadores como ```new``` y ```delete```. La gestión de esta memoria es responsabilidad del programador.
Incluye:
- El bloque de memoria asignado por ```new Cuenta("Heap", 1000)```. Este bloque contiene los miembros de datos (```nombre```, ```saldo```) del objeto Cuenta que se crea dinámicamente. La dirección de inicio de este bloque es lo que se almacena en el puntero ```cuentaHeap``` (que está en la pila). Cuando se llama a ```delete cuentaHeap;```, este bloque de memoria se libera y vuelve a estar disponible para futuras asignaciones en el heap.
