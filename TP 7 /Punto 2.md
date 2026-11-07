## Abran Wireshark en la interfaz Wi-Fi y capturen al menos 2 minutos. Pueden llegar varios mensajes; no tienen porqué ser todos idénticos.

A continuación, se muestran algunos paquetes capturados en Wireshark.
<img width="1163" height="106" alt="Captura de pantalla 2026-10-30 181155" src="https://github.com/user-attachments/assets/59c40907-b789-4b51-87b8-27563d5eb257" />

Para filtrar todos los paquetes mostrados por Wireshark que no eran importantes se utilizó el filto `frame contains "SIZE"`. Luego, a medida que se transmitian paquetes, los únicos que aparecerían son aquellos cuyo payload contenía la palabra `"SIZE"`. 

En dicha imagen se observa lo siguiente:
- Varios paquetes utilizando el protocolo UDP, el cual es ideal para mandar paquetes por medio de broadcast, ya que es un protocolo sin conexión.
- La IP del emisor (router) y su destino (broadcast).
- El tiempo entre paquetes que contienen la palabra `"SIZE"` es relativamente alto, por lo que si no se hubiera utilizado un filtro, sería muy difícil obtener un paquete. Pero eso no es todo, sino que también se tienen paquetes "basura", por lo que la dificultad de capturar el paquete verdadero aumenta mucho más. A los 100 segundos se pudo capturar el paquete verdadero.
- El tamaño (lenght) de cada paquete. Esto da una pista sobre cual sería el paquete verdadero.
- La cantidad de paquetes que se capturaron entre el primero que contenía `"SIZE"` y el verdadero fue de 654. Nuevamente, sin el filtro sería imposible realizar una inspección uno a uno de cada paquete que recibe la placa de red.
