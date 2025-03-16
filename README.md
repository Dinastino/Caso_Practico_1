https://github.com/Dinastino/Caso_Practico_1.git
# Caso_Practico_1

# Diseño de la Arquitectura de Comunicación

## Paso 1: Análisis y Diseño de la Arquitectura de Comunicación

### Explicación de Modelos OSI y TCP/IP

El modelo OSI consta de siete capas que definen el proceso de comunicación de datos:

1. **Capa Física**: Es la encargada de la transmisión de bits a través de medios físicos como cables de trenzado o fibra óptica. También define estándares de conectores, interfaces mecánicas, eléctricas y ópticas como tensiones lógicas, tiempos de hold y set-up o métodos de transmisión. *Ejemplos*: Cables de red, conectores, tarjetas de red.

   
2. **Capa de Enlace de Datos**: Es la capa encargada de convertir el medio de transmisión puro en una línea de comunicación sin errores, detectándolos y corrigiéndolos asegurándose de una transmisión confiable, y organizar los datos en tramas. Se divide en la subcapa de control de acceso al medio compartido y la subcapa de control del flujo. *Ejemplos*: Switches, adaptadores de red, Ethernet.

   
3. **Capa de Red**: Se encarga del rutado desde origen a destino permitiendo la comunicación entre distintas redes. Se divide en rutado estático, tablas fijas ya codificadas, o rutado dinámico, ajustes a tiempo real. Tambien gestiona la congestión de las redes, asegura la calidad del servicio y resuelve la interconexión entre diferentes redes. *Ejemplos*: Routers, direcciones IP.

   
4. **Capa de Transporte**: Abstrae a las capas superiores de los cambios tecnológicos en las capas inferiores, dividiendo los datos para adaptarlos a la red. Garantiza una comunicación punto a punto libre de errores, asegurando que los mensajes lleguen completos y en orden, aunque en algunos casos pueden ser mensajes aislados sin garantía de secuencia. Los datos se manejan como segmentos o datagramas, dependiendo del protocolo utilizado. Opera desde el nodo inicial hasta el nodo final. *Ejemplos*: protocolos TCP, UDP.

   
5. **Capa de Sesión**: Permite que diferentes maquinas establezcan y mantengan sesiones de comunicación. Utiliza múltiples servicios como la administración de tokens, control de secciones criticas, y la sincronización, manejando las interrupciones.

    
6. **Capa de Presentación**: Se ocupa de la sintaxis y semántica de la información transmitida permitiendo la comunicación entre nodos con diferentes formatos de datos.Se basa en estructuras de datos abstractas para estandarizar la interpretación de la información.

    
7. **Capa de Aplicación**: Capa que interactua con el usuario final y proporciona servicios como trasferencia de archivos, correo electrónico y navegación web. Contiene los protocolos mas utilizados como HTTP, FTP o SMPT entre otros.

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

#### Sedes:  
1.Madrid  

2.Málaga

#### Dispositivos:

Se utilizarán múltiples dispositivos para la implementación de la infraestructura de red. El diseño se basa en una segmentación eficiente de la red y un enfoque robusto en seguridad para garantizar la correcta operación de los sistemas y proteger la información sensible.

***Enrutamiento***: Para el enrutamiento, se implementará un router central que gestionará el tráfico entre las distintas redes. Adicionalmente, se instalará un switch en cada par de plantas, comenzando con la recepción y la planta 1, y se continuará de la misma forma para las demás plantas del edificio.
1. Router principal: Cisco ISR4331.
2. Switches de acceso: Cisco 2960-24TT (8 unidades).
3. Switch de multilayer: Cisco 3650-24PS.

***Seguridad***: La seguridad de la red se garantizará mediante la instalación de dos firewalls. Ambos firewalls aislarán las redes internas y externas con una zona desmilitarizada en medio para mayor seguridad.
1. Firewall: Cisco ASA 5505 (2 unidades).

***Servidores***: Los servidores web se ubicarán dentro de la DMZ(zona desmilitarizada), permitiendo acceso controlado desde el exterior, mientras que los servidores internos estarán situados en la red interna, asegurando un entorno aislado y más seguro para los datos sensibles.
1. Servidor: Server PT (7 unidades).

***Dispositivos***: Los ordenadores dentro de cada VLAN junto con los dispositivos de videoconferencia como los MCU, cámaras y micrófonos.

#### Segmentación de la Red:  
La red se segmentará en varias VLANs, siguiendo un esquema de distribución por plantas. El diseño será el siguiente:

1. La recepción y la planta 1 estarán asignadas a la VLAN 100.  
2. Las plantas 2 y 3 corresponderán a la VLAN 200.  
3. Las plantas 4 y 5 estarán en la VLAN 300.  
4. Las plantas 6 y 7 serán asignadas a la VLAN 400.  
5. Las plantas 8 y 9 estarán en la VLAN 500.  
6. Finalmente, a la planta 10 le corresponderá la VLAN 600.  


Para optimizar la administración de las VLANs, se implementará el protocolo VTP (VLAN Trunking Protocol), permitiendo una gestión centralizada y eficiente de las VLANs a lo largo de toda la red. Mediante VTP, los cambios en la configuración de VLAN se propagarán automáticamente a los switches, reduciendo la carga administrativa y evitando inconsistencias en la segmentación.


## Paso 2: Capa Física:
### Cálculo de la Tasa de Transmisión 
Se utiliza la fórmula de Shannon:

Donde: $C = B * log_2(1+SNR)$

Ancho de banda (B)

SNR: relación señal a ruido determinada.  
La relación señal a ruido se mide en dB en un ancho de banda es:
$𝑆𝑁𝑅 = 10 𝑙𝑜𝑔_{10}(𝑆𝑁𝑅) = 10^{\frac{SNR}{10}}$ [dB]

Ruido de mas o menos 30db para una asegurar conexión estable con alto trafico de datos y videoconferencias.  
SNR lineal= $10^{\frac{30}{10}} = 10^3 = 1000$

Trenzado:  

$C = 2,5 * 10^8 * log_2(1+1000) = 2,5 * 10^8 * log_2(1001) = 2,5 * 10^8 * 9.967 = 2.49 * 10^9bps = 2.49 Gbps$

Entre switches:

$C = 1* 10^9 * log_2(1001) =  1 * 10^9 * 9.967 = 9,96710^9 bps = 9.97 Gbps$

Fibra óptica:

$C = 1 * 10^{11} * log(1001) = 1x10^{11} * 9.967 = 9.97 * 10^{11} bps = 997 Gbps$

### Selección de Modulación

Se emplea el esquema de modulación 16-QAM (16-Quadrature Amplitude Modulation). Esta técnica ofrece un equilibrio óptimo entre eficiencia espectral y resistencia al ruido, permitiendo la transmisión de 4 bits por símbolo. Se ha seleccionado 16-QAM en lugar de modulaciones de orden superior, como 64-QAM o 256-QAM, debido a que los enlaces cableados presentan menor susceptibilidad al ruido. Esto garantiza una transmisión más fiable sin necesidad de aplicar esquemas complejos de corrección de errores.

## Paso 3: Capa de Red
### Esquema de direccionamiento de IP y subneteo

Red interna de la sede: 198.168.0.0
- **Dirección de Red:** 198.168.0.0
- **Rango de Hosts:** 198.168.0.1 - 198.168.0.254
- **Dirección de Broadcast:** 198.168.0.255

| **VLAN** | **Subred**       | **Gateway**      | **Broadcast**      | **Rango de Hosts**          |
|----------|------------------|------------------|--------------------|-----------------------------|
| **100**  | 198.168.1.0/27   | 198.168.1.1      | 198.168.1.31       | 198.168.1.2 - 198.168.1.30  |
| **200**  | 198.168.1.32/27  | 198.168.1.33     | 198.168.1.63       | 198.168.1.34 - 198.168.1.62 |
| **300**  | 198.168.1.64/27  | 198.168.1.65     | 198.168.1.95       | 198.168.1.66 - 198.168.1.94 |
| **400**  | 198.168.1.96/27  | 198.168.1.97     | 198.168.1.127      | 198.168.1.98 - 198.168.1.126|
| **500**  | 198.168.1.128/27 | 198.168.1.129    | 198.168.1.159      | 198.168.1.130 - 198.168.1.158|
| **600**  | 198.168.1.160/27 | 198.168.1.161    | 198.168.1.191      | 198.168.1.162 - 198.168.1.190|


***Ejemplo***  

Oficina con 30 hosts (Sala 1 - VLAN 100)
Si una oficina tiene hasta 30 dispositivos, necesitamos al menos 32 direcciones IP (30 hosts + 1 gateway + 1 reserva).
Se necesita una máscara que permita 32 direcciones, lo que corresponde a /27 (255.255.255.224).

Cálculo
Dirección de Red: 10.0.1.0
Máscara de Subred: 255.255.255.224
Dirección de Broadcast: 10.0.1.31
Rango de Hosts: 10.0.1.1 - 10.0.1.30
Gateway: 10.0.1.1
Cálculo para todas las oficinas y VLANs
| VLAN | Área                        | Máscara           | Dirección de Red | Broadcast       | Rango de Hosts       |
|------|-----------------------------|-------------------|------------------|-----------------|----------------------|
| 100  | Sala 1                      | /27 (255.255.255.224) | 10.0.1.0         | 10.0.1.31       | 10.0.1.1 - 10.0.1.30 |
| 200  | Sala 2                      | /27               | 10.0.1.32        | 10.0.1.63       | 10.0.1.33 - 10.0.1.62 |
| 300  | Sala 3                      | /27               | 10.0.1.64        | 10.0.1.95       | 10.0.1.65 - 10.0.1.94 |
| 400  | Sala 4                      | /27               | 10.0.1.96        | 10.0.1.127      | 10.0.1.97 - 10.0.1.126 |





### Enrutamiento
***Dijkstra***  


Para implementar el algoritmo de Dijkstra en un diagrama de rutas entre sedes, necesitamos representar un grafo donde las sedes sean los nodos y las rutas entre ellas sean los bordes con un peso asociado (esto podría representar, por ejemplo, la distancia o el tiempo de viaje).

Pasos del algoritmo de Dijkstra:
1. Inicialización: Se asigna un valor de "infinito" a todas las sedes, excepto a la sede de inicio, que tiene un valor de 0. Este valor representa la distancia más corta desde la sede de inicio a cada sede.

2. Selección del nodo: El nodo con el valor más bajo (la distancia más corta) es seleccionado como el nodo actual. A este nodo se le asignan sus vecinos, actualizando las distancias si se encuentra un camino más corto.

3. Actualización de distancias: Para cada vecino del nodo actual, calculamos si el camino pasando por el nodo actual es más corto que el camino conocido hasta ese momento. Si es más corto, actualizamos la distancia al vecino.

4. Marcado como visitado: Una vez que todos los vecinos han sido explorados, marcamos el nodo actual como visitado y pasamos al siguiente nodo con la distancia más baja no visitada.

5. Repetir: Este proceso se repite hasta que todos los nodos hayan sido visitados.

***Enrutamiento por inundación***


El enrutamiento por inundación es un método donde los paquetes se envían a todas las rutas disponibles en caso de falla, garantizando que lleguen a su destino. Se usa en situaciones de contingencia cuando la red principal se cae.


1. **Definir el Escenario de Contingencia**
Identificar los puntos críticos en la red donde pueden ocurrir fallos.
Determinar si el enrutamiento por inundación será permanente o temporal (activado solo en caso de falla).


2. **Configurar la Propagación de Paquetes**
Cada nodo que recibe un paquete lo reenvía a todos sus vecinos excepto al nodo del que lo recibió.
Implementar una estrategia para evitar la duplicación excesiva de paquetes:
TTL (Time-To-Live): Limitar la cantidad de veces que un paquete puede reenviarse.
Secuenciamiento: Etiquetar los paquetes con identificadores únicos para evitar reenvíos innecesarios.


4. **Implementar en la Red**
A nivel de hardware: Configurar switches o routers con soporte para reenvío automático de paquetes.
A nivel de software: Programar protocolos que activen el enrutamiento por inundación solo cuando se detecte un fallo en las rutas principales.


## Capa de trasporte
## Capa de aplicación y multimedia
## Seguridad
