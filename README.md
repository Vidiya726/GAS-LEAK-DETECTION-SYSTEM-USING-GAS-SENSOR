# GAS-LEAK-DETECTION-SYSTEM-USING-GAS-SENSOR

## Aim:
	To measure the air quality using Gas Sensor  MQ-2 with Arduino UNO Board/ESP-32 using Tinker CAD.

## Hardware / Software Tools required:
	PC/ Laptop with Internet connection
  Tinker CAD tool (Online)
	Arduino UNO Board/ESP-32
  Gas sensor (MQ-2)
	
## Circuit Diagram:

 <img width="1029" height="574" alt="Screenshot 2026-05-30 132433" src="https://github.com/user-attachments/assets/47de9028-993d-4523-b7fa-c42025fcdcfd" />

## Theory :
 The Arduino Uno is powered by the ATmega328P, an 8-bit microcontroller that runs at 16 MHz. It has 32 KB of flash memory, 2 KB of SRAM, and 1 KB of EEPROM. The board 
has 14 digital I/O pins (of which 6 can be used as PWM outputs) and 6 analog input pins. These pins allow the board to interface with various sensors, actuators, and other devices.
The Arduino Uno can be powered via a USB connection or an external power supply. The board has a built-in voltage regulator to manage power from 7 to 12 volts.
The board is programmable using the Arduino IDE (Integrated Development Environment), which supports a simplified version of C/C++. The code, known as a "sketch," is uploaded to the board via a USB connection. The Uno has a USB-B port, which is used for communication with a computer. The USB connection also powers the board when connected. The board includes a reset button that restarts the microcontroller, useful during programming and troubleshooting. The In-Circuit Serial Programming (ICSP) header allows for low-level programming of the microcontroller or firmware updates. The Uno has a built-in LED on pin 13, commonly used for simple tests and debugging.

## Procedure:
### Step 1: Set Up the Tinkercad Environment

1. **Log in to Tinkercad**
   - Open Tinkercad in your web browser.
   - Log in to your account.

2. **Create a New Circuit**
   - In the Tinkercad dashboard, click **Circuits**.
   - Select **Create New Circuit**.

### Step 2: Add Components to the Circuit

1. **Arduino Uno**
   - Drag an Arduino Uno board from the components panel onto the workspace.

2. **Gas Sensor**
   - Search for the MQ-2 Gas Sensor in the components panel.
   - Drag it into the workspace.

3. **Breadboard**
   - Drag a small breadboard into the workspace to help with wiring connections.

4. **Resistor (Optional)**
   - A resistor may not be necessary for this simple setup.
   - You may include one for more accurate readings.

5. **Wires**
   - Use wires to connect the components.

### Step 3: Connect the MQ-2 Gas Sensor to Arduino

#### MQ-2 Pin Connections

- **VCC** → Arduino **5V**
- **GND** → Arduino **GND**
- **A0 (Analog Output)** → Arduino **A0**
- **D0 (Digital Output - Optional)** → Arduino **D2**

#### Breadboard Wiring

- Connect the **VCC** pin of the MQ-2 sensor to the breadboard's 5V rail connected to Arduino 5V.
- Connect the **GND** pin of the MQ-2 sensor to the breadboard's ground rail connected to Arduino GND.
- Connect the **A0** pin of the MQ-2 sensor to Arduino analog pin **A0**.
- Optionally connect the **D0** pin of the MQ-2 sensor to Arduino digital pin **D2** for threshold detection.

### Step 4: Write the Arduino Code

1. Click the **Code** button at the top of the Tinkercad workspace.

2. Ensure the editor is in **Text Mode**.

3. Enter the Arduino code for the MQ-2 gas sensor.

### Step 5: Simulate the Circuit

1. Click **Start Simulation** to run the circuit and code.

2. Open the **Serial Monitor** to view the gas sensor readings.

### Step 6: Troubleshoot and Refine

1. Verify that all wiring connections are correct.

2. Modify the code if necessary to improve accuracy or change the output format.

### Step 7: Save Your Work

1. Click **Stop Simulation** to end the simulation.

2. Click **Save** to store the circuit design and code for future use.

## Program:
```
#include <LiquidCrystal.h>

// initialize the library with the numbers of the interface pins
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  Serial.begin(9600);

  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);

  pinMode(13, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(6, OUTPUT);
}

void loop() {
  int gas_data;

  gas_data = analogRead(A0);

  lcd.setCursor(00, 00);
  lcd.print("Gas :");

  lcd.setCursor(6, 00);
  lcd.print(gas_data);

  if (gas_data > 500) {
    digitalWrite(13, HIGH);
    delay(100);
    digitalWrite(13, LOW);

    lcd.setCursor(00, 1);
    lcd.print("DANGER");
  }
  else if (gas_data > 400) {
    digitalWrite(6, HIGH);
    delay(100);
    digitalWrite(6, LOW);

    lcd.setCursor(00, 1);
    lcd.print("WARNING");
  }
  else {
    digitalWrite(7, HIGH);

    lcd.setCursor(00, 1);
    lcd.print("SAFE");
  }

  Serial.println(gas_data);

  delay(100);
  lcd.clear();
}
```
## Output:

 <img width="729" height="371" alt="Screenshot 2026-05-30 132257" src="https://github.com/user-attachments/assets/929951d4-62cf-422d-b23d-f2476b8d1c74" />
 
## Result:
The quality of air is measured using Gas Sensor MQ-2 with Arduino UNO Board/ESP-32 using 
Tinker CAD Verified Successfully.
