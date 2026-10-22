a) El protocolo de resolución de direcciones (ARP, “Address Resolution Protocol”), nos proporciona un mecanismo para traducir las direcciones IP en direcciones de la capa de enlace. Por ejemplo, si un host con la dirección IP 222.222.222.220 desea enviar un datagrama IP al host 222.222.222.222. Para poder enviar un datagrama, el origen tiene que proporcionar a su adaptador no solo el datagrama IP sino que también la dirección MAC del destino 222.222.222.222. El adaptador del emisor construirá entonces una trama de la capa de enlace que contendrá la dirección MAC del destino y enviará la trama a la red LAN.   
   Nos preguntamos: ¿cómo determina el host emisor la dirección MAC del host de destino con la dirección IP 222.222.222.222?. Utiliza el protocolo ARP. Un módulo ARP en el host emisor toma como entrada cualquier dirección IP de la misma LAN y devuelve la dirección MAC correspondiente.  
   Por qué es discutible:  
* Argumento a favor de Capa 2: Se encapsula directamente dentro de una trama Ethernet (no lleva encabezado IP arriba) y sus mensajes contienen directamente direcciones físicas MAC.  
* Argumento a favor de Capa 3: Su única función es dar soporte al protocolo IP (Capa de Red) traduciendo direcciones IP, por lo que actúa como un protocolo auxiliar de red.

b) ARP Request (Consulta ARP): Consulta que hace el paquete ARP a todos los host y routers de la subred para determinar la dirección MAC correspondiente a la dirección IP con la que se quiere comunicar. La trama que contiene la consulta ARP es recibida por todos los demás adaptadores existentes en la subred y cada adaptador pasa la consulta ARP contenida en la trama a su módulo ARP. 

   ARP Reply (Respuesta ARP): Los módulos ARP realizan una comprobación para ver si su dirección IP se corresponde con la dirección IP de destino del paquete ARP. El único nodo en el que se produzca una coincidencia devolverá al nodo que ha realizado la consulta una respuesta ARP con la correspondencia deseada.  


e) <img width="530" height="125" alt="image7" src="https://github.com/user-attachments/assets/5b47fa5e-18ef-4181-9c01-b3dde2239a01" />

f) <img width="783" height="221" alt="image39" src="https://github.com/user-attachments/assets/808a22e2-ddbd-42d7-bb95-a550eb0b32ea" />

<img width="821" height="35" alt="image22" src="https://github.com/user-attachments/assets/a3a709e0-3407-4fc4-bb7a-8c05b0fcd61b" />

<img width="664" height="349" alt="image6" src="https://github.com/user-attachments/assets/a4bc6c22-abba-4e02-97b9-0a3cc35f3a9d" />

<img width="664" height="348" alt="image13" src="https://github.com/user-attachments/assets/ea6d008c-1426-412b-bf97-cfd51c8cf73e" />

<img width="663" height="379" alt="image32" src="https://github.com/user-attachments/assets/2dac2cc0-6fef-4883-8322-57f5cb5d7503" />

<img width="503" height="168" alt="image15" src="https://github.com/user-attachments/assets/465f4430-a961-4048-9ce6-45b78352e55d" />


| Campo | ARP Request | ARP Reply |
| :---- | :---- | :---- |
| MAC destino (encabezado Ethernet) | ff:ff:ff:ff:ff:ff  | ec:2e:98:2d:5e:11  |
| MAC origen (encabezado Ethernet) | ec:2e:98:2d:5e:11 | c4:e9:84:7c:93:d6 |
| Opcode | request (1) | reply (2) |
| Sender MAC address  | ec:2e:98:2d:5e:11 | c4:e9:84:7c:93:d6 |
| Sender IP address | 192.168.0.101  | 192:168.0.1 |
| Target MAC address  | 00:00:00:00:00:00  | ec:2e:98:2d:5e:11 |
| Target IP address  | 192.168.0.1  | 192:168.0.101 |

