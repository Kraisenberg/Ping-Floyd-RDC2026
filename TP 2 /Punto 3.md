# 3) ¿Cómo ayudan los sistemas de transmisión digital a detectar y corregir errores producidos por ruido en el canal? ¿Y a compensar cambios en la frecuencia?

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

¿Cómo ayudan los sistemas de transmisión digital a detectar y
corregir errores producidos por ruido en el canal? ¿Y a compensar cambios en la frecuencia?
A diferencia de los sistemas analógicos (donde el ruido ambiental se suma inevitablemente a la señal), los sistemas digitales transmiten un flujo de bits. Esto les permite proteger la información agregando redundancia matemática en la capa de enlace:
Para detectar (detección de errores): el equipo transmisor agrupa los datos y les aplica una función matemática (CRC o Comprobación de Redundancia Cíclica). El resultado se añade al final de la trama.
Para corregir (corrección de errores): se utilizan técnicas mucho más avanzadas como FEC (Forward Error Correction). En lugar de solo avisar si hay un error, el transmisor envía bits adicionales estructurados de tal forma que le permiten al receptor deducir exactamente qué bit falló y revertirlo matemáticamente.
Mientras que, para lidiar con los corrimientos de frecuencia analizados en los puntos anteriores, los sistemas de transmisión digital emplean técnicas de rastreo dinámico en la capa física:
Lazos de seguimiento de fase (PLL): los receptores digitales utilizan circuitos de hardware que persiguen activamente la frecuencia portadora. Si la frecuencia entrante sube o baja debido a la velocidad del emisor, el PLL ajusta su propio oscilador local en tiempo real para no perder la sincronía.
Señales Piloto: en esquemas de modulación modernos, el transmisor intercala “subportadoras piloto” entre los datos útiles. Estas son frecuencias de referencia fijas y conocidas. El receptor analiza cómo el efecto Doppler desfasó a estos pilotos y luego aplica esa misma corrección matemática a los canales de datos para recuperar la información intacta.
