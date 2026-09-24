# Alcance de Redes y Virtualización #

## Investigar cómo se clasifican las redes según su alcance. Mencionar brevemente las características principales de cada una y colocar en cada cuadro de la Figura el acrónimo de red que corresponda. ##

Las redes se clasifican según su alcance o área geográfica:  
 
PAN(Personal Area Network): Red de área/cobertura personal (pocos metros)  que conecta dispositivos cercanos como teléfonos, auriculares o computadoras. Su alcance suele ser de 10 m. 
LAN(Local Area Network): Red de alcance local que interconecta o cubre equipos en un área reducida, como una oficina, casa o un aula de clases. Ofrece altas velocidades de transmisión y baja latencia. 
CAN (Campus Area Network ): Interconecta múltiples redes LAN dentro de un área geográfica delimitada como un campus universitario o complejo corporativo.  
MAN(Metropolitan Área Network): Red de alta velocidad que da cobertura a una zona metropolitana, interconectando diversas redes LAN. Utilizada por proveedores de servicios o gobiernos locales para interconectar sedes urbanas.   
WAN(Wide Area Network): Interconecta redes a gran escala geográfica mediante el uso de enlaces satelitales, cables submarinos o fibra óptica de larga distancia. El ejemplo más claro de una red WAN es el Internet.  


## ¿Qué es una vLAN? ¿Cómo se clasifican? ##

Una VLAN (Virtual Local Area Network) o red de área local virtual, es una tecnología de red que nos permite crear redes lógicas independientes dentro de la misma red física, osea, es como dividir nuestra red en redes más pequeñas, “fingimos” mediante software y firmware que existen más de una red local dentro de un mismo SW. Permite agrupar dispositivos de forma lógica sin importar su ubicación física, mejorando la seguridad, el rendimiento y la administración del tráfico.  

Se clasifican principalmente en:  
VLAN basada en puertos (Port-based / Estática): Los puertos del switch se asignan manualmente a una VLAN específica. Es el más común y sencillo.  
VLAN basada en direcciones MAC (Dinámica): La pertenencia a la VLAN se determina según la dirección MAC del dispositivo conectado.  
VLANs basadas en protocolo o subred IP (Capa 3 / Nivel de red): La trama se asigna a una VLAN según el tipo de protocolo de capa superior (por ejemplo, IPv4 o IPv6) o la subred IP a la que pertenece el paquete.  
VLAN Nativa: VLAN asignada a un enlace troncal 802.1Q para transportar el tráfico que no lleva etiqueta.
VLAN de Datos: Creada para transportar únicamente tráfico generado por los usuarios.
