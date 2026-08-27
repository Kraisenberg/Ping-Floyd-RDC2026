# 2) Análisis de Figura

## a) ¿Qué fenómeno físico se está representando? ¿Cuáles son sus características principales?

El fenómeno físico que se está representando es el **ruido**, ya que cuando una señal viaja del emisor al receptor, la señal recibida no es igual a la transmitida: se suman distorsiones propias del medio más señales no deseadas insertadas en algún punto del canal.

En el libro el ruido se clasifica en 4 categorías:

- Ruido térmico
- Ruido de intermodulación
- Diafonía
- **Ruido impulsivo** (este se representa en la figura)

### Características del ruido impulsivo

- No es continuo.
- Está formado por pulsos o picos irregulares, de corta duración y amplitud relativamente grande.
- Causas: perturbaciones electromagnéticas externas o fallos/defectos en equipos del sistema de comunicación.

**Según el tipo de dato ocurre cierto efecto:**

- **Datos analógicos:** es poco relevante ya que se percibe como un chasquido breve, sin pérdida significativa de inteligibilidad.
- **Datos digitales:** aquí es una de las principales fuentes de error. Un pico de muy corta duración puede corromper muchos bits consecutivos, ya que puede hacer que un receptor lea un 1 donde había un 0 o viceversa al muestrear la señal.

El ruido impulsivo, a comparación del ruido térmico, el ruido de intermodulación y la diafonía, es **impredecible**.

## b) Impacto del ruido en distintos tipos de señales

El fenómeno del "ruido" en las señales afecta tanto a señales analógicas como digitales, pero con consecuencias distintas. Las transmisiones analógicas sufren más el impacto del ruido, mientras que las transmisiones digitales y por fibra óptica son más resilientes.

### Transmisiones más afectadas

- **Radio AM:** el ruido cambia la amplitud de la onda, creando sonidos de estática molestos durante tormentas o cerca de cables eléctricos.
- **Televisión analógica antigua:** el ruido genera "nieve" visual o líneas negras en la pantalla.
- **Líneas telefónicas de cobre tradicionales:** las interferencias se escuchan como zumbidos o ecos de fondo.

### Transmisiones más resilientes

- **Fibra óptica:** transporta datos usando pulsos de luz en lugar de electricidad. El ruido electromagnético del ambiente no afecta a la luz.
- **Sistemas digitales (Wi-Fi, 5G, Ethernet):** usan técnicas matemáticas y códigos de corrección de errores para detectar si una parte de la señal falló y reconstruirla al instante.
- **Radio FM (Frecuencia Modulada):** cambia la frecuencia de la onda y no su amplitud, lo que la hace mucho más resistente al ruido que la AM.

## c) ¿Qué es la SNR? ¿Tiene relación con la BER?

La **SNR** (Signal-to-Noise Ratio) es la relación que mide la intensidad o potencia de la señal recibida (la información útil) frente al ruido de fondo presente en un punto determinado del medio de transmisión, y se expresa en decibelios:

$$SNR_{dB} = 10 \log_{10}\left(\frac{P_S}{P_N}\right)$$

donde:

- $P_S$ = potencia de la señal.
- $P_N$ = potencia del ruido.

### Relación con la BER

Los conceptos de SNR y BER están relacionados entre sí.

La **BER** (Bit Error Rate) es la probabilidad de que un bit transmitido sea recibido con error.

**A mayor SNR, menor va a ser la BER**, ya que un aumento en la SNR disminuye la tasa de errores de bits al haber más potencia de la señal sobre el nivel de ruido. Esto disminuye las probabilidades de que las perturbaciones alteren la señal recibida.

$$SNR = \frac{P_S}{P_N}$$
