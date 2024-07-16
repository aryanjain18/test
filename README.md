## Smart Light Bulb Using Arduino

This project aims to create a smart light bulb that can be controlled using an Arduino. The smart light bulb will have functionalities such as on/off control, brightness adjustment, and color change.

### Table of Contents
1. [Stuff Used](#stuff-used)
2. [Steps to Assemble](#steps-to-assemble)
3. [Documentation](#documentation)
4. [Troubleshooting](#troubleshooting)

### Stuff Used
#### Hardware
- Arduino Uno
- RGB LED or Smart LED Bulb (such as an addressable RGB LED strip)
- MOSFETs or Transistors (if using high-power LEDs)
- Resistors (220 ohms for LED)
- Breadboard and jumper wires
- Power supply (depending on the LED power requirements)
- Push buttons (optional for manual control)

#### Software
- Arduino IDE
- Necessary libraries (e.g., `FastLED` or `Adafruit_NeoPixel`)

### Steps to Assemble
1. **Circuit Assembly:**
   - Connect the RGB LED to the Arduino. If using a smart LED strip, connect the data pin to one of the Arduino digital pins (e.g., pin 6).
   - Use MOSFETs or transistors to control the high-power LEDs. Connect the gate of the MOSFET to the Arduino, the source to ground, and the drain to the LED's negative terminal. Connect the LED's positive terminal to the power supply.
   - Connect resistors in series with each color channel of the RGB LED to limit the current.
   - If using push buttons for manual control, connect them to the digital pins of the Arduino with pull-down resistors.

2. **Arduino Code:**
   - Open the Arduino IDE and install the necessary libraries (`FastLED` or `Adafruit_NeoPixel`).
   - Write the code to control the LED. Below is a simple example using the `FastLED` library:

```cpp
#include <FastLED.h>

#define LED_PIN 6
#define NUM_LEDS 1 // Adjust if using more LEDs

CRGB leds[NUM_LEDS];

void setup() {
  FastLED.addLeds<NEOPIXEL, LED_PIN>(leds, NUM_LEDS);
}

void loop() {
  // Example: cycle through colors
  for (int hue = 0; hue < 255; hue++) {
    leds[0] = CHSV(hue, 255, 255);
    FastLED.show();
    delay(10);
  }
}
```

3. **Upload Code:**
   - Connect the Arduino to your computer via USB.
   - Select the appropriate board and port in the Arduino IDE.
   - Upload the code to the Arduino.

4. **Testing:**
   - Power up the circuit.
   - The LED should start cycling through different colors.

### Documentation

#### Circuit Diagram
[Include a simple circuit diagram here.]

#### Code Explanation
- **Libraries:** We use the `FastLED` library to control the LED strip. 
- **Pin Definitions:** `LED_PIN` is the pin connected to the data input of the LED strip.
- **Setup Function:** Initializes the LED strip.
- **Loop Function:** Cycles through colors by changing the hue value.

#### Functionality
- **On/Off Control:** You can add a push button to toggle the LED on and off.
- **Brightness Adjustment:** Modify the `brightness` parameter in the `CHSV` function.
- **Color Change:** The `hue` parameter in the `CHSV` function determines the color.

### Troubleshooting

#### Common Issues
1. **LEDs Not Lighting Up:**
   - Check all connections, especially the data pin connection.
   - Ensure the power supply is sufficient for the LEDs.

2. **LEDs Flickering:**
   - Ensure a common ground between the Arduino and the LED power supply.
   - Check for loose connections.

3. **Incorrect Colors:**
   - Verify the LED type in the code matches your hardware.
   - Check the wiring of the RGB channels.

4. **Arduino Not Detected:**
   - Ensure the correct board and port are selected in the Arduino IDE.
   - Try a different USB cable or port.

#### Tips
- Use external power for high-power LEDs to avoid overloading the Arduino.
- Always use resistors with LEDs to prevent damage.
- Test each component individually before full assembly.

This guide should help you assemble and troubleshoot your smart light bulb project using Arduino. If you have further questions or need assistance, feel free to reach out for support!
