# CODIGO HAMMING (7,4) #







<div> <br> </div>

## Aplicacion de Codigo Hamming ##

**Aplicaremos el codigo Hamming para el payload del mensaje del primer premio**
<div> <br> </div>


Primero tomamos el json obtenido en wireshark

{"SIZE": "8,7", "PL": "11010001110100111010011100001110011011101001011110101111111100111011111110101111010011101011100010110010101011101100011110111111011010101111111001111010001101111111001011101001110011010111111100010111000111011111001111001011111101010010101110111101000011000010100100011111111001101100101110000111101001110101111001010001010111101111001111010001100001111001011001010100000010000001000000100000", "CHECK": "011111010110111111110110011100101111001100001100110010001"}
<div> <br> </div>


Vamos a aplicar el código de hamming para el binario del payload (**corregido**)

11010001110100111010011100001110011011101001011110101111111100111011111110101111010011101011100010110010101011101100011110111111011010101111111001111010001101111111001011101001110011010111111100010111000101011111001111001011111101010010101110111101000011000010110100011111111001101100101110000111101001110101111001011001010111101111001111010001100001111001011001010100000010000001000000100000 
<div> <br> </div>


* **PASO 1 - Dividir el payload en diferentes nibbles**

  Como son 392 bits divididos en nibbles, quedan 98 nibbles los cuales dividimos en 7 filas para mayor organización (el orden de los datos va desde la primera columna de la primer a ultima fila y luego se pasa a la siguiente columna)

<table align="center">
  <tr align="center"><td>1101</td><td>1111</td><td>1100</td><td>1110</td><td>1111</td><td>1100</td><td>1101</td></tr>
  <tr align="center"><td>0001</td><td>0011</td><td>0111</td><td>1001</td><td>0101</td><td>1011</td><td>0001</td></tr>
  <tr align="center"><td>1101</td><td>1011</td><td>1011</td><td>1100</td><td>0010</td><td>1000</td><td>1000</td></tr>
  <tr align="center"><td>0011</td><td>1111</td><td>1111</td><td>1101</td><td>1011</td><td>0111</td><td>0111</td></tr>
  <tr align="center"><td>1010</td><td>1010</td><td>0110</td><td>0111</td><td>1011</td><td>1010</td><td>1001</td></tr>
  <tr align="center"><td>0111</td><td>1111</td><td>1010</td><td>1111</td><td>1101</td><td>0111</td><td>0110</td></tr>
  <tr align="center"><td>0000</td><td>0100</td><td>1111</td><td>0001</td><td>0000</td><td>0101</td><td>0101</td></tr>
  <tr align="center"><td>1110</td><td>1110</td><td>1110</td><td>0111</td><td>1100</td><td>1110</td><td>0100</td></tr>
  <tr align="center"><td>0110</td><td>1011</td><td>0111</td><td>0001</td><td>0010</td><td>0101</td><td>0000</td></tr>
  <tr align="center"><td>1110</td><td>1000</td><td>1010</td><td>1101</td><td>1001</td><td>0001</td><td>1000</td></tr>
  <tr align="center"><td>1001</td><td>1011</td><td>0011</td><td>1111</td><td>0001</td><td>0101</td><td>0001</td></tr>
  <tr align="center"><td>0111</td><td>0010</td><td>0111</td><td>0011</td><td>1111</td><td>1110</td><td>0000</td></tr>
  <tr align="center"><td>1010</td><td>1010</td><td>1111</td><td>1100</td><td>1110</td><td>1111</td><td>0010</td></tr>
  <tr align="center"><td>1111</td><td>1110</td><td>0010</td><td>1011</td><td>0110</td><td>0011</td><td>0000</td></tr>
</table>
<div> <br> </div>

* **PASO 2 - Calcular la paridad segun la posicion de los bits**

  Para un nibble con posiciones d1 d2 d3 d4 calculamos las siguientes paridades:
  
  
  - p1 se calcula con d1 d2 y d4
  
  - p2 se calcula con d1 d3 y d4
  
  - p3 se calcula con d2 d3 y d4
  
  
  <div> <br> </div>
  
  - Si el grupo tiene paridad el bit de paridad toma el valor 0
  
  - Si el grupo no tiene paridad el bit de paridad toma el valor 1
  

  Terminando en una palabra de 7 bits conformada de la siguiente manera:

<table align="center">
  <tr align="center">
    <td><b>Posición</b></td>
    <td>1</td>
    <td>2</td>
    <td>3</td>
    <td>4</td>
    <td>5</td>
    <td>6</td>
    <td>7</td>
  </tr>
  <tr align="center">
    <td><b>Valor</b></td>
    <td>p1</td>
    <td>p2</td>
    <td>d1</td>
    <td>p3</td>
    <td>d2</td>
    <td>d3</td>
    <td>d4</td>
  </tr>
</table>
<div> <br> </div>
Teniendo todo esto en cuenta los nibbles pasan a palabras de 7 bits como se ve a continuación:
<div> <br> </div>
<table align="center">
  <tr align="center"><td>1010101</td><td>1111111</td><td>0111100</td><td>0010110</td><td>1111111</td><td>0111100</td><td>1010101</td></tr>
  <tr align="center"><td>1101001</td><td>1000011</td><td>0001111</td><td>0011001</td><td>0100101</td><td>0110011</td><td>1101001</td></tr>
  <tr align="center"><td>1010101</td><td>0110011</td><td>0110011</td><td>0111100</td><td>0101010</td><td>1110000</td><td>1110000</td></tr>
  <tr align="center"><td>1000011</td><td>1111111</td><td>1111111</td><td>1010101</td><td>0110011</td><td>0001111</td><td>0001111</td></tr>
  <tr align="center"><td>1011010</td><td>1011010</td><td>1100110</td><td>0001111</td><td>0110011</td><td>1011010</td><td>0011001</td></tr>
  <tr align="center"><td>0001111</td><td>1111111</td><td>1011010</td><td>1111111</td><td>1010101</td><td>0001111</td><td>1100110</td></tr>
  <tr align="center"><td>0000000</td><td>1001100</td><td>1111111</td><td>1101001</td><td>0000000</td><td>0100101</td><td>0100101</td></tr>
  <tr align="center"><td>0010110</td><td>0010110</td><td>0010110</td><td>0001111</td><td>0111100</td><td>0010110</td><td>1001100</td></tr>
  <tr align="center"><td>1100110</td><td>0110011</td><td>0001111</td><td>1101001</td><td>0101010</td><td>0100101</td><td>0000000</td></tr>
  <tr align="center"><td>0010110</td><td>1110000</td><td>1011010</td><td>1010101</td><td>0011001</td><td>1101001</td><td>1110000</td></tr>
  <tr align="center"><td>0011001</td><td>0110011</td><td>1000011</td><td>1111111</td><td>1101001</td><td>0100101</td><td>1101001</td></tr>
  <tr align="center"><td>0001111</td><td>0101010</td><td>0001111</td><td>1000011</td><td>1111111</td><td>0010110</td><td>0000000</td></tr>
  <tr align="center"><td>1011010</td><td>1011010</td><td>1111111</td><td>0111100</td><td>0010110</td><td>1111111</td><td>0101010</td></tr>
  <tr align="center"><td>1111111</td><td>0010110</td><td>0101010</td><td>0110011</td><td>1100110</td><td>1000011</td><td>0000000</td></tr>
</table>

<div> <br> </div>

* **PASO 3 - Reorganizar la tabla en un unico binario**
  
Por último organizamos todas las palabras de 7 bits en orden y terminamos con esta carga útil de 686 bits:

10101011101001101010110000111011010000111100000000010110110011000101100011001000111110110101111111111111110000110110011111111110110101111111100110000101100110011111000001100110101010101101000101100111100000111101100111111111110011010110101111111001011000011111011010100001100011111111111010101000101100011001011110010101010001111111111111010010001111110100101001011111111100001101111000110011111111101001010101010011001101100111010101000000001111000101010101010111010011111111001011011001100111100011001111100000001111101101000011110100101001011001001010011001010010100101101111111100001110101011101001111000000011110011001110011001001011001100000000011100001101001000000001010100000000


**Acá tenemos una nueva carga útil codificada con Hamming (7,4)**

