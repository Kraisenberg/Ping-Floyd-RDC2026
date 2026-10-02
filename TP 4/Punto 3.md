<!--<div align="center"> </div>-->
<!--<div> <br> </div>-->
<!--<div align="center"> <em> Comandos enviados para la configuracion del Switch 2 </em> </div>  -->
<!-- Titulo -->
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
<div align="center"><img width="1071" height="665" alt="Server entretenimiento turista" src="https://github.com/user-attachments/assets/b3c9b0e9-4a41-464c-8b9b-caeda9750993" /></div>
<div align="center"> <em> Ingreso HTTP al servidor </em> </div>
<div> <br> </div>
<!-- Foto numero 5 -->

Como se observa, desde la clase **Turista** se puede acceder correctamente al servidor de entretenimiento local pero no tiene acceso a internet

<div> <br> </div>


### Clase Business ###

<div> <br> </div>
Ping a internet desde clase business
<img width="435" height="295" alt="ping business " src="https://github.com/user-attachments/assets/d398235f-6d04-46ef-9bc6-3189daf855d9" />
<div> <br> </div>
conexion con server entretenimiento desde clase business
<img width="662" height="341" alt="Server entretenimiento Business" src="https://github.com/user-attachments/assets/fcf209d3-97ff-4d64-abe6-d6ceec7c1b89" />

<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
ping desde clase turista a servidor local y a internet



<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>

<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>

<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
Ping a todos desde admin
<img width="464" height="997" alt="Ping admin" src="https://github.com/user-attachments/assets/c52a251f-c5ce-4e78-b2fc-9dbcfca93bec" />
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
Conexion a servidor de entretenimiento desde clase turista

<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>

<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
<div> <br> </div>
esta en stand by
<img width="422" height="212" alt="Ping clase turista servidor" src="https://github.com/user-attachments/assets/a51a7429-abab-4438-a195-394e0c1515b0" />

<div> <br> </div>



