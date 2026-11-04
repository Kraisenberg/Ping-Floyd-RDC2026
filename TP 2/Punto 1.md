# 1) Análisis de la figura

## a) ¿Qué se representa? Características principales

Lo que se representa es el **efecto Doppler**: el corrimiento/cambio de la frecuencia de una onda percibido cuando existe movimiento relativo entre la fuente y el receptor (o viceversa). En este caso, el satélite está en movimiento orbital respecto al barco, por lo que la frecuencia de la señal recibida no es exactamente la misma que la transmitida.

### Características principales

- **Corrimiento positivo (blueshift):** si el emisor y el receptor se están acercando, la frecuencia percibida aumenta (la longitud de onda se comprime) — es justo lo que se ve en la figura, la onda se va "apretando" hacia el satélite.
- **Corrimiento negativo (redshift):** si se están alejando, la frecuencia percibida disminuye (la longitud de onda se estira).
- **Depende de la velocidad relativa:** cuanto mayor la velocidad relativa entre transmisor y receptor, mayor el corrimiento de frecuencia ($\Delta f$).

## b) ¿A qué tipos de transmisión afecta? ¿Cuáles son más resilientes?

*Recordando las bandas de transmisión vistas en el TP01:*

- Las bandas de transmisión **más afectadas** por el efecto Doppler son las de **EHF, SHF y UHF**.
- Las bandas de transmisión **más resilientes** a este efecto son las de **HF, MF y LF**.

Básicamente, se observa que el efecto Doppler afecta mayormente a las bandas de transmisión de **alta frecuencia** y en menor medida a las de **baja frecuencia**.

## c) Relación entre el efecto Doppler y el modo avión en celulares

El efecto Doppler tiene que ver con el encendido de celulares arriba de un avión. Las razones son las siguientes:

- **Razones de seguridad (interferencia electromagnética):** los celulares emiten ondas electromagnéticas para buscar señal constantemente. Las emisiones espontáneas pueden inducir ruido o interferencias en los sistemas de navegación, radares y radios de comunicación sensibles de la cabina. También, al estar a gran altitud y dentro del fuselaje, el celular detecta una señal muy pobre. Para compensarlo, el dispositivo eleva automáticamente su potencia de transmisión al máximo, lo que multiplica el riesgo de causar interferencia electromagnética.

- **Problema de redes (congestión terrestre):** a más de 10.000 metros de altura, un teléfono pierde los obstáculos naturales y tiene "línea de vista" hacia varias torres celulares simultáneamente. Al intentar conectarse, hace ping a todas, saturando los canales de señalización y obligando a la red a intentar traspasos de conexión (*handoffs*) caóticos.

- **Relación directa con el efecto Doppler:** un avión comercial vuela a velocidades de crucero cercanas a los 900 km/h. A esa velocidad, el movimiento relativo entre el celular (emisor) y la torre en tierra (receptor) genera un corrimiento Doppler inmenso en la señal de radiofrecuencia. Las redes celulares convencionales tienen un margen de tolerancia al efecto Doppler calculado para autos en rutas o trenes rápidos. Sin embargo, el desplazamiento de frecuencia causado por un avión excede por completo esos filtros de paso banda. La antena terrestre recibe una frecuencia totalmente corrida, es incapaz de demodularla correctamente y el enlace se vuelve inservible.
