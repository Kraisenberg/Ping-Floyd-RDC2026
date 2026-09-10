# Informacion de una red local #

## A) ¿Qué función cumple la capa de enlace dentro del modelo OSI? ¿Qué tipo de comunicación resuelve? ##
La capa de enlace de datos proporciona servicios a la capa de red para ofrecer un tránsito de datos confiable a través del enlace físico.
Sus funciones principales incluyen el direccionamiento físico, el control de acceso al medio, la topología de red, la entrega ordenada de tramas, el control de flujo y la detección y control de errores.

Para ello, toma las unidades de datos de la capa de red y las encapsula en una trama (frame), añadiéndoles una cabecera y una cola de enlace antes de pasarlas a la capa física.
Resuelve la comunicación y transferencia de datos entre dispositivos directamente conectados dentro de la misma red local o enlace físico compartido.


## ¿Qué es una dirección MAC? ¿En qué se diferencia de una dirección IP? ##
La dirección MAC es la dirección física del dispositivo, grabada de fábrica en la tarjeta de interfaz de red. Es única e inalterable a nivel global y sirve para identificar dispositivos dentro de la red local; la capa de enlace de datos administra el direccionamiento físico (a través de la subcapa MAC) mientras que la capa de red se encarga del direccionamiento lógico (donde reside la direccion IP)

La dirección IP es una dirección de direccionamiento lógico que pertenece a la capa de red (Capa 3 del modelo OSI / Capa Internet de TCP/IP)
Mientras que la dirección MAC se utiliza para la entrega local trama a trama dentro del mismo segmento físico
la dirección IP se utiliza para el encaminamiento, selección de rutas y conectividad global entre dispositivos ubicados en redes geográficamente o lógicamente distintas.

A continuación, se muestra una dirección MAC de ejemplo y cómo está compuesta
<p align="center">
<img width="255" height="125" alt="image" src="https://github.com/user-attachments/assets/1edbe45d-55fe-4b01-adfd-0d3d5a1b41f2" />
</p>


## ¿Qué es una trama Ethernet? Identificar sus principales campos y explicar brevemente para qué sirve cada uno. ##
Una trama Ethernet es la unidad de datos de protocolo (PDU) de la capa de enlace de datos / acceso a red.
Encapsula el paquete de datos de la capa de red agregando control antes y después de la carga útil

Breve descripción de los campos principales :

  - **Cabecera de enlace**: Contiene la dirección física/subred de destino (para indicar qué dispositivo del medio debe recibir la trama) e información de control o solicitud de recursos.

  - **Campo de Datos / Carga Útil**: Almacena el paquete recibido de la capa superior (como un datagrama IP o segmento de red)

  - **Cola de enlace**: Contiene códigos de detección de errores (como comprobaciones de redundancia) para verificar que la trama no se haya distorsionado durante la transmisión


La siguiente imagen muestra lo antes explicado.
<p align="center">
<img width="320" height="120" alt="image" src="https://github.com/user-attachments/assets/63f3f6be-ef8a-4165-b5cf-b0dcd2870b1c"/>
</p>

## ¿Qué información permite determinar qué protocolo de capa superior está transportando una trama Ethernet? ##
Para que el receptor sepa a qué protocolo o punto de acceso al servicio (SAP) debe entregar los datos, al desencapsular la cabecera de la capa de enlace,  se encuentra un identificador o campo de control que indica qué tipo de PDU de la capa de red (como IP) está siendo transportado en el campo de datos.
