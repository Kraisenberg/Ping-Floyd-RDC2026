## 3) Analicen la estructura del mensaje. ¿Qué formato tiene? ¿Qué campos contiene y qué creen que representa cada uno? Con lo visto en la sección 1, propongan cómo hay que interpretar los datos.

En la captura anterior, se observan tres paquetes “basura” que fueron emitidos para despistar la identificación del paquete real. En dicho paquete, se observa que su formato representa un texto JSON donde:
SIZE indica las dimensiones de la matriz que debe formarse.
PL: indica los bits que deben ser analizados utilizando bits de paridad.
CHECK: indica los bits de paridad por fila y por columna, antes de que el paquete fuera enviado.

Estos datos deben interpretarse como bits en una matriz bidimensional, en la que deberá verificarse la integridad de cada uno utilizando los bits de paridad de filas y columnas. Una vez corregidos los errores, debe convertirse la secuencia de bits en caracteres ASCII de 7 bits para obtener un texto legible.
