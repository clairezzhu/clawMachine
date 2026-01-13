# clawMachine - DE Final Capstone Project
## Project Overview
This project is a durable, user-friendly claw machine specifically designed for elementary school students. The goal is to donate it to BLAST, an afterschool program at Los Peñasquitos Elementary School, providing a fun and interactive STEAM experience.

The claw machine is built around an Arduino Mega controlling multiple motors, a joystick, buttons, limit switches, and an LCD screen to deliver real-time feedback.

**Key Features:**
- X/Y/Z gantry system for precise claw movement
- Servo-controlled claw for gripping objects
- Stepper motors for X/Y movement and high-torque, repeatable positioning
- DC motors for optional continuous motion components
- Joystick and buttons for control
- LCD display for messages such as `INSERT COIN` and `GAME OVER`
- Safety features using limit switches to prevent over-travel


## Team Members
This project was completed as a collaboration between:
- Claire Zhu @clairezzhu (me)
- Lena Li @lenali26
- Nora Dunn @norad4309

All team members contributed to research, design, testing, and coding of the Arduino Claw Machine.


## Bill of Materials

| Component              | Quantity | Notes / Source                                 |
|------------------------|----------|-----------------------------------------------|
| Arduino Mega 2560      | 1        | Needed for sufficient I/O pins               |
| 16x2 LCD Screen        | 1        | Displays messages to user                     |
| NEMA 17 Stepper Motors | 4        | 2 for Y-axis, 1 X-axis, 1 Z-axis             |
| Servo Motor            | 1        | Controls claw grip                            |
| DC Motor               | 1        | Optional continuous rotation task             |
| Joystick               | 1        | Controls X/Y gantry                           |
| Buttons                | 3       | Start, coin, Z-axis control                   |
| Limit Switches         | 3       | For X/Y/Z travel limits                       |
| TIP-120 Transistors    | 18       | Control motor power safely                    |
| Resistors              | 18       | For transistor bases                           |
| Breadboard & Jumper Wires | N/A   | For testbed and prototyping                   |
| Power Supply           | N/A      | 5V logic for Arduino, separate motor supply  |

*Most of the important stuff is here, smaller parts such as screws aren't documented.*


## Motor & Component Testing
All motors and components were tested individually before integration:

| Component      | Test Summary          | Observations                                      |
|----------------|---------------------|--------------------------------------------------|
| Servo Motor    | Potentiometer control | Smooth motion, precise positioning, limited torque |
| DC Motor       | Limit switch control  | Continuous rotation, controlled start/stop via Arduino |
| Stepper Motor  | Step-based control    | High torque, precise positioning, slower for continuous motion |
| Joystick       | Analog X/Y           | Controlled gantry axes successfully             |
| Limit Switches | Digital input        | Effectively stops motion and prevents over-travel |

*Test codes are in the `setup/` folder.*


## Code Logic Outline
![IMG_2719](https://github.com/user-attachments/assets/3f407fc1-0cc0-458e-9331-9db8f59cf8e2)

## Code
Full code is still in progress. The completed project code will be available in the `code/` folder when done. 

## Wiring Diagram
<img width="778" height="572" alt="Screenshot 2026-01-12 at 11 44 56 PM" src="https://github.com/user-attachments/assets/abc8b0a4-ee54-4a0c-adc4-84afee7b8180" />


## Assembly Plan
1. Build testbed and validate individual components (motors, joystick, switches)
2. Assemble X/Y/Z gantry system and mount motors
3. Wire motors through TIP-120 transistors to Arduino Mega
4. Connect limit switches, joystick, buttons, and LCD screen
5. Verify shared ground connections and separate motor power supply
6. Upload Arduino code and test individual subsystems
7. Integrate all systems and run full game test


## References
Arduino Mega: https://store.arduino.cc/products/arduino-mega-2560-rev3

LCD: https://www.youtube.com/watch?v=s_-nIgo71_w&t=121s

Servo: https://www.youtube.com/watch?v=8-w_8izUO38

Stepper: https://www.youtube.com/watch?v=7spK_BkMJys&t=360s

Button: https://www.youtube.com/watch?v=VPGRqML_v0w

Joystick: https://www.youtube.com/watch?v=vo7SbVhW3pE&t=336s

Limit Switches: https://www.youtube.com/watch?v=6wuInF9Yw08
