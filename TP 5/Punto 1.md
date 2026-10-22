a) ICMP (Internet Control Message Protocol): Es un protocolo de la capa de red (capa 3) diseñado para transferir mensajes de control, diagnóstico y notificación de errores entre routers y hosts.
No, este no está diseñado para transportar datos de usuario o aplicaciones(web, correo, etc), sino únicamente tráfico de control y gestión de su propia red.

b) La relación es que ICMP es un servicio dependiente de I, osea, este viaja dentro de IP, cada mensaje de ICMP es la carga de un paquete IP. El receptor lo sabe gracias al campo “Protocolo”, que se encuentra dentro de la cabecera del paquete IP.

c) Es una herramienta de diagnóstico que verifica si un host remoto está activo y alcanzable a través de la red,  además de medir el tiempo que tardan en ir y volver los paquetes(latencia).
Echo Request(Petición de Eco): Es un mensaje enviado por el origen solicitando al destino que le responda
Echo Reply(Respuesta de Eco): Mensaje devuelto por el destino al origen confirmando que está activo  y recibe la solicitud.
Estos se distinguen por el campo Type(Tipo) de la cabeza ICMP, si:
Si Type=8 → Echo Request
Si Type=0 → Echo Reply

d) Todos los mensajes ICMP empiezan con una cabecera de 64 bits que consta de los siguientes campos:
Tipo (8 bits): especifica el tipo de mensaje ICMP.
Código (8 bits): se usa para especificar parámetros del mensaje que se pueden codificar en uno o unos pocos bits.
Suma de comprobación (16 bits): suma de comprobación del mensaje ICMP entero. Se utiliza el mismo algoritmo de suma de comprobación que en IP.
Parámetros (32 bits): se usa para especificar parámetros más largos.


| Capa (Como la nombra Wireshark) | Direccion/identificado origen  | Dirección/Identificador destino | ¿Qué campo indica qué protocolo viene “adentro”? |
| :---- | :---- | :---- | :---- |
| Ethernet | 14:D4:24:61:D4:93 | 02:10:18:63:ED:34 | IPv4 (0x0800) |
| Internet Protocol Version 4  | 192.168.0.190 | 8.8.8.8 | ICMP (1) |
| Internet Control Message Protocol | No tiene direcciones | No tiene direcciones | No tiene campo de “siguiente protocolo” Type 8 / Code 0 definen el formato y lo que sigue son los datos del Echo |
| Datos / payload | Sin direcciones  | Sin direcciones  | No hay más capas (32 bytes de datos) |

![][image1]

![][image2]

1) *La MAC destino del Echo Request enviado a 8.8.8.8, ¿Es la MAC de 8.8.8.8? ¿De qué equipo es?. Compárenla con la MAC destino del ping al gateway. ¿Que conclusión sacan sobre el alcance de una dirección MAC frente al de una dirección IP?*

- No es la MAC de 8.8.8.8, es ‘02:10:18:63:ed:34’(Gateway), es la misma que en el ping de gateway y coincide con la entrada 192.168.0.1 (arp \-a). A modo de conclusión, la MAC solo tiene alcance local, un salto dentro de la LAN. Sirve para entregar la trama al siguiente dispositivo, que la reenvía. La IP identifica al destino final y se mantiene extremo a extremo, mientras que las MAC se reescriben en cada salto.  
    
    
2) *Comparen un Echo Request con su Echo Reply (Wireshark los vincula en el campo \[Response Frame: …\]). Hagan una lista de los campos que cambian y de los que se mantienen en Ethernet, IP e ICMP. ¿Por qué tiene sentido cada cambio? ¿Por qué  el identificador y el número de secuencia se mantienen?*   

| Capa | Cambia | Se mantiene |
| :---- | :---- | :---- |
| Ethernet | MAC origen y destino | Type (IPv4) |
| IP | IP origen y destino, Identificación (0xf941 → 0x0000), TTL (128 → 117), Header Checksum | Versión, Header/Total Lenght (60), Flags, Protocol |
| ICMP  | Type (8 → 0), Checksum (0x4d53 → 0x5553) | Code, Identifier (0x0001), Sequence Number (8), Data |



- MAC e IP: El Reply viaja en sentido contrario, así que los roles se invierten.  
- Type: Es lo que distingue pedido de respuesta.  
- TTL: Cada emisor arranca con su valor inicial y los routers lo decrementan en el camino.  
- Identification: La asigna cada emisor con su criterio.  
- Checksums: Se recalculan porque cambió el contenido que cubren.  
- Identifier y Sequence Number se mantienen: El que responde los copia. Así ping empareja cada Reply con su Request, calcula el RTT y detecta pérdidas o desorden. Identifier identifica la sesión de ping y Sequence Number el pedido concreto. 

3) *¿Dónde está el payload de ping? ¿Cuántos bytes tiene y qué contiene? ¿Es igual en el Reply? Si en el grupo hay una computadora con Windows y otra con Linux, compárenlos: ¿Que les sugiere que sean distintos?*   
     
- Está dentro de ICMP, después de los 8 bytes de cabecera (DATA), también contiene 32 bytes y el alfabeto en ASCII: abcdefghijklmnopqrstuvwabcdefghi. Es idéntico en el Reply (Se comprobó en 9692 y 9695), aunque para realizar la comparativa de Windows vs Linux, no contaba con el SO necesario. 


4) 

| Paquete | TTL |
| :---- | :---- |
| Echo Request (Windows) | 128 |
| Echo Reply de 8.8.8.8 | 117 |
| Echo Reply del gateway | 64 |


- No son iguales porque los paquetes nacen en equipos distintos con TTL inicial distinto (Windows 128, otros sistemas 64 o 255), y porque cada router decrementa el TTL en 1\. La función del TTL es evitar que un paquete circule indefinidamente en un loop de enrutamiento. Si llega a 0, el router lo descarta y envía un ICMP “Time Exceeded”. En este trabajo el Reply llega con 64 porque el router no recorrió saltos intermedios.

5) Encapsulación:  
- ![][image3]
