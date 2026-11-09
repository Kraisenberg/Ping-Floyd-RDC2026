# CODIGO HAMMING (7,4) #

El código Hamming (7,4) es un esquema de codificación lineal de bloques introducido por Richard Hamming que toma bloques de 4 bits de datos y les añade 3 bits de paridad redundantes, generando palabras de código de 7 bits en total. Es un código de corrección hacia adelante (FEC) capaz de detectar hasta 2 errores en un bloque y corregir automáticamente 1 error de bit sin necesidad de retransmisión.

Para facilitar la identificación del bit fallido mediante aritmética binaria, las posiciones de los 7 bits se numeran del 1 al 7. los bits de paridad se sitúan estrictamente en las potencias de base 2 (2<sup>0</sup>, 2<sup>1</sup>, 2<sup>2</sup>), mientras que los bits de datos ocupan las posiciones restantes. La palabra de código transmitida tiene la forma:

<div align="center"><img width="300" height="55" alt="image" src="https://github.com/user-attachments/assets/efc48060-4f2a-416d-aaa0-0874b92476be" /></div>
<div> <br> </div>

Cada bit de paridad pk supervisa a todas aquellas posiciones cuya representación binaria tiene un 1 en la posición correspondiente al peso de pk:

- p1 cubre posiciones con el bit menos significativo en 1 → 1, 3, 5, 7:
  
<div align="center"><img width="350" height="34" alt="image" src="https://github.com/user-attachments/assets/eae79bbc-46b1-48a1-bfd2-c5c519b9e93f" /></div>


- p2 cubre posiciones con el bit menos significativo en 1 → 2, 3, 6, 7: 

<div align="center"><img width="350" height="34" alt="image" src="https://github.com/user-attachments/assets/06a952b8-0d4e-4b6a-ad55-78dc0cc29063" /></div>


- p2 cubre posiciones con el bit menos significativo en 1 → 4, 5, 6, 7:

<div align="center"><img width="350" height="30" alt="image" src="https://github.com/user-attachments/assets/cd3e637c-46f7-4050-ba23-5e4d885f47c5" /></div>

  

Donde <td>&#8853;</td> representa una compuerta XOR.
<div> <br> </div>

Dado un vector fila de datos d = [d<sub>1</sub>  d<sub>2</sub>  d<sub>3</sub>  d<sub>4</sub>], la palabra de código transmitida *c* se genera mediante

<div align="center"><img width="119" height="45" alt="image" src="https://github.com/user-attachments/assets/a9e5e97b-cee9-4e67-871b-5e8d5a7637ef" /></div>
<div> <br> </div>

Donde <td>*G* &isin;</td> *GF* (2)<sup>4x7</sup> es la matriz generadora y está dada por:

<div align="center"><img width="344" height="150" alt="image" src="https://github.com/user-attachments/assets/497c7535-e739-4d86-85c7-964383f2e071" /></div>
<div> <br> </div>

La matriz de comprobación de paridad (H) es de dimensiones 37 y se construye colocando en cada columna la representación binaria de la posición correspondiente

<div align="center"><img width="380" height="150" alt="image" src="https://github.com/user-attachments/assets/a04ebc00-86cd-48a5-bb16-72051539627d" /></div>
<div> <br> </div>

Por diseño algebraico, cualquier palabra válida c cumple

<div align="center"><img width="136" height="45" alt="image" src="https://github.com/user-attachments/assets/d390edbf-9462-4ee4-962c-7759a476b26f" /></div>
<div> <br> </div>

Cuando el receptor recibe una palabra r=ce (donde e es el vector de error inducido por el canal), calcula el vector síndrome de 3 bits

<div align="center"><img width="234" height="45" alt="image" src="https://github.com/user-attachments/assets/87ff460c-7488-4395-9bb4-424e49ef251e" /></div>
<div> <br> </div>

Si no hubo errores detectables en la transmisión, entonces

<div align="center"><img width="155" height="45" alt="image" src="https://github.com/user-attachments/assets/6acb7ee9-e851-4405-ace9-66405706352d" /></div>
<div> <br> </div>

Pero si

<div align="center"><img width="136" height="45" alt="image" src="https://github.com/user-attachments/assets/6a521eaf-ab62-47cb-9e4c-3744bf9b17e7" /></div>
<div> <br> </div>

El valor numérico del síndrome interpretado en base 2 indica exactamente el índice del bit alterado, debido a que las columnas de H están ordenadas según el valor binario de su posición.

<div> <br> </div>
Una vez identificada la posición k, la corrección consiste en invertir el bit en esa posición

<div> <br> </div>
<div align="center"><img width="167" height="45" alt="image" src="https://github.com/user-attachments/assets/65280e24-db52-490f-beb7-88f2cc96bbf4" /></div>
<div> <br> </div>


Este método de corrección de errores es superior al de paridad bidimensional ya que posee las siguientes diferenciales

<div> <br> </div>
<ul>
  <li>
    Eficiencia de redundancia y código perfecto: Cumple con igualdad estricta la cota de Hamming
    <br><br>
    <div align="center"><img width="535" height="80" alt="image" src="https://github.com/user-attachments/assets/d2064c12-ee85-43db-848c-de499e13df6e" /></div>
    <br><br>
    Lo que hace que no desperdicie combinaciones del espacio de estados (2<sup>3</sup>=8). Los posibles valores del síndrome se asignan sin redundancia sobrante (1 estado para “sin error” y 7 estados para cada posible posición individual que falla).
  </li>
</ul>
  

- Menor sobrecarga (overhead): La tasa de código es R=4/7 <td>&#8776;</td>  57.1% de carga útil neta en bloques de apenas 4 bits, requiriendo únicamente 3 bits de control.

- Corrección directa sin ambigüedad geométrica: Procesa cada bloque de 7 bits de manera autónoma, logrando un tiempo de procesamiento determinista en hardware O(1) mediante compuertas XOR en paralelo, sin necesidad de algoritmos de búsqueda o permutaciones de matrices.

- Capacidad SEC-DED (Hamming extendido): Añadiendo un único bit de paridad global adicional (Hamming 8,4), la distancia mínima de Hamming pasa de d<sub>min</sub>= 3 a d<sub>min</sub> = 4. Esto confiere capacidad SEC-DED (Single Error Correction, Double Error Detection), estándar utilizado en hardware de misión crítica y memorias RAM ECC para corregir un bit alterado y alertar sin falsas correcciones si se alteraron dos bits simultáneos.







<div> <br> </div>

## Aplicacion de Codigo Hamming ##

<div> <br> </div>

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

