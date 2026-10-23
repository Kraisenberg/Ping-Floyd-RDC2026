Para este punto, necesitamos usar dos computadoras, a las cuales se les modifico lo siguiente:

1. Dirección IPv4

	La computadora 1 se la configuro con la dirección: 192.168.100.2
	La computadora 2 se la configuro con la dirección: 192.168.100.1

2. Máscara de Subred 

	Ambas computadoras se configuraron con la mascara: 255.255.255.0

3. Default Gateway
		
	En ambas computadoras, no hizo falta configurarlo debido a que no tenemos salida a internet

La elección tuvo sentido para la actividad ya que cuando configuramos ambas computadoras en la misma red hizo que puedan comunicarse a través del switch, utilizando mensajes HTTP y UDP sin necesidad de un router que tenga que estar enrutando tráfico entre las distintas redes. El default gateway no fue relevante en este trabajo práctico porque el tráfico que se generaba era de manera local.

Luego, utilizando “ncat”, establecemos un receptor UDP desde la computadora 1:

<img width="562" height="173" alt="image4" src="https://github.com/user-attachments/assets/146bd2b9-405c-407b-b3f4-3d19ce10aec8" />


Desde la computadora 2, enviamos un mensaje al receptor:

<img width="844" height="128" alt="Screenshot From 2026-10-15 20-40-41" src="https://github.com/user-attachments/assets/0f93486e-fd6b-46b1-8041-e23260d0ceff" />

Finalmente, capturamos los siguientes paquetes:

<img width="1600" height="900" alt="image5" src="https://github.com/user-attachments/assets/258db9e8-d02e-4e3b-bc4c-57f26d65451c" />


5) ¿Se observa algún procedimiento de establecimiento de conexión antes de enviar los datos?
No se observa ningún tipo de procedimiento para establecer conexión antes de enviar datos. En este protocolo, el emisor envía los paquetes de datos directamente, sin antes establecer un handshake.	

¿Existe algún mecanismo de confirmación de recepción equivalente a los ACK de TCP?
El protocolo UDP no tiene un mecanismo de confirmación de recepción equivalente a los ACK de TCP.
Esto se debe a que el protocolo está diseñado para ser simple y rápido, sacrificando la confiabilidad en la transmisión, por lo que no tiene confirmación de recepción.

¿Qué ocurre si se envían mensajes mientras el receptor UDP no está ejecutándose?
Los mensajes se pierden sin que el emisor se entere de forma directa, lo que sucedería es que los datagrama llegan al host destino, pero como no hay ningún proceso escuchando en ese puerto UPD se descarta los datagramas, acto seguido el receptor  responde con un mensaje ICMP “Destination Unreachable - Port Unreachable”

¿UDP garantiza que los mensajes lleguen en el mismo orden en que fueron enviados?
UDP no garantiza que los paquetes lleguen en orden, ya que en su cabecera no se incluye un número de secuencia que indique el orden en que deben ser reconstruidos los paquetes recibidos. Si una aplicación requiere los paquetes ordenados y aún así utilizar UDP, el ordenamiento y el chequeo de errores deben ser realizados en la capa de aplicación.

¿Qué aplicaciones reales utilizan UDP y por qué?
UDP tiene sus aplicaciones reales en el uso de videollamadas o llamadas, streaming, juegos online, DNS y QUIC/HTTP entre otras opciones. esto porque UDP se utiliza cuando la velocidad y la baja latencia importan más que la fiabilidad o cuando la aplicación prefiere manejar ella misma los errores. 
