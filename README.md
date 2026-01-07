
# Autonomous Slot Car Control with Q-Learning
![Demo GIF](/Docs/demo.gif)
(the red car is autonomous)
## Overview
This project implements a **Q-learning–based control system** for an autonomous slot car. It serves as an educational and experimental platform to explore **reinforcement learning applied to embedded and cyber-physical systems**.

The system runs on **Raspberry Pis**, separating sensing and control to enable modular experimentation with learning algorithms, real-time control, and networked communication.

## Architecture
- **Sensor Node** (`capteur@kpteur`)  
  Collects sensor data from the slot car and sends it over the network.
- **Controller Node** (`pi@controlleur`)  
  Runs the Q-learning algorithm and controls the vehicle’s speed.

The nodes communicate over a local network using a simple client–server model.

## Setup

### Python environment
```bash
python3.11 -m venv myenv
source myenv/bin/activate
pip install -r requirements.txt
```

## Running the System

1.Connect both Raspberry Pis and your computer to the same Wi-Fi network.
2.SSH into both devices:
```bash
ssh username@hostname.local
```
3. Search for the **Sensor** IP
```bash
ifconfig
```
4.Start sensor server:
```bash
./LaunchServer <Sensor_IP> <Q_table>   #optional Q_table
```
4.Start controller client:
```bash
./LaunchClient-ip <Sensor_IP>
```

If everything is correctly connected, the slot car should start running autonomously.

## Testing and Debugging

Hardware and sensor tests are available in the **tests/** directory.
**tests/gpio.py** verifies motor control by increasing speed step by step.
Sensor values should remain in the range -0.5 to 14.7 during motion.

## Additional Notes
The repository includes wiring diagrams and component datasheets to facilitate replication and further experimentation.
