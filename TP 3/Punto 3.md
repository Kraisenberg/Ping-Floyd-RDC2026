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
  
El Three-Way y Four-Way handshake son los mecanismos que TCP usa para establecer la conexion y el cierre entre cliente y servidor respectivamente.

El **Three-Way Handshake** realiza tres pasos para establecer la conexion entre el cliente y el servidor. Esto es asi porque un proceso de dos pasos no seria tan fiable y podrian establecerse conexiones por error.
Los pasos son los siguientes:

  1) El cliente envia un segmento especial de TCP al servidor con el bit de control SYN en 1 y un numero de secuencia inicial X
  2) El servidor confirma la recepcion respondindo con otro segmento con los bits SYN y ACK en 1 ambos, con su propio numero de secuencia inicial Y y con un numero de ACK=X+1
  3) El cliente por ultimo confirma la recepcion del servidor enviando otro numero de ACK=Y+1

  Luego de esto, la conexion ya esta establecida entre ambos.  

<div> <br> </div>


El **Four-Way Handshake** realiza 4 pasos para terminar la conexion entre cliente y servidor, esto porque toda conexion TCP es full duplex, por lo que hay dos canales independientes (Cliente → Servidor y Servidor → Cliente) en la comunicacion y ambos se deben cerrar independientemente.
Los pasos son los siguientes:

  1) El cliente solicita el cierre de comunicacion enviando un segmento TCP con el bit de control FIN en 1, y con su numero de secuencia actual X.
  2) El servidor recibe el segmento, responde enviando un segmento con el bit de control ack en 1 y el fin en 0 (ya que puede querer mantener la comunicacion servidor → cliente para enviar mas datos). Ademas envia el numero de secuencia actual del servidor Y y envia un numero de ACK X+1.
    
     **A partir de este momento la comunicacion Cliente → Servidor esta cerrada**
     
  3) Cuando el servidor termino de enviar todos los datos y esta listo para cerrar la comunicacion envia un segmento con el bit de control FIN en 1 y envia su numero de secuencia actual Y y envia un numero de ACK X+1.
  4) Por ultimo, el cliente confirma la recepcion enviando un segmento con el bit ACK en 1 y FIN en 0. Ademas un numero de secuencia X+1 y un numero de ACK Y+1.
     
     **Con esto se concluye la comunicacion entre ambos**
