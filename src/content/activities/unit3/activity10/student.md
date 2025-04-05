## Solución a la décima actividad
### ¿Qué ocurre después de llamar a la función ```cambiarNombre```? ¿Por qué aparece el mensaje ```Destructor: Punto cambiado(70, 80) destruido.```?
Cuando se llama a la función ```cambiarNombre(original, "cambiado");```, en realidad se crea una copia del objeto original que se pasa a la función. 
Al finalizar la ejecución de ```cambiarNombre```, esta copia local (```p```) se destruye automáticamente, lo cual hace que vea el mensaje ```Destructor: Punto cambiado(70, 80) destruido.```. Eso sucede porque la copia tiene un tiempo de vida limitado solo al interior de esa función.
### ¿Por qué original sigue existiendo luego de llamar ```cambiarNombre```?
El objeto original sigue existiendo porque nunca se envió directamente a la función, solo una copia temporal de él. El objeto original permanece intacto.
### En qué parte del mapa de memoria se encuentra ```original``` y en qué parte se encuentra ```p```? ¿Son el mismo objeto?
Al observar el depurador se ve que:
El objeto ```original``` está almacenado en el stack dentro de main. La copia ```p``` también se almacenó en el stack, pero en una dirección de memoria diferente. Por lo tanto, no son el mismo objeto. Cada uno tiene una ubicación distinta, confirmando que la copia es independiente del original.
### Modifica la función cambiarNombre: ¿Qué ocurre ahora? ¿Por qué?
Ahora el cambio realizado dentro de ```cambiarNombre``` comparado con el cambio realizado para uno de los puntos anteriores sí afectó al objeto original. Esto ocurre porque al pasar por referencia estoy trabajando directamente sobre el objeto original, sin hacer una copia. Al terminar la función tampoco apareció ningún destructor adicional, ya que no se creó ninguna copia.
### Modificar a ```cambiarNombre``` y a ```main```: ¿Qué ocurre ahora? ¿Por qué?
Los cambios realizados dentro de la función afectaron directamente al objeto original. Esto ocurre porque se pasa la dirección del objeto original, y dentro de la función se usa un puntero que apunta directamente al objeto original en memoria. Por lo tanto, tampoco se creó ninguna copia, y tampoco hubo destructor adicional.
### En este caso ¿Cuál es la diferencia entre pasar un objeto por valor, por referencia y por puntero?
- **Paso por valor:** se crea una copia del objeto original que vive solo dentro de la función. Cualquier cambio no afecta al original.
- **Paso por referencia (&):** la función trabaja directamente con el objeto original sin copias, y cualquier modificación afecta directamente al original.
- **Paso por puntero (*):** la función recibe la dirección del objeto original y modifica directamente sus valores mediante un puntero, afectando también al original.

