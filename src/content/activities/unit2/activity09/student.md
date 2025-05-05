## Solución a la novena actividad
### Traducción de programa en binario a C#:
``` csharp
using System;

class Program {
    // dirección base de SCREEN y tamaño del arreglo (8192 palabras)
    const int SCREEN_BASE = 16384;
    const int SCREEN_SIZE = 8192;

    // Simulación de los dispositivos:
    static int KBD = 0; // Se puede modificar para simular la presión de una tecla (0 = sin tecla, distinto de 0 = tecla presionada)
    static int[] SCREEN = new int[SCREEN_SIZE]; //  representa la pantalla

    static void Main() {
        // este puntero/pointer vendría siendo la variable que almacena una dirección dentro de SCREEN.
        int pointer = SCREEN_BASE; // Se inicializa en la dirección base de la pantalla

        // Bucle de espera: mientras no se presione una tecla, se decrementa el puntero.
        while (true) {
            if (KBD != 0) {
                break; // presiona alguna tecla y se sale del bucle.
            }
            int diff = pointer - SCREEN_BASE; // Se calcula la diferencia entre pointer y SCREEN_BASE.
            if (diff <= 0) {
                continue; // Si la diferencia es menor o igual que cero, se sigue esperando sin modificar pointer.
            }
            pointer--; // De lo contrario, el puntero disminuye.
        }

        // Si dectecta que se presionó una tecla,
        int diff2 = pointer - 24576; // se calcula la diferencia entre el puntero y 24576 (valor usado en el programa original)
        if (diff2 >= 0) {
        }

        // Se escribe -1 en la posición de la pantalla correspondiente.
        int index = pointer - SCREEN_BASE; // como la pantalla va desde 16384 hasta 16384+8192-1, el índice es (pointer - SCREEN_BASE)
        if (index >= 0 && index < SCREEN_SIZE) {
            SCREEN[index] = -1;
            Console.WriteLine("SCREEN[{0}] se ha establecido en -1.", index);
        } else {
            Console.WriteLine("El puntero ({0}) está fuera del rango de la pantalla.", pointer);
        }

        // Reinicio del programa (en el original salta a dirección 0).
        Console.WriteLine("Reiniciando el programa...");
        Main();
    }
}

```
