1) La capa de enlace de datos proporciona servicios a la capa de red para ofrecer un tránsito de datos confiable a través del enlace físico
Sus funciones principales incluyen el direccionamiento físico, el control de acceso al medio, la topología de red, la entrega ordenada de tramas, el control de flujo y la detección y control de errores.
Para ello, toma las unidades de datos de la capa de red y las encapsula en una trama (frame), añadiéndoles una cabecera y una cola de enlace antes de pasarlas a la capa física.
Resuelve la comunicación y transferencia de datos entre dispositivos directamente conectados dentro de la misma red local o enlace físico compartido.

2) La dirección MAC es la dirección física del dispositivo, grabada de fábrica en la tarjeta de interfaz de red. Es única e inalterable a nivel global y sirve para identificar dispositivos dentro de la red local; la capa de enlace de datos administra el direccionamiento físico (a través de la subcapa MAC)
mientras que la capa de red se encarga del direccionamiento lógico (donde reside la direccion IP )
La dirección IP es una dirección de direccionamiento lógico que pertenece a la capa de red (Capa 3 del modelo OSI / Capa Internet de TCP/IP)
Mientras que la dirección MAC se utiliza para la entrega local trama a trama dentro del mismo segmento físico
la dirección IP se utiliza para el encaminamiento, selección de rutas y conectividad global entre dispositivos ubicados en redes geográficamente o lógicamente distintas

3) Una trama Ethernet es la unidad de datos de protocolo (PDU) de la capa de enlace de datos / acceso a red.
Encapsula el paquete de datos de la capa de red agregando control antes y después de la carga útil

Breve descripción de los campos principales :

Cabecera de enlace : Contiene la dirección física/subred de destino (para indicar qué dispositivo del medio debe recibir la trama) e información de control o solicitud de recursos.

Campo de Datos / Carga Útil: Almacena el paquete recibido de la capa superior (como un datagrama IP o segmento de red)

Cola de enlace : Contiene códigos de detección de errores (como comprobaciones de redundancia) para verificar que la trama no se haya distorsionado durante la transmisión

4) Para que el receptor sepa a qué protocolo o punto de acceso al servicio (SAP) debe entregar los datos al desencapsular, la cabecera de la capa de enlace incluye un identificador o campo de control que indica qué tipo de PDU de la capa de red (como IP) está siendo transportado en el campo de datos.
