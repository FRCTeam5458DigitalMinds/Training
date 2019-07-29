# Basics of C++  
## Commenting:  
Comments are lines in code that act as notes or headers, where they have no effect on the code.  
1. To make a single line comment type **//** followed by text. 
2. To make a multiple line comment type **/*** and to complete the comment type ***/**.

## Variables:  
Variables act as containers of values, similar to in math. There are different variables for different types of data, but the main ones we use are **int, float, and bool.**  
1. **int** is used to store an integer, a whole number that can be either positive or negative.  
2. **float** is used to store a positive or negative number with a decimal.  
3. **bool** is used to store a true/false value. (Bool is short for boolean, but that doesn't really matter)  
4. As a side note, sometimes we use a double in place of a float if we want to store more decimal places (usually used for precise values).  

## Declaring a Variable:  
Declaring a variable basically means giving it a name and a value. The *syntax* or format is the same for all variables.  
Syntax: **type of variable** *space* **name for variable** *space* **=** *space* **value;**  
Examples:  
- int speed = 5;  
- float rotation = 2.25;  
- bool isActive = true;  
*Notice how all lines of code end in a semicolon, with the exception being comments.*  

## Declaring Physical Components:  
In a robot, the code is put onto the roboRIO which is essentially a computer that controls other physical components on the bot. These components are treated in code as if they are variables, allowing you to give them names (for example: RightMotorOne). Almost every component is slightly different, so here examples for the main components:  
  
- **Power Distribution Panel** (aka PDP) distributes power from the battery to various components:  
frc::PowerDistributionPanel pdp{0};  
- **Gyroscope** (aka Gyro) gives the bot rotational orientation, which helps it move in a straight line:  
frc::ADXRS450_Gyro Gyro{};  
*It's worth noting that the gyroscope could be a different type and therefore have a different name.*
- **Driver Station Controllers** are the three basic controllers we use: A race wheel for steering, a joystick for accellerating, and an Xbox controller for operating things such as intake:  
frc::Joystick JoyAccel1{0}, Xbox{1}, RaceWheel{2};  
*IMPORTANT: The numbers following each controller have to match the numbers given to each controller in Driver Station (software that reads controller input).*  
- **Motors** are not themselves programmable, so we use motor *controllers* to control them. There are two different types: *Talons* and *Victors*. We use two pieces of information to declare them, physical location and number.
- WPI_TalonSRX RightMotorOne{5};
- WPI_VictorSPX LeftMotorTwo{7};
- VictorSPX CargoIntakeMotor{4};
First you put the appropriate type on controller, followed by its physical location, and then the number that is on the controller itself or the motor it is connected to.  

## Includes:
Includes are header files that are stated at the beginning of the code.
1. #include <iostream> instructs the preprocessor to include a section of standard C++ code, called header iostream, that allows it to perform input and output operations.
### Include Statement Examples:
- #include <string>
- #include <sstream>
- #include <Robot.h>
- #include <iostream>
- #include <WPILib.h>
- #include <stdlib.h>
- #include <frc/Timer.h>
- #include <TimedRobot.h>
- #include <frc/Joystick.h>
- #include <ctre/Phoenix.h>
- #include <frc/ADXRS450_Gyro.h>
- #include <frc/Solenoid.h>
- #include <frc/smartdashboard/SmartDashboard.h>
  
## Void Function

