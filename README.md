https://github.com/Dinastino/Caso_Practico_1.git
# Caso_Practico_1

# Diseño de la Arquitectura de Comunicación

## Paso 1: Análisis y Diseño de la Arquitectura de Comunicación

### Explicación de Modelos OSI y TCP/IP

El modelo OSI consta de siete capas que definen el proceso de comunicación de datos:

1. **Capa Física**: Es la encargada de la transmisión de bits a traves de medios fisicos como cables de trenzado o fibra optica. También define estandares de conectores, interfaces mecanicas, electricas y opticas como tensiones logicas, tipempos de hold y set-up o metodos de transmisión. *Ejemplos*: Cables de red, conectores, tarjetas de red.

   
2. **Capa de Enlace de Datos**: Es la capa encargada de convertir el medio de transmisión puro en una línea de comunicación sin errores, detectandolos y corrigendolos asegurandose de una transmision confiable, y organizar los datos en tramas. Se divide en la subcapa de control de acceso al medio compartido y la subcapa de control del flujo. *Ejemplos*: Switches, adaptadores de red, Ethernet.

   
3. **Capa de Red**: Se encarga del rutado desde origen a destino permition la comunicaion entre distintas redes. Se divide en rutado estatico, tablas fijas ya codificadas, o rutado dinamico, ajustes a tiempo real. Tambien gestiona la congestion de las redes, asegura la calidad del servicio y resuelve la interconexión entre diferentes redes. *Ejemplos*: Routers, direcciones IP.

   
4. **Capa de Transporte**: Abstrae a las capas superiores de los cambios tecnológicos en las capas inferiores, dividiendo los datos para adaptarlos a la red. Garantiza una comunicación punto a punto libre de errores, asegurando que los mensajes lleguen completos y en orden, aunque en algunos casos pueden ser mensajes aislados sin garantía de secuencia. Los datos se manejan como segmentos o datagramas, dependiendo del protocolo utilizado. Opera desde el nodo inicial hasta el nodo final. *Ejemplos*: protocolos TCP, UDP.

   
5. **Capa de Sesión**: Permite que diferentes maquinas establezcan y mantengan sesiones de comunicaión. Utiliza multiples servicios la aadministracion de token, control de secciones criticas, y la sincronización, manejando las interrupciones.

    
6. **Capa de Presentación**: Se ocupa de la sintaxis y semántica de la informacion transmitida permitienddo la comunicación entre nodos con diferentes formatos de datos.Se basa en estructuras de datros abstractas para estanddarizar la interpretación de la información.

    
7. **Capa de Aplicación**: Capa que iteractua con el usuario final y proporcoina servicios como trasferencia de archivos, correo electronico y navegación web. Contiene los protocolos mas utilizados como HTTP, FTP o SMPT entre otros.

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



### Diseño Lógico de la Red:

Diagrama en el drawio

#### Dispositivos:

Se utilizarán múltiples dispositivos para la implementación de la infraestructura de red. El diseño se basa en una segmentación eficiente de la red y un enfoque robusto en seguridad para garantizar la correcta operación de los sistemas y proteger la información sensible.

***Enrutamiento***: Para el enrutamiento, se implementará un router central que gestionará el tráfico entre las distintas redes. Adicionalmente, se instalará un switch en cada par de plantas, comenzando con la recepción y la planta 1, y se continuará de la misma forma para las demás plantas del edificio.

***Seguridad***: La seguridad de la red se garantizará mediante la instalación de dos firewalls. Ambos firewalls aislaran las redes internas y externas con una zona desmilitarizada enmedio para mayor seguridad.

***Servidores***: Los servidores web se ubicarán dentro de la DMZ, permitiendo acceso controlado desde el exterior, mientras que los servidores internos estarán situados en la red interna, asegurando un entorno aislado y más seguro para los datos sensibles.

***Dispositivos***: Los ordenadores dentro de cada VLAN junto con los dispositivos de videoconferencia como los MCU, camaras y microfonos.


#### Segmentación de la Red:  


La red se segmentará en varias VLANs, siguiendo un esquema de distribución por plantas. El diseño será el siguiente:

1.La recepción y la planta 1 estarán asignadas a la VLAN 100. 
2.Las plantas 2 y 3 corresponderán a la VLAN 200.  
3.Las plantas 4 y 5 estarán en la VLAN 300.  
4.Las plantas 6 y 7 serán asignadas a la VLAN 400.  
5.Las plantas 8 y 9 estarán en la VLAN 500.  
6.Finalmente, las plantas 10 y 11 corresponderán a la VLAN 600.  


Para optimizar la administración de las VLANs, se implementará el protocolo VTP (VLAN Trunking Protocol), permitiendo una gestión centralizada y eficiente de las VLANs a lo largo de toda la red. Mediante VTP, los cambios en la configuración de VLAN se propagarán automáticamente a los switches, reduciendo la carga administrativa y evitando inconsistencias en la segmentación.
