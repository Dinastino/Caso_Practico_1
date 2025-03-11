# Caso_Practico_1

# Diseño de la Arquitectura de Comunicación

## Paso 1: Análisis y Diseño de la Arquitectura de Comunicación

### Explicación de Modelos OSI y TCP/IP

El modelo OSI consta de siete capas que definen el proceso de comunicación de datos:

1. **Capa Física**: Es la encargada de la transmisión de bits a traves de medios fisicos como cables de trenzado o fibra optica. También define estandares de conectores, interfaces mecanicas, electricas y opticas como tensiones logicas, tipempos de hold y set-up o metodos de transmisión. *Ejemplos*: Cables de red, conectores, tarjetas de red.

   
3. **Capa de Enlace de Datos**: Asegura una comunicación confiable entre nodos adyacentes. Controla los errores de transmisión, la dirección física (MAC) y organiza los datos en tramas. *Ejemplos*: Switches, adaptadores de red, Ethernet.

   
5. **Capa de Red**: Determina rutas y direcciones IP y utiliza direcciones IP para la gestión de la comunicación entre dispositivos en redes diferentes. *Ejemplos*: Routers, direcciones IP.

   
7. **Capa de Transporte**: Gestiona la entrega confiable de datos  proporcionando control de flujo, control de datos y segmentacion. *Ejemplos*: protocolos TCP, UDP.

   
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

