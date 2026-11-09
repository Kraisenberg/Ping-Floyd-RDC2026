
# Desafío / Consigna

## 1) Averigüen su IP y su máscara (ipconfig / ip addr) y calculen la dirección de broadcast de la red. ¿Cuál es la dirección MAC de broadcast?

La IP del dispositivo conectado a la red Wi-Fi fue: 192.168.8.174. Mientras que, la máscara de subred fue: 255.255.255.0, que corresponde a una máscara /24.
Con estos datos, se realiza una operación OR entre la dirección IP y el complemento uno a uno de la máscara de subred para obtener la dirección MAC de Broadcast. Para ello, debe utilizarse su representación en binario, como se muestra en la siguiente tabla

<img width="737" height="134" alt="image44" src="https://github.com/user-attachments/assets/c36a9264-887b-4d46-badc-4aa1f109aafe" />

Luego, la operación resulta en

<img width="579" height="78" alt="image38" src="https://github.com/user-attachments/assets/47199c98-ce9a-4f3f-91e9-5dc78a4d648c" />

Por lo que la dirección de broadcast es 192.168.8.255.
La dirección MAC de broadcast está fijada por el estándar IEEE 802 como una constante universal de capa 2. Se compone de 48 bits fijados en 1, cuya representación hexadecimal es FF:FF:FF:FF:FF:FF. Este valor fue verificado en Wireshark al inspeccionar la cabecera Ethernet II de los datagramas UDP recibidos.
A continuación, se muestra una tabla donde se observan las diferentes direcciones IP de interés

<img width="467" height="230" alt="image37" src="https://github.com/user-attachments/assets/6577b406-eefe-4b5f-83a7-e8bbb688ff6a" />

## 2) Abran Wireshark en la interfaz Wi-Fi y capturen al menos 2 minutos. Pueden llegar varios mensajes; no tienen porqué ser todos idénticos.

A continuación, se muestran algunos paquetes capturados en Wireshark.

<img width="1163" height="106" alt="image25" src="https://github.com/user-attachments/assets/65da2e65-0324-4b61-bfc1-9b9fc9896d93" />

## 3) Analicen la estructura del mensaje. ¿Qué formato tiene? ¿Qué campos contiene y qué creen que representa cada uno? Con lo visto en la sección 1, propongan cómo hay que interpretar los datos.
En la captura anterior, se observan tres paquetes “basura” que fueron emitidos para despistar la identificación del paquete real. En dicho paquete, se observa que su formato representa un texto JSON donde:
  * SIZE indica las dimensiones de la matriz que debe formarse.
  * PL: indica los bits que deben ser analizados utilizando bits de paridad.
  * CHECK: indica los bits de paridad por fila y por columna, antes de que el paquete fuera enviado.

Estos datos deben interpretarse como bits en una matriz bidimensional, en la que deberá verificarse la integridad de cada uno utilizando los bits de paridad de filas y columnas. Una vez corregidos los errores, debe convertirse la secuencia de bits en caracteres ASCII de 7 bits para obtener un texto legible.


