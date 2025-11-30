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

![Figura 6](img/dana6.png)

