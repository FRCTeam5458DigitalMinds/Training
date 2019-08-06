# Basics of C++  
## Commenting:  
Comments are lines in code that act as notes or headers, where they have no effect on the code.  
1. To make a single line comment type **//** followed by text. 
2. To make a multiple line comment type **/*** and to complete the comment type ***/**.

## Variables:  
Variables act as containers of values, similar to in math. There are different variables for different types of data, but the main ones we use are **int, float, and bool.**  
1. **int** is used to store an integer, a whole number that can be either positive or negative.  
2. **float** is used to store a positive or negative number with a decimal.  
3. **bool** is used to store a true/false value. (bool is short for boolean, but that doesn't really matter)  
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
In a robot, the code is put onto the roboRIO which is essentially a computer that controls other physical components on the bot. These components are treated in code as if they are variables, allowing you to give them names (for example: RightMotorOne). Almost every component is slightly different, so here are examples for the main components:  
  
- **Power Distribution Panel** (aka PDP) distributes power from the battery to various components:  
**frc::PowerDistributionPanel pdp{0};**  
- **Gyroscope** (aka Gyro) gives the bot rotational orientation, which helps it move in a straight line:  
**frc::ADXRS450_Gyro Gyro{};**  
*It's worth noting that the gyroscope could be a different type and therefore have a different name.*
- **Driver Station Controllers** are the three basic controllers we use: A race wheel for steering, a joystick for accellerating, and an Xbox controller for operating things such as intake:  
**frc::Joystick JoyAccel1{0}, Xbox{1}, RaceWheel{2};**  
*IMPORTANT: The numbers following each controller have to match the numbers given to each controller in Driver Station (software that reads controller input).*  
- **Motors** are not themselves programmable, so we use motor *controllers* to control them. There are two different types: *Talons* and *Victors*. We use two pieces of information to declare them, physical location and number:  
**WPI_TalonSRX RightMotorOne{5};**  
**WPI_VictorSPX LeftMotorTwo{7};**  
**VictorSPX CargoIntakeMotor{4};**  
First you put the appropriate type of controller, followed by its physical location, and then the number that is on the controller itself or the motor it is connected to.  

## 1st Section of Code - Include Statements:
Include files (aka includes) are header files that are stated at the beginning of the code. No code comes before include statements and they are not contained in brackets.
1. #include <iostream> instructs the preprocessor to include a section of standard C++ code, called header iostream, that allows it to perform input and output operations. These allow you to write code specific to a component, for example "#include <frc/Joystick.h>" allows you to write code to recognize joystick input.
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
  
## 2nd Section of Code - Declarations:  
This section is after includes and contains all of the component and value declarations. This section is not surrounded by brackets.    
  
## 3rd Section of Code - Void Functions:  
After adding all the includes and declarations, functions are created to run pieces of code on the bot. The two main functions we use are RobotInit and RobotPeriodic, although sometimes we use others. Each function contains code that is *called*, meaning run, at a specific time on the robot:  
**void Robot::RobotInit() {**  
*all code in these brackets is called once when the robot is connected*  
**}**  
  
**void Robot::RobotPeriodic() {**  
*all code in these brackets is called on every robot packet, no matter what mode*  
**}**  

## What to Put in Void Functions:  
Void functions make up the bulk of the programming we do but are usually created bit by bit. This is because not all parts are added on the bot at once, and usually you can't program ahead of time. The first function we write code in is RobotInit.  
### RobotInit Code:  
This code is run once when the robot is first connected and it sets up the bot before it is driven. The first lines of code are:  
**m_chooser.SetDefaultOption(kAutoNameDefault, kAutoNameDefault);  
  m_chooser.AddOption(kAutoNameCustom, kAutoNameCustom);  
  frc::SmartDashboard::PutData("Auto Modes", &m_chooser);**  
I have no idea why, but its the first lines in RobotInit for our past three bots, so if its not already there I would type it in or copy-paste it.  
All of our motors spin clockwise, so when they're on the left side of the bot, the wheels move forward, but since we face them the other way on the right side we have to inverse them to make sure that they also go forward. We inverse the motion of the motor by writing:  
**RightMotorOne.SetInverted(true);  
  RightMotorTwo.SetInverted(true);  
  RightMotorThree.SetInverted(true);**  
*Note that these three motors happened to be named right motor one, two, and three. You can use these names, or give your motors names of your choosing as long as they make sense when looking at the motors and their positions. It is also useful to make sure others can understand the names when looking at the robot.*
Each motor has to have its own line saying it is inversed, and its name has to match what you named it earlier in the declarations section (VS Code will probably tell you if its wrong but it's good to check on your own). Other pieces of code will also eventually be put into this function, such as setting Solenoids to false, but this is all you need to get started.  
### RobotPeriodic Code:  
This code is run on every robot packet, no matter the mode, meaning it will run whenever the bot is enabled in Driver Station. *Every lines in the code is executed several times a second while the bot is enabled,* which allows us to get the current position of our controllers, and then based on the information we can tell the bot what to do. To read the current position of the controllers, we store the controllers values in variables that we declared earlier:  
**double JoyY = -JoyAccel1.GetY();  
  double WheelX = RaceWheel.GetX();  
  double XboxRightAnalogY = Xbox.GetRawAxis(5);**  
JoyY is the input for accelerating and we inverse it because that way pushing the joystick forward will gives it a positive value. Racewheel is the angle that the wheel is turned at. XboxRightAnalogY is used to get values used in controlling things such as the height of the elevator. The 5 represents that axis Driver Station recognizes the right joystick as.**  
  
When we are programming the bot to drive, we take the input values and decide what to do based on them. For example, we don't want our bot to try to go straight and spin at the same, so we use **if statements.** If statements are very simple and they are formatted like:  
**if (inputOneIsTrue) {**  
*runs code for input one*  
**}  
else if (inputTwoIsTrue) {**  
*runs code for input two because input one was false, there can be several else if statements in a row*  
**}  
else {**  
*no input was true so this runs automatically*  
**}**  
Every statement has only one **if** to start it and one **else** to end it, but can have as many **else if** sections as you want in between. If one of the inputs is true, it no longer goes down the list. If none of the inputs is true, it runs the code in **else.**





