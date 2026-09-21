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
<summary><b>STM32 Project ...</b></summary>

  * Proyecto generado con **STM32CubeIde** (*STM32CubeMX*), mediante la opción *File > New > STM32 Project*, que permite iniciar desde cero un archivo de proyecto, seleccionando el *chip* o la *placa* que se va a usar (en nuestro caso la *placa*).
  * Contiene una estructura de directorios de base (ver *árbol de directorios* al pie) y  entre otros, archivos de encabezamiento (```.h```), de código fuente (```.c, .s```), de comentario (```.txt```) y de configuración ```.ioc```.
    * El *árbol de directorios*, contiene la carpeta *Core*, destinada a almacenar código fuente y archivos de configuración creados por el usuario o generados por *STM32CubeMX* para hacer funcionar el microcontrolador.
    * En éstos archivos, el usuario debe insertar su código estrictamente dentro de los bloques de comentarios ```USER CODE``` que genera automáticamente el entorno.
      * Si escribes código fuera de estas secciones, *STM32CubeMX* borrará todo tu trabajo la próxima vez que regeneres el proyecto desde la interfaz gráfica.  

```
stm32_project
├───.settings
├───Core
│   ├───Inc
│   ├───Src
│   └───Startup
└───Drivers
    ├───CMSIS
    │   ├───Device
    │   │   └───ST
    │   │       └───STM32F1xx
    │   │           ├───Include
    │   │           └───Source
    │   │               └───Templates
    │   └───Include
    └───STM32F1xx_HAL_Driver
        ├───Inc
        │   └───Legacy
        └───Src
```

</details>

<details>
<summary><b>Semihosting ...</b></summary>

  * Semihosting es un mecanismo que permite al microcontrolador usar los recursos de tu computadora (como la pantalla, el teclado o archivos), a través de la placa de depuración.
    * Sirve para ver mensajes de funciones como ```printf()``` directamente en la consola del IDE sin configurar un puerto físico, requiere de:
      * Configurar el linker para agregar una biblioteca (y sus opciones de linkeo).
      * Excluir un archivo de la compilación para evitar conflictos con las llamadas al sistema del semihosting.
      * Configurar el depurador (*OpenOCD*).
      * Modificar el código fuente  código en el archivo (```main.c```), como se detalla a continuación.
  
```
/* USER CODE BEGIN Includes */

#include "stdio.h"

/* USER CODE END Includes */

. . .

/* USER CODE BEGIN 0 */

extern void initialise_monitor_handles(void);

/* USER CODE END 0 */
  . . .

  /* USER CODE BEGIN 1 */

  initialise_monitor_handles();

  /* USER CODE END 1 */
  . . .

  /* USER CODE BEGIN 2 */

  printf("Hello World!\n");

  /* USER CODE END 2 */
```

</details>

<details>
<summary>Software Design Patterns:</summary>

  * Los patrones de diseño (**design patterns**) son soluciones habituales a problemas comunes en el diseño de software. Cada patrón es como un plano que se puede personalizar para resolver un problema de diseño particular de tu código.

</details>

---

### Proyectos de referencia
| Proyecto          | Link |   |
| :---------------- | :----| - |
| <b>STM32 Project</b> | [stm32_project](https://github.com/JuanManuelCruz-FIUBA/tdse-software_design_patterns/tree/main/TdSE_workspace/stm32_project) | X |
| <b>Semihosting</b> | [semihosting](https://github.com/JuanManuelCruz-FIUBA/tdse-software_design_patterns/tree/main/TdSE_workspace/semihosting) | X |
| Cyclic Executive  | tdse-tp0_03-cyclic_executive      |   |
| Model Integration | tdse-tp2_00-model_integration     |   |
| Porting C Code 01 | tdse-tp3_01-porting_c_code_solved |   |
| Porting C Code 02 | tdse-tp3_02-porting_c_code_solved |   |
| System Setup Menu | tdse-tp3_03-system_setup_menu     |   | 
