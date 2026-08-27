# 4) Vamos ahora a discutir e investigar cómo podemos empezar a interpretar la información una vez decodificada:
   
   a) ¿Qué significa sincronización en una comunicación digital? Investigar la diferencia entre sincronización de bits y sincronización de trama.

   b) ¿Qué es una trama (frame)? ¿Qué diferencias existen entre el encabezado (header), la carga útil (payload) y el tráiler (trailer)?
   
   c) ¿Qué función puede cumplir un preámbulo antes de una trama? ¿Es necesariamente parte de la información que se quiere transmitir?
   
   d) Investigar al menos tres formas mediante las cuales un protocolo puede determinar dónde termina una trama: longitud fija, un campo que indique la longitud y caracteres/secuencias delimitadoras.
   
---
a)

Sincronización digital: 

La sincronización digital es el mecanismo que le permite al receptor saber en qué instante exacto debe muestrear la señal para interpretar de manera correcta cada bit y cada bloque de datos que llega. Si no hay sincronización, el receptor no sabría dónde empieza y donde termina cada unidad de información. (Aunque la señal física llegue perfectamente)

- Sincronización de bits: El receptor tiene que saber a que velocidad llegan los bits para poder leer la línea en los instantes correctos y no confundir, por ejemplo, dos bits iguales consecutivos con uno solo. Para esto se puede lograr de dos formas típicas: una es enviando un reloj por línea aparte o la otra es incrustando la sincronización en la propia señal

- Sincronización de trama: Acá una vez que el receptor está leyendo los bits correctamente, necesita también saber dónde arranca y dónde termina cada bloque (la trama) dentro de ese flujo continuo de bits. 

---

b) 

Una trama o frame es un bloque estructurado de bits que se transmiten como una unidad de comunicación, está compuesta por los datos, la información de control de la comunicación y mecanismos para la detección de errores.
Diferencias entre encabezado, la carga útil y trailer

El encabezado es el campo de información de control, anteriores a la carga util.

La carga útil es el bloque que contiene toda la información real que se necesita comunicar.

El trailer son todos los campos de control luego de la carga útil. Estos están diseñados para garantizar la integridad física de la comunicación.

---

c)

Un preámbulo sirve principalmente para sincronizar el receptor con el emisor antes de que comience la transmisión de los datos reales. Es una secuencia de bits conocida (patrón fijo, por ejemplo 10101010...) que se envía antes de la “trama” para que el receptor sincronice su reloj con el del transmisor y detecte el inicio de la transmisión. 
No es parte de la información útil que se quiere transmitir, es una sincronización, se considera una extra de bits(overhead) necesarios para el control de la comunicación, se descarta una vez cumplida su función.

---

d)

Para que el receptor sepa exactamente dónde empieza y dónde termina termina cada bloque existen estos tres métodos:

- Tramas de longitud fija: en este método, el protocolo establece que absolutamente todas las tramas tendrán exactamente el mismo tamaño. Su funcionamiento se basa en que el receptor no necesita buscar un final; simplemente cuenta los bits a medida que llegan. Si la longitud fija es de 100 bits, sabe que el bit 101 es el inicio de la siguiente trama.

- Conteo de caracteres: en lugar de forzar un tamaño único, las tramas pueden ser de tamaño variable. Para determinar el final, se incluye un número en el encabezado (header) de la trama. Esta técnica se basa en que el protocolo dedica el primer campo de la trama a especificar cuántos bytes o caracteres contiene en total. El receptor lee ese número y cuenta esa cantidad exacta de bytes para saber dónde termina.

- Banderas / Flags: este es el método más utilizado y robusto en las redes modernas (como Ethernet o PPP). Para esto se define un patrón de bits específico o un carácter ASCII especial para que actúe como un marcador o bandera. El protocolo coloca esta bandera al principio y al final de cada trama. El receptor sólo debe escuchar el medio y buscar ese patrón para saber que una trama acaba de terminar.
