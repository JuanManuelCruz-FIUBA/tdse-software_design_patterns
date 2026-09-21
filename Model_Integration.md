<b>Model Integration</b>

  * Los patrones de diseño (**design patterns**) son soluciones habituales a problemas comunes en el diseño de software. Cada patrón es como un plano que se puede personalizar para resolver un problema de diseño particular de tu código.
  * Ejemplo de *Modularización* del código en en *tareas* del tipo: **Escrutar - Procesar - Actuar**.
    * **Escrutar**  => *Sensor*
      * Genera sus propios *eventos* por *Polling* de **GPIO**), que estimulan su *statechart*
      * Genera *eventos* para el módulo siguiente, mediante la *interfaz* correspondiente.
    * **Procesar**  => *System*
      * Recupera *eventos* generados por el módulo anterior, mediante la *interfaz* correspondiente, que estimulan su *statechart*
      * Genera *eventos* para el módulo siguiente, mediante la *interfaz* correspondiente.
    * **Actuar**    => *Actuator*
      * Recupera *eventos* generados por el módulo anterior, mediante la *interfaz* correspondiente, que estimulan su *statechart*
      * Actúa sobre **GPIO** 
