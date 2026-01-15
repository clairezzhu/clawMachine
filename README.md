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


## User Interface
1. LCD displays `INSERT COIN`
2. Coin button starts the game
3. Joystick controls X/Y movement
4. Button lowers claw (Z-axis)
5. Servo closes claw
6. Claw retracts and returns to drop zone
7. LCD displays `GAME OVER`


## Bill of Materials

| Component              | Quantity | Notes / Source                                 |
|------------------------|----------|-----------------------------------------------|
| Arduino Mega 2560      | 1        | Needed for sufficient I/O pins               |
| 16x2 LCD Screen        | 1        | Displays messages to user                     |
| NEMA 17 Stepper Motors | 4        | 2 for Y-axis, 1 X-axis, 1 Z-axis             |
| Servo Motor            | 1        | Controls claw grip                            |
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
| Stepper Motor  | Step-based control    | High torque, precise positioning, slower for continuous motion |
| Joystick       | Analog X/Y           | Controlled gantry axes successfully             |
| Limit Switches | Digital input        | Effectively stops motion and prevents over-travel |

*Test codes are in the `setup/` folder.*

**Note:** Stepper motors were selected for the X and Y axes due to their precise step-based positioning, while a servo motor was used for the claw to provide controlled angular motion for gripping objects.


## Code Logic Outline
![IMG_2719](https://github.com/user-attachments/assets/3f407fc1-0cc0-458e-9331-9db8f59cf8e2)


## Code
Full code is still in progress as shown in the `code/` folder The completed project code will be updated in the same file when done. 


## Wiring Diagram
All motors are driven through TIP-120 transistors, allowing the Arduino Mega to safely control higher-current loads. Shared ground connections ensure consistent logic levels across the system, while signal wiring was routed to minimize noise and interference.
<img width="778" height="572" alt="Screenshot 2026-01-12 at 11 44 56 PM" src="https://github.com/user-attachments/assets/abc8b0a4-ee54-4a0c-adc4-84afee7b8180" />


## Mechanical Design
Note: We're still finalizing the gantry plan. We're leaning towards a **Cartesian Gantry** with linear-rods. I've made a decision matrix comparing some possible ways:


**Rating Scale:**  
1 = Poor / Very Difficult  
5 = Excellent / Ideal  

| Gantry Type | Mechanical Simplicity | Precision | Safety for Kids | Ease of Control (Code) | **Total ( /25 )** |
|------------|----------------------|-----------|------------------|------------------------|------------------|
| Cartesian (X/Y/Z) | 5 | 5 | 5 | 5 | **20** |
| CoreXY | 2 | 5 | 2 | 2 | 11 |
| H-Bot | 3 | 3 | 3 | 3 | 12 |
| Polar (Rotational + Radial) | 3 | 3 | 2 | 3 | 11 |
| Cable-Driven | 2 | 2 | 2 | 2 | 8 |
| SCARA Arm | 1 | 3 | 1 | 1 | 6 |

*While higher-performance systems such as CoreXY scored well in precision, their increased mechanical and software complexity made them less suitable for an educational claw machine.*


## CAD Designs
The claw machine enclosure and internal layout were designed in CAD to ensure proper component fit and structural stability. 

Key design considerations included:
- Adequate clearance for motors, wiring, and connectors
- Structural support for the gantry system and moving components
- Ventilation and access for maintenance

Below is the CAD model of the control box:

<img width="477" height="526" alt="Screenshot 2026-01-14 at 8 44 22 PM" src="https://github.com/user-attachments/assets/fb1ac2c8-b5d1-421b-8e05-618fc4cd677b" />


## Assembly Plan
1. Build testbed and validate individual components (motors, joystick, switches)
2. Assemble X/Y/Z gantry system and mount motors
3. Wire motors through TIP-120 transistors to Arduino Mega
4. Connect limit switches, joystick, buttons, and LCD screen
5. Verify shared ground connections and separate motor power supply
6. Upload Arduino code and test individual subsystems
7. Integrate all systems and run full game test


## Technical Challenges
**Challenge 1:**
The machine needed to be safe for young users while remaining functional.

**Solution:**
Motor speeds were limited in software, pinch points were minimized mechanically, and the system was designed to fail safely by stopping motion when limits are triggered.


**Challenge 2:**
Without safeguards, motors could drive the gantry beyond physical limits, risking damage.

**Solution:**
Limit switches were installed on the X, Y, and Z axes. The code continuously monitors these switches and immediately stops or reverses motor movement when a limit is reached.


**Challenge 3:**
The Arduino Mega’s I/O pins cannot safely supply the current required by motors and other high-power components. Directly driving motors from the Arduino risked exceeding current limits, which could permanently damage the microcontroller or cause unstable behavior.

**Solution:**
To protect the Arduino, TIP-120 transistors were used as power switches between the Arduino and the motors. The Arduino controls the transistor bases using low-current digital signals, while the transistors handle the higher motor currents from an external power supply. This design isolates the microcontroller from high-current loads, prevents overcurrent conditions, and ensures reliable operation.



## Skills Demonstrated
- Embedded systems programming (Arduino/C++)
- Motor control (stepper & servo)
- Hardware & software integration
- Electrical safety and power management
- Mechanical design and prototyping
- Team collaboration and documentation


## Potential Improvements

Future improvements could include adding adjustable difficulty levels or closed-loop motor control to improve positioning accuracy. Additional safety features such as emergency stop buttons could also be added.


## Team Members
This project was completed as a collaboration between:
- Claire Zhu @clairezzhu (me)
- Lena Li @lenali26
- Nora Dunn @norad4309

All team members contributed to research, design, testing, and coding of the Arduino Claw Machine.


## References
Arduino Mega: https://store.arduino.cc/products/arduino-mega-2560-rev3

LCD: https://www.youtube.com/watch?v=s_-nIgo71_w&t=121s

Servo: https://www.youtube.com/watch?v=8-w_8izUO38

Stepper: https://www.youtube.com/watch?v=7spK_BkMJys&t=360s

Button: https://www.youtube.com/watch?v=VPGRqML_v0w

Joystick: https://www.youtube.com/watch?v=vo7SbVhW3pE&t=336s

Limit Switches: https://www.youtube.com/watch?v=6wuInF9Yw08
