# Implementacion de red LAN en aeronave #

Para empezar a implementar la red LAN, armamos un esquema de red tal como nos sugiere el informe en Packet-Tracer
<!-- Foto numero 1 -->
<div> <br> </div>
<div align="center"><img width="852" height="465" alt="Captura de pantalla 2026-09-16 223226" src="https://github.com/user-attachments/assets/687d4d8e-2b41-420f-ba34-b556e61b4b38" /> </div>
<div> <br> </div>
<!-- Foto numero 1 -->

Luego de realizar todo el esquema físico de nuestra red con sus conexiones correspondientes, empezamos a realizar las distintas configuraciones indicadas.
  * Configuramos las distintas interfaces conectadas al switch y sus distintas VLAN
  * Configuramos el router del Avion y el router simulando el ISP para la conexion a internet con sus diferentes permisos y bloqueos para las distintas IPs
  * Configuramos el servidor de entretenimiento para simular correctamente su conexion a traves de las distintas computadoras

  Al finalizar todas las configuraciones, nos cercioramos de que cumplan las condiciones de la siguiente tabla:

<!-- Foto numero 2 -->
<div align="center"> <img width="711" height="193" alt="image" src="https://github.com/user-attachments/assets/97bcddc1-a89f-4f7c-812d-e99858bfa565" /></div>
<div> <br> </div>
<!-- Foto numero 2 -->

  Teniendo todo listo, empezamos a realizar los siguientes testeos como indica la siguiente tabla para verificar que todo este configurado correctamente:
  
<!-- Foto numero 3 -->
<div> <br> </div>
<div align="center"><img width="709" height="367" alt="image" src="https://github.com/user-attachments/assets/4ad561aa-774f-4b64-bebc-c0ab1585428f" /></div>
<div> <br> </div>
<!-- Foto numero 3 -->

## Empezamos con los testeos desde las distintas clases ##

### Clase Turista ###

Ping desde clase Turista al servidor de entretenimiento local (**10.10.99.10**) y al router del ISP (**200.0.0.2**)
<!-- Foto numero 4 -->
<div> <br> </div>
<div align="center"><img width="530" height="451" alt="Ping turista" src="https://github.com/user-attachments/assets/2a2dcfea-a3fd-49c2-8853-7c0a9e68f746" /></div>
<div align="center"> <em> Ping a servidor y a internet </em> </div>
<div> <br> </div>
<!-- Foto numero 4 -->

<!-- Foto numero 5 -->
<div> <br> </div>
<div align="center"><img width="918" height="570" alt="Server entretenimiento turista" src="https://github.com/user-attachments/assets/b3c9b0e9-4a41-464c-8b9b-caeda9750993" /></div>
<div align="center"> <em> Ingreso HTTP al servidor </em> </div>
<div> <br> </div>
<!-- Foto numero 5 -->

Como se observa, desde la clase **Turista** se puede acceder correctamente al servidor de entretenimiento local pero no tiene acceso a internet

<div> <br> </div>
<div> <br> </div>


### Clase Business ###

Ping desde clase Business al router del ISP **200.0.0.2** y acceso HTTPS al servidor
<div> <br> </div>
<div align="center"><img width="435" height="295" alt="ping business " src="https://github.com/user-attachments/assets/d398235f-6d04-46ef-9bc6-3189daf855d9" /></div>
<div align="center"> <em> Ping a internet </em> </div>
<div> <br> </div>
<div align="center"><img width="662" height="341" alt="Server entretenimiento Business" src="https://github.com/user-attachments/assets/fcf209d3-97ff-4d64-abe6-d6ceec7c1b89" /></div>
<div align="center"> <em> Ingreso HTTP al servidor </em> </div>
<div> <br> </div>

Como se observa, desde la clase **Business** se puede acceder correctamente al servidor de entretenimiento local y tambien tiene acceso a internet


<div> <br> </div>
<div> <br> </div>

### Clase Admin ###

Pings realizados desde la clase Admin hacia todos los puntos importantes de la estructura para verificar que se tiene acceso absoluto

<div> <br> </div>
<div align="center"><img width="464" height="997" alt="Ping admin" src="https://github.com/user-attachments/assets/c52a251f-c5ce-4e78-b2fc-9dbcfca93bec" /></div>
<div align="center"> <em> Todos los pings realizados desde Admin </em> </div>
<div> <br> </div>

Como se puede observar en la imagen, todos los pings dentro de la estructura del avion se realizaron correctamente por lo que se verifica que desde Admin podemos tener acceso a todos los dispositivos de la estructura, sin embargo el ping hacia internet falla ya que la configuracion del router del avion solo admite las IPs de la clase business.


