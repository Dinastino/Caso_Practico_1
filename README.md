https://github.com/Dinastino/Caso_Practico_1.git
# Caso_Practico_1

# Diseño de la Arquitectura de Comunicación

## Paso 1: Análisis y Diseño de la Arquitectura de Comunicación

### Explicación de Modelos OSI y TCP/IP

El modelo OSI consta de siete capas que definen el proceso de comunicación de datos:

1. **Capa Física**: Es la encargada de la transmisión de bits a traves de medios fisicos como cables de trenzado o fibra optica. También define estandares de conectores, interfaces mecanicas, electricas y opticas como tensiones logicas, tipempos de hold y set-up o metodos de transmisión. *Ejemplos*: Cables de red, conectores, tarjetas de red.

   
3. **Capa de Enlace de Datos**: Es la capa encargada de convertir el medio de transmisión puro en una línea de comunicación sin errores, detectandolos y corrigendolos asegurandose de una transmision confiable, y organizar los datos en tramas. Se divide en la subcapa de control de acceso al medio compartido y la subcapa de control del flujo. *Ejemplos*: Switches, adaptadores de red, Ethernet.

   
5. **Capa de Red**: Se encarga del rutado desde origen a destino permition la comunicaion entre distintas redes. Se divide en rutado estatico, tablas fijas ya codificadas, o rutado dinamico, ajustes a tiempo real. Tambien gestiona la congestion de las redes, asegura la calidad del servicio y resuelve la interconexión entre diferentes redes. *Ejemplos*: Routers, direcciones IP.

   
7. **Capa de Transporte**: Abstrae a las capas superiores de los cambios tecnológicos en las capas inferiores, dividiendo los datos para adaptarlos a la red. Garantiza una comunicación punto a punto libre de errores, asegurando que los mensajes lleguen completos y en orden, aunque en algunos casos pueden ser mensajes aislados sin garantía de secuencia. Los datos se manejan como segmentos o datagramas, dependiendo del protocolo utilizado. Opera desde el nodo inicial hasta el nodo final. *Ejemplos*: protocolos TCP, UDP.

   
9. **Capa de Sesión**: Establece, mantiene y termina las sesiones de comunicación entre aplicaciones.

    
11. **Capa de Presentación**: Convierte y cifra datos.

    
13. **Capa de Aplicación**: Interactúa con el usuario final (HTTP, FTP, SMTP).

El modelo TCP/IP se basa en cuatro capas:

1. **Capa de Acceso a la Red**: Equivale a las capas física y de enlace de datos del modelo OSI.
2. **Capa de Internet**: Equivale a la capa de red del modelo OSI y maneja direccionamiento IP.
3. **Capa de Transporte**: Similar a la del modelo OSI, emplea TCP o UDP.
4. **Capa de Aplicación**: Combina las capas de aplicación, presentación y sesión del modelo OSI.

Estos modelos se integran en la solución asegurando una comunicación estructurada y eficiente entre dispositivos.

### Comparación entre el Modelo OSI y el Modelo TCP/IP

| **Capa**               | **Modelo OSI**                     | **Modelo TCP/IP**                  |
|------------------------|------------------------------------|------------------------------------|
| **Capa 1**              | Capa Física                        | Capa de Acceso a la Red           |
| **Capa 2**              | Capa de Enlace de Datos            | Capa de Acceso a la Red           |
| **Capa 3**              | Capa de Red                        | Capa de Internet                  |
| **Capa 4**              | Capa de Transporte                 | Capa de Transporte                |
| **Capa 5**              | Capa de Sesión                     | Capa de Aplicación (combinada)    |
| **Capa 6**              | Capa de Presentación               | Capa de Aplicación (combinada)    |
| **Capa 7**              | Capa de Aplicación                 | Capa de Aplicación (combinada)    |

