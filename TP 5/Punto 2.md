a) El protocolo de resolución de direcciones (ARP, “Address Resolution Protocol”), nos proporciona un mecanismo para traducir las direcciones IP en direcciones de la capa de enlace. Por ejemplo, si un host con la dirección IP 222.222.222.220 desea enviar un datagrama IP al host 222.222.222.222. Para poder enviar un datagrama, el origen tiene que proporcionar a su adaptador no solo el datagrama IP sino que también la dirección MAC del destino 222.222.222.222. El adaptador del emisor construirá entonces una trama de la capa de enlace que contendrá la dirección MAC del destino y enviará la trama a la red LAN.   
   Nos preguntamos: ¿cómo determina el host emisor la dirección MAC del host de destino con la dirección IP 222.222.222.222?. Utiliza el protocolo ARP. Un módulo ARP en el host emisor toma como entrada cualquier dirección IP de la misma LAN y devuelve la dirección MAC correspondiente.  
   Por qué es discutible:  
* Argumento a favor de Capa 2: Se encapsula directamente dentro de una trama Ethernet (no lleva encabezado IP arriba) y sus mensajes contienen directamente direcciones físicas MAC.  
* Argumento a favor de Capa 3: Su única función es dar soporte al protocolo IP (Capa de Red) traduciendo direcciones IP, por lo que actúa como un protocolo auxiliar de red.

b) ARP Request (Consulta ARP): Consulta que hace el paquete ARP a todos los host y routers de la subred para determinar la dirección MAC correspondiente a la dirección IP con la que se quiere comunicar. La trama que contiene la consulta ARP es recibida por todos los demás adaptadores existentes en la subred y cada adaptador pasa la consulta ARP contenida en la trama a su módulo ARP. 

   ARP Reply (Respuesta ARP): Los módulos ARP realizan una comprobación para ver si su dirección IP se corresponde con la dirección IP de destino del paquete ARP. El único nodo en el que se produzca una coincidencia devolverá al nodo que ha realizado la consulta una respuesta ARP con la correspondencia deseada.  

c) La caché ARP es una tabla o memoria temporal IP → MAC que cada host guarda. Guarda la correspondencia entre direcciones IP (Capa 3) y sus respectivas direcciones MAC (Capa 2) aprendidas en la red local.
Existe para no preguntar antes de cada paquete, ósea, evita que el emisor tenga que enviar una consulta en broadcast a toda la red y también reduce la latencia, ya que permite que los dispositivos se comuniquen de forma instantánea sin perder tiempo en consultas repetitivas de red.

e) 

Terminal, tabla de cache ARP
<img width="530" height="125" alt="image7" src="https://github.com/user-attachments/assets/5b47fa5e-18ef-4181-9c01-b3dde2239a01" />

Sí, coincide. La caché ARP asocia 192.168.0.1 con c4-e9-84-7c-93-d6, y esa misma MAC es la MAC destino del Echo Request enviado al gateway (frame 3791).

f)

Realizamos un ping
<img width="783" height="221" alt="image39" src="https://github.com/user-attachments/assets/808a22e2-ddbd-42d7-bb95-a550eb0b32ea" />

Wireshark, capturamos ARP
<img width="821" height="35" alt="image22" src="https://github.com/user-attachments/assets/a3a709e0-3407-4fc4-bb7a-8c05b0fcd61b" />

Detalle del Request, destino broadcast
<img width="664" height="349" alt="image6" src="https://github.com/user-attachments/assets/a4bc6c22-abba-4e02-97b9-0a3cc35f3a9d" />

Detalle del Reply, respuesta unicast
<img width="664" height="348" alt="image13" src="https://github.com/user-attachments/assets/ea6d008c-1426-412b-bf97-cfd51c8cf73e" />

Echo Request al gateway, MAC destino es la del gateway
<img width="663" height="379" alt="image32" src="https://github.com/user-attachments/assets/2dac2cc0-6fef-4883-8322-57f5cb5d7503" />

Cache ARP final
<img width="503" height="168" alt="image15" src="https://github.com/user-attachments/assets/465f4430-a961-4048-9ce6-45b78352e55d" />



| Campo | ARP Request | ARP Reply |
| :---- | :---- | :---- |
| MAC destino (encabezado Ethernet) | ff:ff:ff:ff:ff:ff  | ec:2e:98:2d:5e:11  |
| MAC origen (encabezado Ethernet) | ec:2e:98:2d:5e:11 | c4:e9:84:7c:93:d6 |
| Opcode | request (1) | reply (2) |
| Sender MAC address  | ec:2e:98:2d:5e:11 | c4:e9:84:7c:93:d6 |
| Sender IP address | 192.168.0.101  | 192.168.0.1 |
| Target MAC address  | 00:00:00:00:00:00  | ec:2e:98:2d:5e:11 |
| Target IP address  | 192.168.0.1  | 192.168.0.101 |


a) El ARP Request va a la dirección de broadcast ff:ff:ff:ff:ff:ff porque el emisor (192.168.0.101) conoce la IP del equipo que busca (192.168.0.1) pero no su MAC. Como no sabe a quién enviarlo, lo manda a todos los equipos de la red local, y solo el dueño de esa IP responde. El Reply, en cambio, va por unicast directo a ec:2e:98:2d:5e:11, porque el Request ya incluía la MAC del solicitante en el campo Sender MAC, así que el que responde sabe a quién contestar.   
En el Request, Target MAC vale 00:00:00:00:00:00, porque es justamente el dato que se está preguntando: todavía no se conoce, así que se deja en ceros como marcador.  
     
b) El campo Type de Ethernet II vale 0x0806, que identifica al protocolo ARP. No hay encabezado IP: en el panel de Wireshark solo aparecen Frame, Ethernet II y Address Resolution Protocol. Esto indica que ARP "vive" pegado a la capa de enlace: viaja directamente dentro de la trama Ethernet, sin usar IP, por lo que solo funciona dentro de la red local. No puede cruzar un router, porque los routers trabajan con IP y no reenvían broadcasts.   
     
c) Aparecieron 6 ARP Request Who has 192.168.0.253? Tell 192.168.0.101, enviados aproximadamente uno por segundo. No hubo ningún Reply, porque no existe ningún equipo con esa IP. Tampoco apareció ningún ICMP Echo Request. Porque para enviarlo hay que armar una trama Ethernet con la MAC destino, y como nadie respondió el ARP, la MAC nunca se obtuvo. Sin MAC destino el paquete IP no se puede encapsular, así que el ping nunca llegó a salir de la computadora y fallo con "Host de destino inaccesible".  

d)
Terminal, dos ping, el segundo un minuto despues que el primero
<img width="491" height="380" alt="image12" src="https://github.com/user-attachments/assets/9b5995e5-c69c-4a5b-99fb-003967180d09" />

Captura con arp || icmp, el ARP inicial en segundo 4,38s y el segundo ping en el segundo 74,70s
<img width="1366" height="232" alt="image10" src="https://github.com/user-attachments/assets/0cdd2264-1c64-405c-b235-28fed59f27c8" />


Un minuto después de la primera resolución (ARP Reply en el segundo 4,39 de la captura) volví a hacer ping a 192.168.0.1, en el segundo 74,71 (unos 70 segundos después), y no apareció ningún ARP nuevo para resolver esa dirección: el sistema usó directamente la MAC guardada en la caché, ya que la entrada seguía en la caché (arp -a) con la MAC c4-e9-84-7c-93-d6.
La ventaja del caché es que evita preguntar por ARP antes de cada paquete, reduciendo el tráfico de broadcast y la demora de cada envío. Pero el problema es que si el equipo cambió de MAC o la IP pasó a otro equipo, la computadora seguiría enviando las tramas a la MAC anterior hasta que la entrada caduque.
