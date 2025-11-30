### Analiza y triunfaras

Antes que nada, quiero comentar algo: aunque este laboratorio es relativamente sencillo, requiere bastante paciencia y perseverancia. Si quieren obtener los resultados correctos, es clave prestar atención a los detalles: las fechas de los análisis, los nombres de los archivos y cualquier pista pequeña que pueda parecer insignificante.

Lo primero que me llamó la atención, apenas abrí la captura en Wireshark, fue esto:

![Figura 1](img/dana0.png)

Como analistas, una de las primeras cosas que debemos tener siempre presente es:

- Quién se está conectando a nuestra red y desde dónde lo está haciendo.

![Figura 2](img/dana1.png)

Al seguir revisando, noté lo siguiente:

- En VirusTotal, el dominio aparecía relacionado con actividad maliciosa.

![Figura 3](img/dana2.png)

También consulté el dominio en URLhaus, donde aparecía reportado en varios registros recientes, lo que reforzaba la correlación con campañas de distribución de malware.

![Figura 4](img/dana4.png)

Con estos indicios sobre la mesa, era momento de ponernos en marcha y empezar a reconstruir paso a paso lo que realmente había ocurrido en la captura.
Al revisar el inicio de la captura, se puede observar claramente el three-way handshake previo a la conexión TCP donde ocurre el acceso inicial. También la dirección IP asociada al atacante y el dominio previamente identificado en Virustotal y URLhaus.

![Figura 5](img/dana5.png)

Si prestamos suficiente atención a los primeros paquetes posteriores a la conexión, notamos que se produce una transferencia de datos acompañada por un código de estado HTTP 200 OK. Siguiendo ese hilo, es posible identificar con claridad el archivo que se está intercambiando durante la sesión.

![Figura 6](img/dana6.png)

Y acá es donde entra en juego el tema de los hashes y todo ese análisis adicional. Usualmente estoy acostumbrado a descargar el archivo directamente y calcular su hash con alguna herramienta en Linux, pero en este caso eso no es posible: el dominio ya no funciona. Por lo tanto, toca investigar análisis previos, reportes ya publicados o cualquier referencia que aparezca relacionada con el nombre del archivo para avanzar con la identificación.

En mi búsqueda, encontré que en ANY.RUN había información relacionada con el archivo, y para corroborarlo lo verifiqué también en Hybrid-Analysis, donde los resultados coincidían y reforzaban la identificación del malware.

![Figura 7](img/dana7.png)

![Figura 8](img/dana8.png)





