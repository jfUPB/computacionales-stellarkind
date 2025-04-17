## Solución a la onceava actividad
### ¿Qué puedo concluir sobre los miembros estáticos y de instancia de una clase en C++? ¿Cómo se gestionan en memoria?
Después de mirar el depurador, entendí que los miembros de instancia (como ```valor```) se almacenan individualmente en cada objeto creado, por lo que cada objeto tiene su propia copia y dirección de memoria separada. Por el contrario, los miembros estáticos (como ```total```) no están asociados a cada objeto, sino que son compartidos por todos los objetos de la clase. Por lo tanto, solo hay una copia en memoria del miembro estático, independientemente del número de objetos que cree.
#### Miembros de instancia:  
- **Ventajas:** permiten mantener información específica de cada objeto.  
- **Desventajas:** ocupan memoria por cada objeto creado.  
#### Miembros estáticos:  
- **Ventajas:** eficientes en memoria, ideales para contar objetos creados o mantener información compartida.  
- **Desventajas:** no sirven para almacenar información única por objeto, ya que todos los objetos comparten la misma variable.  
#### ¿Cuándo es útil utilizarlos?
Es útil usar miembros estáticos cuando quiero compartir un valor entre todas las instancias de una clase, por ejemplo, para contar cuántos objetos se han creado. Los miembros de instancia son ideales para almacenar valores únicos para cada objeto individual.
### En qué segmento de memoria están almacenados ```c1```, ```c2```, ```c3``` y ```Contador::total```?  
- Los objetos ```c1``` y ```c2``` están almacenados directamente en el stack, ya que fueron creados en memoria automática. Cada uno tiene su propia dirección y almacenamiento separado.
- La variable ```c3``` (el puntero) está almacenada también en el stack, porque es una variable local que contiene únicamente la dirección de memoria del objeto al que apunta.
- El objeto al que apunta ```c3``` (creado con ```new```) está almacenado en el heap, ya que reservé memoria dinámica para él, que persiste hasta que lo elimino explícitamente con ```delete```.
- El miembro estático ```Contador::total``` está almacenado en el segmento de datos estáticos (similar a una variable global), por lo tanto, tiene una sola dirección fija en memoria compartida por todos los objetos.
