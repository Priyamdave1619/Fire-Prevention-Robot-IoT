# 🔥 IoT Fire Prevention Robot

An autonomous, Arduino-based firefighting robot that detects flames, navigates toward the fire source while avoiding obstacles, and extinguishes it using an onboard water pump and servo-actuated sprayer nozzle.

**Author:** Priyam Dave

---

## 📖 Overview

Fire spreads rapidly and can be extremely dangerous to human life, especially in environments with high temperatures, toxic fumes, or explosive materials (e.g., petrochemical or chemical plants) where human firefighters cannot safely operate. This project addresses that gap with a low-cost, autonomous robot capable of:

- Detecting fire/flame sources using IR flame sensors
- Navigating autonomously and avoiding obstacles
- Approaching the fire and extinguishing it with a water spray mechanism
- Sweeping the spray nozzle via a servo motor to cover a wider area

This is an IoT/embedded systems project built on the **Arduino Uno** platform.

## 🎯 Problem Statement

It is often impossible for firefighting personnel to access a fire site due to extreme heat or the risk of explosion. Firefighting robots can operate in these hazardous conditions in place of human responders, reducing the risk of injury or death while helping to control the spread of fire in high-risk industrial environments.

## ⚙️ How It Works

1. Three digital flame sensors (front, left, and right) continuously scan the robot's surroundings for fire.
2. If no fire is detected, the robot drives forward.
3. If a flame is detected on the left or right, the robot steers toward that direction.
4. If a flame is detected directly ahead, the robot moves forward toward the source and flags that a fire has been found.
5. Once in range, the robot stops, activates the water pump, and sweeps the nozzle (mounted on a servo) back and forth to extinguish the flame.
6. After extinguishing, the pump switches off, the servo resets to its neutral position, and the robot resumes scanning for further fires.

## 🧩 Hardware Components

| # | Component | Purpose |
|---|-----------|---------|
| 1 | Arduino Uno | Main microcontroller running the control logic |
| 2 | Flame Sensors (x3) | Detect fire/flame in front, left, and right directions |
| 3 | L298N Motor Driver (H-Bridge) | Drives the two DC gear motors for movement |
| 4 | DC Gear Motors (x2) | Provide left/right wheel drive |
| 5 | 5V Relay Module | Switches the water pump on/off |
| 6 | Water Pump | Draws water from the tank to extinguish fire |
| 7 | Servo Motor | Sweeps the spray nozzle across the fire area |
| 8 | DC Motor + Fan/Sprayer assembly | Auxiliary motor for the spray/cooling mechanism |
| 9 | AAA Battery Pack | Power supply for the control and sensor circuit |
| 10 | Sound/IR Sensor Module | Auxiliary sensing input |

> The project's `.ino` filename references an MLX90614 IR temperature sensor; the current firmware implementation, however, relies on digital flame sensors for fire detection rather than the MLX90614.

## 🔌 Circuit Diagram

The wiring diagram (Fritzing) is included in this repository. Key connections:

- **Flame sensors** → Digital pins 8 (Front), 9 (Left), 10 (Right)
- **Left motor** → Digital pins 2 & 7 (direction), PWM pin 3 (speed)
- **Right motor** → Digital pins 4 & 12 (direction), PWM pin 5 (speed)
- **Water pump (via relay)** → Digital pin 6
- **Servo (nozzle sweep)** → Digital pin 11
- **L298N Motor Driver** → Powers both DC gear motors from the battery pack
- **Relay Module** → Switches pump power independently from logic-level signals

## 💻 Software Requirements

- [Arduino IDE](https://www.arduino.cc/en/software)
- `Servo.h` library (bundled with the Arduino IDE)

## 🚀 Getting Started

1. Assemble the hardware according to the circuit diagram (`Fire_v3.jpg`).
2. Install the Arduino IDE and ensure the `Servo` library is available.
3. Open `Fire_Fighting__mlx_90614.ino` in the Arduino IDE.
4. Select **Arduino Uno** as the board and the correct COM port.
5. Upload the sketch to the board.
6. Power the robot using the battery pack and place it in the test environment.

## 📁 Repository Contents

| File | Description |
|------|--------------|
| `Fire_Fighting__mlx_90614.ino` | Main Arduino firmware controlling sensors, motors, pump, and servo |
| `Fire_v3.jpg` | Fritzing circuit/wiring diagram for the robot |
| `Fire_Prevention_Robot_Priyam_Dave_.pptx` | Project presentation covering IoT concepts, problem statement, and component details |

## 🔮 Future Improvements

- Integrate an MLX90614 non-contact IR temperature sensor for more precise fire-source verification
- Add Wi-Fi/Bluetooth connectivity for remote monitoring and manual override
- Implement camera-based flame/smoke detection for improved accuracy
- Add a water-level sensor to monitor tank capacity
- Include an SMS/app-based alert system to notify personnel when a fire is detected

## 📜 License

This project was developed for academic purposes as part of a T.Y. B.Sc. (IT) coursework submission. Feel free to reference or build upon it for educational use.
