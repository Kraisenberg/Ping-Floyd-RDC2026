**Punto 3\)**

Para este punto se creó, desde la computadora 1, el siguiente directorio:

<img width="1117" height="185" alt="image13" src="https://github.com/user-attachments/assets/5f88bcab-41ba-480a-a396-f20629634e4c" />

En la misma, se inicio el servidor en Python, usando el comando:

python3 -m http.server 8000

Desde la computadora 2, se accede al servidor ubicado en “http\://192.168.100.1”, descargando el archivo “imagen-2.png”.

Luego, usando el comando “curl”, se procede a descargar el archivo “pdf-1.pdf”

<img width="808" height="92" alt="image6" src="https://github.com/user-attachments/assets/701dc992-1d12-4420-b471-9c13d2d1af23" />

En la terminal del servidor, podemos comprobar que este recibe las peticiones y entrega correctamente los archivos, respondiendo con códigos de estado HTTP 200 OK (y 304 para los archivos.

<img width="931" height="127" alt="image7" src="https://github.com/user-attachments/assets/dcc81527-0099-41a7-a716-1f3e7b6f07aa" />
Capturando el trafico desde Wireshark, obtenemos:
<img width="1600" height="167" alt="image11" src="https://github.com/user-attachments/assets/5ca0d14b-2837-42a6-857d-0bf576c9047d" />

<img width="1600" height="202" alt="image2" src="https://github.com/user-attachments/assets/2fd86d12-01ac-4017-b7d2-f312b5fc3d89" />

<img width="1600" height="271" alt="image12" src="https://github.com/user-attachments/assets/2f4b9995-4822-42cd-85c3-318b58f5f05c" />

Finalmente, podemos ver que tenemos un “tráfico HTTP” de la capa de aplicación que viaja sobre TCP.
