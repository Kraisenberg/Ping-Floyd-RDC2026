# Alcance de Redes y Virtualización #

## a) Investigar cómo se clasifican las redes según su alcance. Mencionar brevemente las características principales de cada una y colocar en cada cuadro de la Figura el acrónimo de red que corresponda. ##

### Las redes se clasifican según su alcance o área geográfica:  
 
**PAN (Personal Area Network):** <br>
Red de área/cobertura personal (pocos metros)  que conecta dispositivos cercanos como teléfonos, auriculares o computadoras. Su alcance suele ser de 10 m.   
**LAN (Local Area Network):** <br> 
Red de alcance local que interconecta o cubre equipos en un área reducida, como una oficina, casa o un aula de clases. Ofrece altas velocidades de transmisión y baja latencia.   
**CAN (Campus Area Network ):** <br> 
Interconecta múltiples redes LAN dentro de un área geográfica delimitada como un campus universitario o complejo corporativo.  
**MAN (Metropolitan Área Network):** <br> 
Red de alta velocidad que da cobertura a una zona metropolitana, interconectando diversas redes LAN. Utilizada por proveedores de servicios o gobiernos locales para interconectar sedes urbanas.   
**WAN (Wide Area Network):** <br> 
Interconecta redes a gran escala geográfica mediante el uso de enlaces satelitales, cables submarinos o fibra óptica de larga distancia. El ejemplo más claro de una red WAN es el Internet.  

## b) ¿Qué es una vLAN? ¿Cómo se clasifican? ##

### Una VLAN (Virtual Local Area Network) 
O red de área local virtual, es una tecnología de red que nos permite crear redes lógicas independientes dentro de la misma red física, osea, es como dividir nuestra red en redes más pequeñas, “fingimos” mediante software y firmware que existen más de una red local dentro de un mismo SW. Permite agrupar dispositivos de forma lógica sin importar su ubicación física, mejorando la seguridad, el rendimiento y la administración del tráfico.  

### Se clasifican principalmente en:  
**VLAN basada en puertos (Port-based / Estática):** <br> 
Los puertos del switch se asignan manualmente a una VLAN específica. Es el más común y sencillo.  
**VLAN basada en direcciones MAC (Dinámica):** <br>
La pertenencia a la VLAN se determina según la dirección MAC del dispositivo conectado.  
**VLANs basadas en protocolo o subred IP (Capa 3 / Nivel de red):** <br>
La trama se asigna a una VLAN según el tipo de protocolo de capa superior (por ejemplo, IPv4 o IPv6) o la subred IP a la que pertenece el paquete.  
**VLAN Nativa:** <br>
VLAN asignada a un enlace troncal 802.1Q para transportar el tráfico que no lleva etiqueta.
**VLAN de Datos:** <br>
Creada para transportar únicamente tráfico generado por los usuarios.

## c) Investigar y resumir el protocolo IEEE 802.1Q. ¿Cómo se relaciona con las VLAN?

### **El protocolo IEEE 802.1Q:** 
También conocido como dot1Q, fue un proyecto del grupo de trabajo 802 de la IEEE para desarrollar un mecanismo que permita a múltiples redes compartir de forma transparente el mismo medio físico, sin problemas de interferencia entre ellas (Trunking). Es también el nombre actual del estándar establecido en este proyecto y se usa para definir el protocolo de encapsulamiento usado para implementar este mecanismo en redes Ethernet. Todos los dispositivos de interconexión que soportan VLAN deben seguir la norma IEEE 802.1Q que especifica con detalle el funcionamiento y administración de redes virtuales.

### **Relación entre 802.1Q y las VLAN**
Una VLAN segmenta una red física conmutada en múltiples dominios de broadcast lógicos. Dentro de un solo switch, el equipo sabe a qué VLAN pertenece cada puerto mediante su tabla interna.
Sin embargo, cuando el tráfico debe atravesar un enlace que conecta dos switches (o un switch y un router), se utiliza un enlace troncal (trunk). Aquí es donde entra 802.1Q: introduce un mecanismo de etiquetado de tramas (frame tagging) para que ambos extremos sepan a qué VLAN pertenece cada trama que cruza el cable compartido.

## d) **¿Qué es el Tagging?**

### El Taggin (o etiquetado de tramas) 
es el proceso mediante el cual un switch o dispositivo de red inserta metadatos dentro de la cabecera de una trama Ethernet para identificar explícitamente a qué VLAN pertenece ese paquete mientras viaja por un enlace compartido. 

### ¿Por qué existe el tagging?
Dentro de un switch convencional, los puertos finales suelen ser puertos de acceso: Una PC o servidor no sabe ni necesita saber qué es una VLAN. Envía tramas Ethernet estándar (sin etiqueta, o untagged). El switch sabe a qué VLAN pertenece esa PC porque el administrador configuró el puerto físico (por ejemplo, Puerto 3 = VLAN 10). Mientras la trama circula por la memoria interna del switch, este la mantiene aislada en la VLAN 10. El problema surge cuando esa trama tiene que viajar hacia otro switch o router a través de un único cable físico (enlace troncal o trunk): Si el Switch A simplemente envía la trama normal por el cable, el Switch B no tendría forma de saber si ese paquete pertenece a la VLAN 10 (Ventas), VLAN 20 (Ingeniería) o VLAN 30 (Servidores).

