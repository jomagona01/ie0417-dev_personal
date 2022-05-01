*************
Laboratorio 1
*************

Introducción
==================
* Desde el start-up eieLabs se requiere de la creación de un software centralizado que sea capaz de enviar comandos de control y status a los diferentes dispositivos interconectados.
    * Después de una reunión general se determinó que este software debe ser dividido en dos grandes áreas: eieManager y eieDevice.
    * El sistema desde una perspectiva muy amplia se determinó de la siguiente forma:
    
    
.. image:: /home/josemario/Pictures/Screenshots/diagramageneral.png
    :align: center


Planeamiento
==================

* Para iniciar con el planeamiento en este caso se pretende seguir una metología enfocada en los conceptos de planeamiento Agile, esencialmente contemplando responsabilidadesa largo plazo.
    * Se pretende cumplir con los requerimientos y las funcionalidades, dejando amplio espacio para la modificabilidad y el constante cambio.
* A corto plazo es importante enfocarse en la funcionalidad del sistema a gran escala.
    * Se procede a garantizar el completo entendimiento por parte de los equipos de trabajo del funcionamiento global del sistema, las funcionalidades y requerimientos de los dispositivos mas determinantes como lo son eie_manager, eieDevice y el API.
* Se determina un grupo de trabajo para el desarrollo de eie_manager.
    * Uno de los ejes del sistema es el dispositivo eie_manager por lo que es importante emfocarse de inmediato en este desarrollo, en este caso se deben contemplar las numerosas funcionalidades y requerimientos de este dispositivo como una de las mas exigentes por lo que se debe preveer los requisitos para el equipo de trabajo, apertura constante al cambio, intervalos de fechas, etc.
* Se determina un grupo de trabajo para el desarrollo de los eieDevice.
    * El sistema deberá almientar con una serie de requerimientos y funcionalidades a varios dispositivos que deberán equiparse con las suficientes capacidades de recepción y envío de información y comandos con eie_manager. Se deben reconocer los requerimientos así como las necesidades de este dispositivo para ser reproducido y modificado según se requiera.
* Equipo de recepción de client y desarrollo de API.
    * El sistema deberá de estar conectado y en constante comunicación con un client externo, para esto se deberá desarrollar un API que sea capaz de interpretar los requerimientos o necesidades del componente externo, para posteriormente llevarle la información a eie_manager, que transmite la información a los eieDevice, para finalmente enviar una respuesta al cliente por el mismo medio en función de las acciones que hayan tenido que ejecutar.
* Sección de comandos.
    * Es necesario la creación de un lenguaje de comandos que el sistema va a ser capaz de reconocer como el medio de intercomunicación de los dispositivos y el cliente.



Requerimientos
==================

* Especifique una lista de requerimientos funcionales y no funcionales detallados según el apartado 5.3 Specific Requirements del estándar IEEE Recommended Practice for Software Requirements Specifications (Std 830-1998).
    * Asegúrese de utilizar identificadores numéricos para todos los requerimientos (ej, REQ-XYZ).


