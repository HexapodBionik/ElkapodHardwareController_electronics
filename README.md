# Elkapod Hardware Controller module repository

Elkapod Hardware Controller is a module responsible for communication and control of hardware layer of Elkapod walking robot.

It abstracts components such as power supply module, servomotors, force sensors for main onboard computer - Raspberry Pi 5 - providing neat and standarized system interface.

![](images/ElkapodHardwareController_pcb_3d_isometric.png)

Electronic schematics as well as mechanical drawing are available in the `docs/` folder.

## Components
Elkapod Control Module is equipped with **STM32F446ZET6** microcontroller clocked at 180MHz which lets it handle even most demanding tasks.

### User interface
User may interfact with the board using dedicated **User button**.
Along with 6 controllable LEDs with different colors it makes prototyping and debugging process easier. 
The colors are:
- L1, L2 -  <span style="color: red;">**red**</span>
- L3, L4 -  <span style="color: rgb(50, 205, 50);">**green**</span>
- L5, L6 -  <span style="color: rgb(0, 171, 240);">**blue**</span>

### Sensors
#### Inertial measurement unit (IMU)
The module has **BMI055** Bosch sensortech inertial measurement unit used for measuring current orientation of the PCB, and, thus orientation of the Elkapod's main body.

Because it is vital to have a reliable and fast response to changes in the robot's orientation, the BMI055 is connected to the MCU using an SPI bus.

#### Temperature sensor
Temperature of the environment in which the module is located is measured using MCP9808-E/MS temperature sensor connected to the MCU using I²C bus.

### Connections



![](images/ElkapodHardwareController_pcb_3d_front_connectors_numbered.png)

The list of connections and their numbering according to the drawing above:
1. **KK power connector** - used for powering the module - power supply requirements (5V / 1.5A)
2. **IDC20 connector** - outputs PWM signals for 18 servomotors connected to the power supply board

<p align="center">
  <img src="images/elkapod_idc20_connector_pinout.drawio.svg"">
</p>

3. **USB type C connector** - used for powering the module and communication and diagnostics. Supports only USB 1.0 standard (transfer up to 12MBit/s)
4. **CAN 2.0 connectors** -  4 connectors for CAN communication using the 2.0 standard. It is important that the first device connected to the first upper connector is equipped with a 120Ω terminal resistor at the end of the line. Other devices should not have terminal resistors at their endpoints.
5. **SWD** connector - used for programming and debugging.

<p align="center">
  <img src="images/ekapod_swd_connector_pinout.drawio.svg"">
</p>

6. **GPIO connector 1** - generic use GPIO I/O

<p align="center">
  <img src="images/elkapod_gpio_connector1.drawio.svg"">
</p>

7. **SPI1 connector** - SPI bus connector used for high-speed communication with Raspberry Pi 5 

<p align="center">
  <img src="images/elkapod_spi_connector.drawio.svg"">
</p>

8. **GPIO connector 2** - SPI bus connector used for high-speed communication with Raspberry Pi 5 

<p align="center">
  <img src="images/elkapod_gpio_connector2.svg"">
</p>


9. **USART1 connector** - USART / UART connector used for peer - peer full-duplex communication with Raspberry Pi 5

<p align="center">
  <img src="images/elkapod_usart_connector.drawio.svg"">
</p>

10. **FAN connector** - KK connector for external FAN. Power parameters - 5V / up to 0.5A

<p align="center">
  <img src="images/elkapod_fan_pinout.drawio.svg"">
</p>


11. **Force Sensitive Resistor connectors** - connectors for FSR402 force sensitive resistors

## Mechanical drawing

<p align="center">
  <img src="images/ElkapodHardwareController_MechanicalDrawingTop.png"">
</p>

<p align="center">
  <img src="images/ElkapodHardwareController_MechanicalDrawingSide.png"">
</p>








