# FIUBA - Electrónica - Taller de Sistemas Embebidos
## Software Design Patterns
### Contexto

<details>
<summary><b>Codificamos en C, soluciones del tipo ...</b></summary>

* **Bare Metal** (sin Sistema Operativo)
  * **Cyclic Executive**
    * *Super-Loop* (**Polling & Interrupts**)
    * *Update by Time Code* (**period = 1mS**)
    * **Event-Triggered Systems**
    * **Estructurada, Modular**
      * *Escrutar - Procesar - Actuar*
    * **Software Design Patterns** (*Statecharts*)
      * **Portabilidad, Escalabilidad, Flexibilidad, Fiabilidad, Reutilización,**
      * **Rendimiento, Costo, Disponibilidad, Mantenibilidad, Sensibilidad,**
      * **Simplicidad, Razonabilidad, Colaboración, Capacidad de Prueba,**
      * **Eficiencia, Robustez, Previsibilidad, etc.**
  * **STM32CubeIDE**, entorno de desarrollo integrado multi-OS en C/C++ para el desarrollo de código STM32.
  * **STM32CubeMX**, herramienta gráfica que simplifica la configuración de los productos STM32 y genera el código de inicialización correspondiente.
  * **HAL**, capa de abstracción de hardware de STM32, un software embebido que garantiza la máxima portabilidad en toda la gama STM32.

</details>

<details>
<summary><b>Cyclic Executive ...</b></summary>

  * Modelo de *programación* y *planificación* de **tareas**
    * Ejecuta una secuencia fija de **tareas** en un bucle infinito (*Super-Loop*).
    * Permite implementar **Event-Triggered Systems**.
    * Permite gestionar *eventos* por **Polling & Interrupts**.
    * Permite ejecutar **tareas** del tipo *Non-Blocking Code* & *Update by Time Code* con **period = 1mS**.
    * Permite *Modularizar* el código en en *tareas* del tipo: **Escrutar - Procesar - Actuar**.
  * Requiere de:
      * Configurar el linker para agregar una biblioteca (y sus opciones de linkeo).
      * Excluir un archivo de la compilación para evitar conflictos con las llamadas al sistema del semihosting.
      * Configurar el depurador (*OpenOCD*).
      * Modificar el código fuente  código de dos archivo (```stm32f1xx_it.c``` & ```main.c```), como se detalla a continuación.
      * El **period** de ejecución de tareas (**1mS**) lo aporta una variable actualizada por un *Callback* del *Handler* de la *Interrupción* del **Systick**.
      * La vinculación entre ```main.c``` y ```app.c``` (**Cyclic Executive**) es mediante las funciones ```app_int()``` & ```app_update()```.
      * La vinculación entre ```app.c``` (**Cyclic Executive**) y ```task_name.c``` (**Task**) es mediante las funciones ```task_name_int()``` & ```task_a_update()```.
      * Agregar al *árbol de directorios* del proyecto, la carpeta **app**, destinada a almacenar código fuente y archivos de configuración creados por el usuario.
      * Incluir en la compilación, las carpetas **app/inc** & **app**, que contienen  archivos de encabezamiento (```.h```), de código fuente (```.c```) y de comentario (```.txt```).

```
cyclic_executive/Code/Src/stm32f1xx_it.c

  /* USER CODE BEGIN SysTick_IRQn 1 */

  HAL_SYSTICK_IRQHandler();

  /* USER CODE END SysTick_IRQn 1 */

/* USER CODE BEGIN Includes */

/* Application includes */
#include "logger.h"
#include "app.h"

/* USER CODE END Includes */


cyclic_executive/Code/Src/main.c

/* USER CODE BEGIN 0 */

#if (1 == LOGGER_CONFIG_USE_SEMIHOSTING)

extern void initialise_monitor_handles(void);

#endif

/* USER CODE END 0 */
  . . .

  /* USER CODE BEGIN 1 */

  #if (1 == LOGGER_CONFIG_USE_SEMIHOSTING)

  initialise_monitor_handles();

  #endif

  /* USER CODE END 1 */
  . . .

  /* USER CODE BEGIN 2 */

  /* Application Init */
  app_init();

  /* USER CODE END 2 */
  . . .

    /* USER CODE BEGIN 3 */

    /* Application Update */
    app_update();

  }
  /* USER CODE END 3 */
```

```
cyclic_executive
├───.settings
├───Core
├───Drivers
└───app
    ├───inc
    └───src
```
</details>

<details>
<summary><b>Model Integration</b></summary>

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

</details>

<details>
<summary><b>Software Design Patterns</b></summary>

  * Los patrones de diseño (**design patterns**) son soluciones habituales a problemas comunes en el diseño de software. Cada patrón es como un plano que se puede personalizar para resolver un problema de diseño particular de tu código.

</details>

---

### Proyectos de referencia
| Referencias | Fuentes |   |
| :------- | :----| - |
| [<b>STM32 Project</b>](https://github.com/JuanManuelCruz-FIUBA/tdse-software_design_patterns/blob/main/STM32_Project.md) | [stm32_project](https://github.com/JuanManuelCruz-FIUBA/tdse-software_design_patterns/tree/main/TdSE_workspace/stm32_project) | <b>X</b> |
| [<b>Semihosting</b>](https://github.com/JuanManuelCruz-FIUBA/tdse-software_design_patterns/blob/main/Semihosting.md) | [semihosting](https://github.com/JuanManuelCruz-FIUBA/tdse-software_design_patterns/tree/main/TdSE_workspace/semihosting) | <b>X</b> |
| <b>Cyclic Executive</b> | [cyclic_executive](https://github.com/JuanManuelCruz-FIUBA/tdse-software_design_patterns/tree/main/TdSE_workspace/cyclic_executive) | <b>X</b> |
| <b>Model Integration</b> | [model_integration](https://github.com/JuanManuelCruz-FIUBA/tdse-software_design_patterns/tree/main/TdSE_workspace/model_integration) | <b>X</b> |
