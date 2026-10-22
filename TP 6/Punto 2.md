Para este punto, necesitamos usar dos computadoras, a las cuales se les modifico lo siguiente:

Dirección IPv4

	La computadora 1 se la configuro con la dirección: 192.168.100.2
	La computadora 2 se la configuro con la dirección: 192.168.100.1

Máscara de Subred 

	Ambas computadoras se configuraron con la mascara: 255.255.255.0

Default Gateway
		
	En ambas computadoras, no hizo falta configurarlo debido a que no tenemos salida a internet

La elección tuvo sentido para la actividad ya que cuando configuramos ambas computadoras en la misma red hizo que puedan comunicarse a través del switch, utilizando mensajes HTTP y UDP sin necesidad de un router que tenga que estar enrutando tráfico entre las distintas redes. El default gateway no fue relevante en este trabajo práctico porque el tráfico que se generaba era de manera local.



Desde la computadora 2, enviamos un mensaje al receptor:

<img width="844" height="128" alt="Screenshot From 2026-10-15 20-40-41" src="https://github.com/user-attachments/assets/0f93486e-fd6b-46b1-8041-e23260d0ceff" />

