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


