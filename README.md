# FIUBA - Electrónica - Taller de Sistemas Embebidos
## Software Design Patterns
### Contexto

<details>
<summary>Codificamos soluciones del tipo:</summary>

* **Bare Metal** (sin Sistema Operativo)
  * **Cyclic Executive**
    * *Super-Loop* (**Polling & Interrupts**)
    * *Update by Time Code* (**period = 1mS**)
    * **Event-Triggered Systems**
    * **Estructurada, Modular**
      * *Escrutar - Procesar - Actuar*
    * **Software Design Patterns** (*Statecharts*)
  * **STM32CubeIDE**, entorno de desarrollo integrado multi-OS en C/C++ para el desarrollo de código STM32.
  * **STM32CubeMX**, herramienta gráfica que simplifica la configuración de los productos STM32 y genera el código de inicialización correspondiente.
  * **HAL**, capa de abstracción de hardware de STM32, un software embebido que garantiza la máxima portabilidad en toda la gama STM32.
</details>

---

### Proyectos usados en los TP´s
| Name                 | STM32 Project Name                | OK |
| -------------------- | --------------------------------- | -- |
| Native STM32 Project | tdse-tp0_01-stm32_project         |    |
| Semihosting          | tdse-tp0_02-semihosting           |    |
| Cyclic Executive     | tdse-tp0_03-cyclic_executive      |    |
| Model Integration    | tdse-tp2_00-model_integration     |    |
| Porting C Code 01    | tdse-tp3_01-porting_c_code_solved |    |
| Porting C Code 02    | tdse-tp3_02-porting_c_code_solved |    |
| System Setup Menu    | tdse-tp3_03-system_setup_menu     |    | 