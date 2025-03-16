## Solución a la cuarta actividad
### Experimento 1: modificar el segmento de texto:
- **¿Qué ocurre?** R/ El programa se deja de ejecutar con un error que dice ```0xC0000005: Infracción de acceso al escribir en la ubicación 0x00007FF613B51348.``` lo que al buscar en google me indica que hayun error de tipo "Excepción no controlada: Access Violation"  
- **¿Por qué?** R/ Pues este segmento de texto(o código pues) está protegido contra modificaciones por el sistema operativo para preservar la integridad del programa.  
### Experimento 2: modificar el segmento de datos (constante global):  
- **¿Qué ocurre?** R/  El programa se deja de ejecutar con un error que dice ```Se produjo una excepción no controlada: infracción de acceso de escritura. ptr fue 0x7FF68C73BBB0.```. Que al igual que en el experimento anteriores en Windows un de tipo "Excepción no controlada: Access Violation"
- **¿Por qué?** R/ Se da porque```mensaje_ro``` es una constante global, por lo tanto, se guarda en una región especial protegida contra escritura. Al intentar modificar su contenido, el sistema operativo detecta inmediatamente esta operación ilegal y bloquea el programa, generando un error.
