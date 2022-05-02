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

* Para la continuación del desarrollo del proyecto se deben considerar los siguientes requerimientos:
* Funcionales
    * REQ-001: EL eie_manager debe exponer un API para comunicarse con el cliente externo, esta comunicación debe darse mediante un protocolo con un mismo lenguaje entre los dispositivos.
    * REQ-002: Los eieDevice deben generar respuestas a través del eie_manager en función de los requerimientos del cliente externo así como las capacidades de funcionalidad de los dispositivos.
    * REQ-003: El eie_manager debe generar una respuesta final para enviar al cliente externo, con toda la información recopilada en el proceso de comunicación.
   
* No funcionales
    * REQ-004: Los comandos de comunicación deben estar pre definidos y deben de tener algún formato específico para poder identificarlos.
    * REQ-005: Los comandos deben ser diseñados para ser dirigidos tanto a un dispositivo en específico como a un grupo de broadcast. En el segundo caso, todos los dispositivos en el grupo de broadcast deberán recibir el mismo comando.
    * REQ-006: El API debe ser construido de forma que pueda ser facilmente consumido por otos desarrolladores para la implementación de un app móvil con GUI. Es importante que la plataforma no esté capacitada únicamente para un lenguaje ya que se debe cinsiderar la implementación de esta app en cualquier lenguaje y/o entorno.
    * REQ-007: Continunando con el API es muy destacable la modificabilidad, ya que esta debe soportar dispositivos heterogéneos, de distintos fabricantes y/o características. DE la misma forma que debe soportar la incorporación de nuevos dispositivos, sin que eso implique cambio alguno en la interface. También es importante considerar que estos nuevos dispositivos pueden requerir de nuevos protocolos de comunicación.
    * REQ-008: El sistema debe ser capaz de generar una amplia variedad de comandos. Nuevos comandos deben ser sencillos de agregar y esto no debe implicar cambios en el API.
    * REQ-009: El sistema debe tener un rendimiento y escalabilidad considerables. Para esto es importante considerar la concurrencia y el paralelismo en la implementación de los dispositivos y los patrones de comunicación, de forma que múltiples procesos e información puedan estar en movimiento a la hora de la ejecución.
    * REQ-010: El sistema debe ser capaz de volver a su estado incial de forma eficaz (con la velocidad que mantenga el sistema y con la productividad requerida) cuando haya algún fallo o caída inesperada.


ADD
==================

PContinuando con la arquitectura del proyecto, se procede a crear el diseño, en este caso siguiendo la metodología Attribute-driven design (ADD).
PSegún se pudo concluir en las reuniones, se requiere de al menos dos iteraciones del proceso para la comprobación de la arquitectura a utilizar, en este caso se realizarán al menos dos iteraciones para abarcar a eie_manager y eieDevice.

* Comprobación de requerimientos.
    * Para la comprobación de requerimientos se analizan los requerimientos en función de los objetivos de negocio, como también se procede a realizar escenarios de calidad para los determinados requerimientos.


+-------+-----------------------------------------------------------------------------+------------+
|REQ    |                                                                             |  Prioridad |
+=======+=============================================================================+============+
|REQ-001|Se requiere que el API no esté predefinido para ningun lenguaje en específico| Alta       |
|       |tambien debe ser de facil consumo para otros desarrollaodores,               |            |
|       |debe poder ser implementada en un app movil.                                 |            |
|       |(Modifiability)                                                              |            |
+-------+-----------------------------------------------------------------------------+------------+
|       | Los eieDevice deben poder responder a los comandos de ingreso con           | Alta       |
|REQ-002| comandos de salida en funcion de lo requerido por el usuario. (Funcionality)|            |
|       |                                                                             |            |
|       |                                                                             |            |
+-------+-----------------------------------------------------------------------------+------------+
|REQ-003| eie_managerse debe diseñar de una forma que genere una respuets final al cli| Alta       |
|       | ente externo en funcion del proceso de recopilación de datos que lo precede.|            |
|       | (Funcionality)                                                              |            |
+-------+-----------------------------------------------------------------------------+------------+
|REQ-004| Se debe crear un lenguaje de comandos que debe ser entendible por todos lo  |Alta        |
|       | s dispositivos que formen parte del sistema, esto para tener un lenguaje    |            |
|       | universal dentro del sistema.    (Usability)                                |            |
+-------+-----------------------------------------------------------------------------+------------+
|REQ-005| Los comandos deben poder ser enviados a los dispositivos internos tanto     | Alta       |
|       | como a grupos de broadcasty debe ser funcional.                             |            |
|       | (Funcionality)                                                              |            |
+-------+-----------------------------------------------------------------------------+------------+
|       |                                                                             | Alta       |
|REQ-006|                                                                             |            |
|       |                                                                             |            |
|       |                                                                             |            |
+-------+-----------------------------------------------------------------------------+------------+
|       | Es importante que eie_manager mediante el API soporte la heterogeneidad de  | Alta       |
|REQ-007| dispositivos, en forma y de fabricantes.                                    |            |
|       | (Portability)                                                               |            |
|       |                                                                             |            |
+-------+-----------------------------------------------------------------------------+------------+
|       |                                                                             | Alta       |
|REQ-008|                                                                             |            |
|       |                                                                             |            |
+-------+-----------------------------------------------------------------------------+------------+
|REQ-009| Es importan que el sistema tenga un rendimiento y escalabilidad adecuada a l| Media      |
|       | as exgencias que el sistema le requiere. Considerar el paralelismo en el    |            |
|       | diseño.       (eficiency)                                                   |            |
+-------+-----------------------------------------------------------------------------+------------+
|REQ-010| Que el sistema tenga alta disponibilidad, siendo capaz de volver a su estado| Media      |
|       | inicial en casos de fallos y caídas inesperadas.                            |            |
|       | (Usability)                                                                 |            |
+-------+-----------------------------------------------------------------------------+------------+

* Descomposición de elemento del sistema:
    * Después del análisis se determinó que la primera iteración de este diseño se va a realizar sobre el eie_manager.
    * Se opta a empezar por este debido a que conlleva gran porcentaje de la funcionalidad del sistema.
    * eie_manager interacciona con todos los dispositivos del sistema, deben construirse varios sub dispositivos dentro de este.

* Atributos primitivos que satisfacen los requerimientos:
    * Según se conoció del análisis, una lista de posibles componenentes dentro de eie_manager está dada por,
        *  ConfigHandler
        *  APIServer
        *  CommandRegistry
        *  DeviceManager
        *  GroupManager
        *  CommandInvoker
        *  TransportClient
        *  DatabaseHandler
        *  Device
        *  Group
        *  CommandInfo