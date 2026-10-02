<!-- Titulo -->
# Implementacion de Topologia en Packet-Tracer # 
<!-- Titulo -->

Lo primero que realizamos fue la topología solicitada en el trabajo practico en el software Packet-Tracer mediante los dispositivos ofrecidos en el mismo y con sus correspondientes conexiones.

<!-- FOTO NUMERO 1 -->
<div align="center"> <img width="1439" height="852" alt="Estructura" src="https://github.com/user-attachments/assets/ec85c357-22dd-41e9-937b-cc3debe7c2c9" /> </div>  
<div> <br> </div>
<!-- FOTO NUMERO 1 -->

Luego de esto, a través de la conexión de consola entre cada PC y su switch correspondiente realizamos la configuración de los mismos, cambiando su nombre y añadiendo contraseñas de acceso.


<!-- FOTO NUMERO 2 -->
<div> <br> </div>
<div align="center"> <img width="488" height="248" alt="config 2" src="https://github.com/user-attachments/assets/5b79ffa5-d8f6-44de-8886-de88b8ab98d8" /> </div>  
<div align="center"> <em> Comandos enviados para la configuracion del Switch 2 </em> </div>  
<div> <br> </div>
<!-- FOTO NUMERO 2 -->

Una vez hecho esto, seguimos con la configuración de las redes VLAN de los switches con las especificaciones que están en la tabla.

Luego observamos cuales son las interfaces que existen y están habilitadas, para luego desconectarlas y dejar únicamente activas las interfaces utilizadas en nuestro esquema.


<!-- FOTO NUMERO 3 -->
<div> <br> </div>
<div align="center"><img width="591" height="375" alt="Fastethernet antes" src="https://github.com/user-attachments/assets/27f30314-fbb7-4f36-971d-8dcfe8898362" /></div>
<div align="center"> <em> Estado de las interfaces de modo predeterminado  </em> </div>
<div> <br> </div>
<div align="center"><img width="586" height="417" alt="Fastethernet despues" src="https://github.com/user-attachments/assets/14ce3045-4c41-424d-b8e1-45a6aa9f9ae1" /></div> 
<div align="center"> <em> Interfaces luego de desconectarlas </em> </div>  
<div> <br> </div>
<!-- FOTO NUMERO 3 -->

Al terminar todas las configuraciones testeamos la conexión entre las computadoras a través de pings para verificar que estén correctamente comunicadas.


<!-- FOTO NUMERO 4 -->
<div> <br> </div>
<div align="center"><img width="466" height="266" alt="Ping" src="https://github.com/user-attachments/assets/176472e7-541b-4a24-a8cd-900571955541" /></div> 
<div align="center"> <em> Paquetes recibidos correctamente </em> </div>  
<div> <br> </div>
<!-- FOTO NUMERO 4 -->

Ahora nos centramos en la creacion de las VLANs en los switches mediante la consola

<!-- FOTO NUMERO 5 -->
<div> <br> </div>
<div align="center"><img width="481" height="210" alt="Conf vlan" src="https://github.com/user-attachments/assets/6f88b4a7-3d1c-4721-829e-dbcdfffb162e" /></div>
<div> <br> </div>
<!-- FOTO NUMERO 5 -->



<!-- FOTO NUMERO 6 -->
<div> <br> </div>
<div align="center"><img width="615" height="254" alt="Vlan" src="https://github.com/user-attachments/assets/f7603ea5-d4c5-4a02-99c8-11cb26abbcf8" /></div>
<div> <br> </div>
<!-- FOTO NUMERO 6 -->



<!-- FOTO NUMERO 7 -->
<div> <br> </div>
<div align="center"><img width="672" height="644" alt="Nueva configuracion de vlan" src="https://github.com/user-attachments/assets/3c9abd71-631a-490e-a715-ef933f9fb214" /></div>
<div align="center"> <em> Configuracion final Switch 1 </em> </div>  
<div> <br> </div>
<!-- FOTO NUMERO 7 -->



<!-- FOTO NUMERO 8 -->
<div> <br> </div>
<div align="center"><img width="602" height="652" alt="Nueva configuracion de vlan 2" src="https://github.com/user-attachments/assets/c92f3ffa-0eb7-4787-9bfc-85f67a38a05a" /></div>
<div align="center"> <em> Configuracion final Switch 2 </em> </div>  
<div> <br> </div>
<!-- FOTO NUMERO 8 -->



<!-- FOTO NUMERO 9 -->
<div> <br> </div>
<div align="center"><img width="509" height="269" alt="nuevo ping" src="https://github.com/user-attachments/assets/2e3f70d3-72ca-42da-b2dd-7635d856c9e7" /></div>
<div align="center"> <em> Intento de comunicación entre ambas computadoras </em> </div>  
<div> <br> </div>
<!-- FOTO NUMERO 9 -->
