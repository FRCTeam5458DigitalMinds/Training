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
Syntax: **type of variable** *space* **name for variable** *space* **=** *space* **vaule;** 
Examples:  
- int speed = 5;  
- float rotation = 2.25;  
- bool isActive = true;  
*Notice how all lines of code end in a semicolon, with the exception being comments.*

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

