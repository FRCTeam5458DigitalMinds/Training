# Installing FRC Softwares
## FRC Control System
* Each year, FRC makes a new page with a control system filled with libraries to download, programming languages, 
new features, WPI Lib tools, and troubleshooting tips for that competition season. This document will include information on 
commonly used electronics and pointers on some of the most important parts of the FRC Control System.
* **Link to 2019 Control System:** 
https://wpilib.screenstepslive.com/s/4485

## Hardware and Software Components
### **Main Hardware Components**
* **National Instruments roboRIO**
  - roboRIO is the main FRC robot controller. The Integrated controller I/O includes a variety of communication protocols Ethernet, USB, as well as digital I/O and analog I/O channels used to connect to peripherals for sensing and control. For example, for the 2019 season, one peripheral we used was a smart camera called a Limelight to obtain vision during the Sandstorm period of the match when drivers could not 
    see the field.
* **PDP (Power Distribution Panel)**
  - The PDP is designed to distribute power from the battery to various robot components through auto-resetting circuit breakers and a small number of special function fused connections. The PDP provides 12V(V = voltage) connectors specifically for the roboRIO, as well as connectors for the Voltage Regulator Module and Pneumatics Control Module, which will be mentioned later on. It also includes a CAN interface for logging current, temperature, and battery voltage.
* **Pneumatics Control Module**
  - The PCM is a device that contains all of the inputs and outputs required to operate the pneumatics, including solenoids and the on board compressor. The PCM is enabled and disabled by the roboRIO over the CAN interface. The PCM contains an input for the pressure sensor and will control the compressor automatically when the robot is enabled.
* **Voltage Regulator Module**
  - The VRM is an independent module that is powered by 12 volts. The device is wired to a specific connector on the PDP. The module has multiple 12V and 5V outputs. The purpose of the VRM is to provide regulated power for the robot radio, custom circuits, and vision cameras.
* **Radio**
  - The radio is used as the robot radio to provide wireless communication functionality to the robot. It can also be configured as a bridge for use on the competition field. The robot radio should be powered by one of the 12V/2A outputs on the VRM and connected to the roboRIO controller over Ethernet.
* **Circuit Breaker**
  - The Circuit Breaker serves two roles on the robot: the robot power switch and a protection device for robot wiring and components. The circuit breaker is wired to the positive terminals of the robot battery and Power Distribution boards.
### Motor Controllers
* **Talon SRX**
  - The Talon SRX motor controller is a CAN-enabled "smart motor controller" from Cross The Road Electronics/VEX Robotics. The Talon SRX can be controlled over the CAN bus. When using the CAN bus control, this device can take inputs from limit switches and potentiometers, encoders, or similar sensors in order to perform advanced control.
* **Victor SPX**
  - The Victor SPX motor controller is a CAN or PWM controlled motor controller from Cross The Road Electronics/VEX Robotics. The device is made to allow easy connection to the roboRIO PWM connectors or a CAN bus chain. When controlled over the CAN bus, the device has a number of the closed loop features also present in the Talon SRX. The case is sealed to prevent debris from entering the controller.
  
### Main Software Components
* **Visual Studio Code**
  - Visual Studio Code is the supported programming environment for C++ and Java, two of the three supported coding languages used for programming an FRC robot. 




