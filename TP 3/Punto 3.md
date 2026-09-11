# Transporte de informacion mediante TCP #  

## A) ¿Qué problema(s) resuelve TCP que no resuelve directamente Ethernet ni IP? ##

El protocolo TCP resuelve varios problemas que no resuelven IP ni Ethernet:

  - Garantiza que los paquetes de datos lleguen de extremo a extremo sin errores, perdidas o duplicados. Analiza que todo llegue correctamente a traves de confirmaciones de recibo y reenvios.
  - Numera secuencialmente cada byte transmitido para que el receptor pueda ordenar correctamente los paquetes de datos.
  - Protege al receptor un posible desborde de memoria, controlando al emisor en la cantidad de mensajes o datos que envia y ademas controla la congestion de la red, regulando la velocidad de envio de datos.
  - Gestiona protocolos, para que aplicaciones y proceso puedan enviar y recibir sus paquetes de datos simultaneamente a traves de una misma IP sin que se mezclen sus datos.

<div> <br> </div>

## B) Investigar los campos más importantes de la metadata en un frame TCP. ¿Para qué sirve cada uno? ##

Los campos mas importantes en un frame TCP son:  
 - **Los puertos de origen y destino**: Como aclaramos anteriormente, esto permite organizar los paquetes recibidos y enviarlos al programa o proceso que lo solicito.
 - **Numeros de secuencia**: Son los que se encargan de asignarle un valor secuencial a cada paquete enviado para que luego el receptor pueda reordenarlos correctamente.
 - **Banderas de control**: Son las que gestionan la conexion. Tanto para iniciar, cortar, cerrar o sincronizar el envio de datos.
 - **Tamaño de ventana**: Este campo es el que se encarga de regular el flujo de datos. Avisa al emisor del espacio libre disponible para que no se sature y se pierdan datos.

<div> <br> </div>

## C) Explicar el Three y Four way handshake en TCP ##
  
El Three-Way y Four-Way handshake son los mecanismos que TCP usa para establecer la conexión y el cierre entre cliente y servidor respectivamente.

<div> <br> </div>

El **Three-Way Handshake** realiza tres pasos para establecer la conexion entre el cliente y el servidor. Esto es así porque un proceso de dos pasos no seria tan fiable y podrian establecerse conexiones por error.
Los pasos son los siguientes:

  1) El cliente envía un segmento especial de TCP al servidor con el bit de control SYN en 1 y un número de secuencia inicial _X_.
  2) El servidor confirma la recepción respondiendo con otro segmento con los bits SYN y ACK en 1 ambos, con su propio número de secuencia inicial _Y_ y con un número de _ACK=X+1_.
  3) El cliente por ultimo confirma la recepcion del servidor enviando otro numero de _ACK=Y+1_.

  Luego de esto, la conexión ya está establecida entre ambos.  

<div> <br> </div>


El **Four-Way Handshake** realiza 4 pasos para terminar la conexión entre cliente y servidor, esto porque toda conexion TCP es full duplex, por lo que hay dos canales independientes (Cliente → Servidor y Servidor → Cliente) en la comunicación y ambos se deben cerrar independientemente.
Los pasos son los siguientes:

  1) El cliente solicita el cierre de comunicación enviando un segmento TCP con el bit de control FIN en 1, y con su número de secuencia actual _X_.
  2) El servidor recibe el segmento, responde enviando un segmento con el bit de control ack en 1 y el fin en 0 (ya que puede querer mantener la comunicación servidor → cliente para enviar mas datos). Además, envia el número de secuencia actual del servidor _Y_ y envia un número de ACK _X+1_.
    
     **A partir de este momento la comunicación Cliente → Servidor está cerrada**
     
  3) Cuando el servidor terminó de enviar todos los datos y está listo para cerrar la comunicación envia un segmento con el bit de control FIN en 1 y envía su número de secuencia actual Y y envia un número de ACK _X+1_.
  4) Por último, el cliente confirma la recepción enviando un segmento con el bit ACK en 1 y FIN en 0. Además, un número de secuencia _X+1_ y un número de ACK _Y+1_.
     
     **Con esto se concluye la comunicación entre ambos**


## D) Comunicación Cliente-Servidor con PacketSender y Sniffeamos con WireShark ##

Vamos a establecer una comunicación cliente-servidor a través de dos instancias de PacketSender y luego vamos a interceptarla a traves de WireShark.

<img width="1437" height="775" alt="3" src="https://github.com/user-attachments/assets/4efcafcf-869b-4923-8586-2eb53533e056" />
<div align="center"> <em> Configuramos PacketSender para actuar como cliente y servidor y enviamos un paquete de datos</em> </div>  

<div> <br> </div>


Luego de haber configurado correctamente cada instancia, enviamos el paquete de datos entre ellos con la carga util "_Hola_", mientras que en WireShark ya tenemos iniciada la escucha para poder capturar la comunicación.

<div> <br> </div>

<img width="1252" height="361" alt="4" src="https://github.com/user-attachments/assets/f056fb75-3edc-4415-9ed8-1e7e4b12b156" />
<div align="center"> <em> Vista de la captura de las comunicaciones a través de WireShark </em> </div>  
<div> <br> </div>

<img width="1250" height="378" alt="5" src="https://github.com/user-attachments/assets/f527de85-3e91-4456-bee8-17ac452529e3" />
<div align="center"> <em> Paquete de datos con la carga útil "Hola" </em> </div>
<div> <br> </div>

**Acá podemos observar claramente como actua el protocolo TCP**
  - Los 3 primeros paquetes (N° 249, 250 y 251) son los pasos del Three-Way Handshake para establecer la conexión.
  - El siguiente paquete (N° 252) es el paquete que originalmente queriamos enviar en la comunicacion, con su carga útil.
  - El paquete que le continúa (N° 253) es el que confirma la recepción del paquete anterior.
  - Los últimos 4 paquetes (N° 254, 255, 256 y 257) son los pasos del Four-Way Handshake para terminar la comunicación correctamente.

## F) Conclusiones Finales ##

Luego de observar la facilidad con la que un programa puede capturar e interceptar comunicaciones que supuestamente son privadas, nos hace darnos cuenta la falta de privacidad y seguridad que muchas veces no tenemos en cuenta.
Esto nos hace replantearnos lo importante de concientizarnos más en que nosotros mismos debemos ser mucho más responsables con nuestros dispositivos y uso de internet para no poner en riesgo nuestra privacidad y nuestros datos.
Además, de lo importante y necesario es que las comunicaciones sean lo más encriptadas posibles.
