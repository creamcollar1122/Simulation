# ESP32 LED Control via HTTP Server (Wokwi Simulation)

This project demonstrates how to control LEDs connected to an ESP32 using an HTTP server. The simulation runs on the Wokwi platform and toggles LEDs based on user input (ON/OFF buttons) in a web interface.  

### Features:
- Toggle LEDs using a web-based interface.
- Simulate Wi-Fi scanning and HTTP server functionality.
- Visual feedback via LEDs in the Wokwi simulation.

This setup can be simulated using the [Wokwi Simulator](https://wokwi.com/projects/320964045035274834).

## Circuit Diagram

The circuit consists of three LEDs connected to the Arduino Uno through resistors. The LEDs turn on in sequence, creating the flip-flop effect.

![Circuit Diagram](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/circuit-diagram.png)

[**View the project on Wokwi**](https://wokwi.com/projects/320964045035274834)


### To download the entire project, including the circuit setup and code files:
Click **Download Project ZIP** from the top left corner on Wokwi.

---

## Steps to Build

### 1. Create a New GitHub Repository

- Go to [GitHub](https://github.com/) and create a new repository.
- Upload the following files:
  - `diagram.json`
  - `libraries.txt`
  - `esp32-http-server.ino`
  - `wokwi-project.txt`

### 2. Set Up GitHub Codespaces

If you want to use GitHub Codespaces to build and simulate the project:

- Create a **new Codespace** from the repository's main branch.
- You will see the uploaded files in the GitHub explorer.

![Explorer](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/explorer.png)

### 3. Organize the Files

- Create a folder named `src` in your repository.
- Move the `esp32-http-server.ino` file into this folder for better organization.

### 4. Add Necessary Configuration Files

In the root directory, add the following two configuration files for proper simulation.

#### `wokwi.toml` Configuration File

```
[wokwi]
version = 1
elf = ".pio/build/esp32/firmware.elf"
firmware = ".pio/build/esp32/firmware.bin"

# Forward HTTP requests from localhost to port 80 on the simulated ESP32
[[net.forward]]
from = "localhost:8180"
to = "target:80"

# Specify custom peripherals or connections in your Wokwi simulation
[[peripherals]]
id = "led"
type = "led"
pin = 2

```

### `platformio.ini` Configuration File

```
; PlatformIO Project Configuration File
;
;   Build options: build flags, source filter
;   Upload options: custom upload port, speed and extra flags
;   Library options: dependencies, extra library storages
;   Advanced options: extra scripting
;
; Please visit documentation for the other options and examples
; https://docs.platformio.org/page/projectconf.html

[env:esp32]
platform = espressif32
framework = arduino
board = esp32dev
```
![Folder Constraints](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/folder-constraints.png "Folder Constraints")

### 5. Install Necessary Extensions

Make sure the following extensions are installed in your Codespace or local environment:

1. **Wokwi Simulator** – To simulate your Arduino project.
2. **Arduino** – To handle Arduino code and libraries.
3. **C/C++** – For proper code syntax highlighting and IntelliSense.
4. **PlatformIO IDE** – To manage build configurations and dependencies.

![Extensions](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/extension.png?raw=true)

Once the extensions are installed, PlatformIO will begin configuring your environment. You may see a configuration loading message.

![PlatformIO Configuring](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/reload.png?raw=true)

## Integration Steps

1. Place the `platformio.ini` and `wokwi.toml` files in your project root directory.

2. Build the firmware in PlatformIO:
   ```bash
   pip install platformio
   pio run

- Use the generated firmware files (.elf and .hex) in the wokwi.toml configuration.
- Run the Wokwi simulator and test your setup.

### 6. Build the Project
Click the commit button to ensure the changes are confirmed.

![commit](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/commit.png?raw=true)

After PlatformIO finishes configuring, click **Build** to compile the code.

![PlatformIO Build](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/build.png?raw=true)

If everything is set up correctly, you should see a build success message.

![Build Output](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/build-output.png?raw=true)

### 7. Enter Your License Key

When prompted, enter your Wokwi license key to continue the simulation.
Once your Licence key is correct the below message showcased
![licence-key](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/licence-key.png?raw=true)

**Sample Reference Key:**
```
JnU9NDExNDMzOTE2NzAwNDgxNTM3Jm49QVJVVkkrQiZlPWFydXZpYmFsYW11cnVnYW4lNDBnbWFpbC5jb20meD0yMDI0MTIxOQDUGJjn9WS08KhQ1wqeo5hdL3e7YQBWpa2jQn5fFH5vC02cUWu561snpiR9XLkR_StBSXRv7j3DL34qMqmueEKSN3mG_P1QVlYK0UlhOScWEhgT1ZD3844r_S3IBcFKxAvg4fIbsX8388iPvgSCrBQNXzjxVS_Pk_PKUtc0eGsxY3pAfdNvl5MTMKuzIjneS8q3jYunrtkvMA30tCj_SZbCGj5eHJGlYkZ9IiSvAegqTkx2mBdDnhph0EyVVuYcITF9wEBAYKRQVisTNCtw_P8SSGZNcBZM4rCdeponWyQzYGzGu5_Sw3U51ZXB7_Sb0k7UAEncvYNuITgr85J_S2C3cwmG7r7z_SL

```

### 8. Start the Simulation
Once your Wokwi license is verified, start the simulation to see the ESP32 controlling LEDs via Wi-Fi.

Expected Simulation Behavior:
- The LEDs toggle in a flip-flop pattern or respond to your Arduino code logic.
- Ensure the wokwi.toml file is correctly configured with proper paths for peripherals, firmware, and ELF files.

**Screenshot: Starting the Simulation**

![Start Simulation](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/start-simulation.png?raw=true)

---

## CHECK OUTPUT

When the simulation starts, the ESP32 scans for Wi-Fi networks and displays them in the terminal. Once connected, it sets up an HTTP server to toggle LED states.

1. Output Screenshots:
Terminal showing scanned networks and HTTP server setup

![Output](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/output-.png?raw=true)

2. Web Interface with ON/OFF buttons

Open the browser using the provided link in the terminal.
You will see a simple interface with buttons to control the LEDs.
 
![Output-On](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/two-led.png?raw=true)

Testing the Web Interface:

Turn ON LED 1: Click the "ON" button to toggle the first LED.

![output-One-led](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/led-1-on.png)

Here we see the output in the terminal

![output-terminal](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/output-ON.png)

Terminal Output: The terminal logs the button click and LED state changes.

![Output-On](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/two-led.png?raw=true)

Additional Test Cases:
Toggle both LEDs multiple times and observe the interface and terminal logs.
![Output-On](https://github.com/Aruvi-B/http-server-wokwi/blob/main/Images/output-ONN.png?raw=true)



**It is working................**
---

## Conclusion

- Congratulations! You have successfully built and simulated your **ESP32 LED Control via HTTP Server (Wokwi Simulation)**.
---
