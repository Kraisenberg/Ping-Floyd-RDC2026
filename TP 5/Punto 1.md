1a-. Internet Control Message Protocol básicamente es un protocolo de capa de red, está diseñado para control, diagnóstico de errores entre un router o varios y un host o varios. No transporta datos de aplicaciones y tampoco interactúa con aplicaciones de usuario ni usa puertos.  

1b-. La relación que tiene IP con ICMP es que IP contiene a ICMP, ICMP es un protocolo que viaja encapsulado o adentro de IP. 
Se da cuenta el receptor que el contenido es ICMP porque la cabecera IP tiene un "Protocol" y ese campo le indica a la computadora el contenido de un paquete. En este caso específico sería si el valor del campo vale 1.

1c-. La herramienta 'ping' lo que hace es comprobar si el equipo puede conectarse con otro a través de una red IP.
Lo que hace Echo Request es enviar un mensaje en el que solicito una respuesta, Echo Reply es el mensaje que devuelve el destinatario si procesó correctamente la solicitud.
Los campos que utiliza ICMP para distinguir los mensajes son 'type' y 'code'. Por ejemplo la computadora recibe un paquete dirigido a su IP, entonces mira su campo 'protocol' le llegó 1; entonces identifica que es ICMP.
Luego ICMP mira su campo 'type' y 'code' y en base a eso sabe si es un 'echo request' (type 8 code 0) o un 'echo reply' (type 0 code 0 )

1d-. La información que contiene mínima es un encabezado ICMP de 8 bytes y un campo de datos.

