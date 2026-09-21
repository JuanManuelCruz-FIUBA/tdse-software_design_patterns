<b>STM32 Project ...</b>

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
