# Entramos en Wireshark y empezamos a capturar el trafico #  

<div align="center"> <img width="1439" height="631" alt="11" src="https://github.com/user-attachments/assets/6f1f23e3-656e-43e7-8344-56218d002b88" /> </div>
<div align="center"> <em> Seleccionamos un paquete al azar </em> </div>  
<div> <br> </div>
<div align="center"> <img width="555" height="84" alt="2" src="https://github.com/user-attachments/assets/5217516b-451c-4672-a63e-591cda4b7c82" /> </div>
<div align="center"> <em> Observamos el paquete de datos </em> </div>  
<div> <br> </div>

## A) Seleccionar una trama Ethernet e identificar las direcciones MAC de origen y destino. ¿A qué dispositivos creen que corresponden? ##  
Observando la trama y localizando la OUI de ambas direcciones MAC podemos saber los fabricantes y por lo tanto inferir sus dispositivos correspondientes.

La MAC de origen es **B4:2E:99:F9:82:89**, su OUI es **B4:2E:99** y pertenece a Gigabyte, por lo tanto, el origen es la placa de red interna de la PC.

La MAC  de destino es **58:2F:F7:0C:58:F3**, su OUI es **58:2F:F7** y pertenece a Sagemcom, por lo tanto el destino es el router/modem de la empresa de internet.  

<div> <br> </div>

## B) Dentro de la misma trama, identificar el paquete IP. ¿Cuáles son las direcciones IP de origen y destino? (no importa si son versión 4 o versión 6) ##  

Seguimos observando la trama e identificamos el paquete IP

La IP de origen es **192.168.0.129**

La IP de destino es **157.90.91.74**

<div> <br> </div>

## C) Comparar las direcciones MAC y las direcciones IP encontradas. ¿Representan lo mismo? ##  

No, direcciones IP y direcciones MAC no representan lo mismo.

Las direcciones MAC representan los dispositivos que se envian el paquete de datos dentro de la red LAN, mientras que las direcciones IP, una marca el dispositivo dentro de mi red donde se origino y la otra marca el destino final dentro de internet del paquete.

<div> <br> </div>

## D) Observar el campo EtherType. ¿Qué protocolo está encapsulado dentro de la trama analizada? ##  

Observando el EtherType vemos que el protoco encapsulado es el **TCP** (Identificado con un 06)
