
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


## 4) Verificar la integridad del mensaje con el codigo de la seccion 1: recalculen las paridades y comparenlas con las recibidas. Registren que las fila y que columnas fallan (el sindrome).

## 5) Si hay errores, ubíquenlos y corríjanlos. Para cada bit corregido indiquen fila, columna, valor recibido y valor corregido. Si recibieron más de un mensaje distinto, analicen cada uno por separado.

## 6) Construyan un archivo de texto en el formato de mensaje.txt con los datos ya corregidos y decodifíquenlo con decodificar_mensaje.py (o el cuaderno). Si todo salió bien, el mensaje les va a indicar cómo seguir. Ojo: un mensaje que "se lee bien" no es necesariamente un mensaje correcto.

Se recibieron tres diferentes mensajes, los cuales se muestran a continuación, junto con su comprobación de paridad y el resultado que se obtiene al realizar las correcciones pertinentes.

PREMIO 1:
{"SIZE": "8,7", "PL": "11010001110100111010011100001110011011101001011110101111111100111011111110101111010011101011100010110010101011101100011110111111011010101111111001111010001101111111001011101001110011010111111100010111000111011111001111001011111101010010101110111101000011000010100100011111111001101100101110000111101001110101111001010001010111101111001111010001100001111001011001010100000010000001000000100000", "CHECK": "011111010110111111110110011100101111001100001100110010001"}

<img width="1255" height="207" alt="image43" src="https://github.com/user-attachments/assets/18e05142-fb25-4e9d-ab0a-fef53a854900" />
<img width="1246" height="370" alt="image32" src="https://github.com/user-attachments/assets/93471b60-91cc-402e-b4f9-c46c64064ab2" />

El mensaje posee un error en las siguientes posiciones de la matriz: [5,9],[6,17],[7,23]
<img width="1252" height="102" alt="image30" src="https://github.com/user-attachments/assets/530e5a85-c5b2-4c92-8c7c-95a40466ee18" />

PREMIO 2:
{"SIZE": "10,6", "PL": "111100011101001110100111000011100110111010010111101011111111001110111111101011110100111010111000101100101010111011000111101111110110101011111110011110100011011111110010111010011101110101111101011110000111101001011010111010001111101011000110001011110001111000110010010111111110011011001011100001111010011101011110010110110101111011110011110100011000011110010110010101000000100000010000001000000100000010000001000000100000", "CHECK": "1000000100101001111100001011110111100110101001011001"}

<img width="1247" height="247" alt="image34" src="https://github.com/user-attachments/assets/adeaaffe-ce0f-4a10-a2fb-a8dfec402adb" />
<img width="1247" height="418" alt="image29" src="https://github.com/user-attachments/assets/a8dd95c6-b56f-4e21-95ad-43d9e20de2c3" />

El mensaje posee un error en las siguientes posiciones de la matriz: [1,3],[5,12],[6,18],[8,25]
<img width="1247" height="102" alt="image47" src="https://github.com/user-attachments/assets/4f28fe54-8447-4e75-b3e5-356bcae90f3f" />

PREMIO 3:
{"SIZE": "4,4", "PL": "1010001111001001100111101101110100101110000100001011101001010010110001111000001011011100100100100111001111011010", "CHECK": "10001110100011101010001110100000"}

<img width="1247" height="182" alt="image36" src="https://github.com/user-attachments/assets/7a2feecd-f925-48aa-8d1b-495984802036" />
<img width="1251" height="245" alt="image41" src="https://github.com/user-attachments/assets/8db31618-e256-4e8b-9882-e100eda49cda" />

El mensaje posee un error en las siguientes posiciones de la matriz: [1,7],[2,11],[3,15],[4,20]
<img width="1252" height="100" alt="image28" src="https://github.com/user-attachments/assets/efa3051e-0bd1-47cd-8644-7551b839d327" />

Además de estos paquetes, se recibieron los siguientes paquetes “basura”:

{"SIZE": "2,23", "PL": "https://www.youtube.com/watch?v=CsGYh8AacgY", "CHECK": "110011001100"}

{"SIZE": "N,M", "PL": "https://www.youtube.com/watch?v=ahE0VT3suZY", "CHECK": "110011001100"}

Que fueron utilizados para que no sea tan fácil obtener el paquete verdadero.
