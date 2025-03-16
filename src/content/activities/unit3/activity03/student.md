## Solución a la tercer actividad:
### Captura de pantalla con el resultado de la ejecución del programa:  



<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
</head>
<body>

<table>
    <caption>Mapa de Memoria Real del Programa en C++</caption>
    <thead>
        <tr>
            <th>Dirección (hexadecimal)</th>
            <th>Contenido</th>
            <th>Segmento</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0x00007FF7496BF4C0</td>
            <td>global_no_inicializada</td>
            <td>Variables globales</td>
        </tr>
        <tr>
            <td>0x00007FF7496BF004</td>
            <td>var_estatica (static, dentro de función)</td>
            <td>Variables estáticas</td>
        </tr>
        <tr>
            <td>0x00007FF7496BF000</td>
            <td>global_inicializada = 42</td>
            <td>Variables globales</td>
        </tr>
        <tr>
            <td>0x00007FF7496BBBC0</td>
            <td>"Hola, memoria de solo lectura"</td>
            <td>Segmento de solo lectura</td>
        </tr>
        <tr>
            <td>0x00000165FE3040F4</td>
            <td>arrayHeap[9] = 9</td>
            <td rowspan="10">Heap (asignación dinámica)</td>
        </tr>
        <tr><td>0x00000165FE3040F0</td><td>arrayHeap[8] = 8</td></tr>
        <tr><td>0x00000165FE3040EC</td><td>arrayHeap[7] = 7</td></tr>
        <tr><td>0x00000165FE3040E8</td><td>arrayHeap[6] = 6</td></tr>
        <tr><td>0x00000165FE3040E4</td><td>arrayHeap[5] = 5</td></tr>
        <tr><td>0x00000165FE3040E0</td><td>arrayHeap[4] = 4</td></tr>
        <tr><td>0x00000165FE3040DC</td><td>arrayHeap[3] = 3</td></tr>
        <tr><td>0x00000165FE3040D8</td><td>arrayHeap[2] = 2</td></tr>
        <tr><td>0x00000165FE3040D4</td><td>arrayHeap[1] = 1</td></tr>
        <tr><td>0x00000165FE3040D0</td><td>arrayHeap[0] = 0 (primer elemento del heap)</td></tr>
        <tr>
            <td>0x00000014FED1F734</td>
            <td>Variable local 'c' (resultado = 30)</td>
            <td rowspan="3">Stack (variables locales)</td>
        </tr>
        <tr><td>0x00000014FED1F714</td><td>Variable local 'b' = 20</td></tr>
        <tr><td>0x00000014FED1F6F4</td><td>Variable local 'a' = 10 (breakpoint aquí)</td></tr>
    </tbody>
</table>

</body>
</html>
