# STM32 Push Button Control Project

This project demonstrates how to configure a push button input on pin PA0 of an STM32 microcontroller and control an LED connected to pin PA1. Instead of using a physical push button, you can connect the PA0 pin directly to VCC (3.3V) or GND to simulate the button press.

## How It Works
- The program enables the clock for GPIO Port A and configures PA0 as an input pin.
- It reads the input state of PA0 continuously in a loop.
- When PA0 is grounded (0), the LED connected to PA1 is turned ON.
- When PA0 is connected to VCC (1), the LED is turned OFF.

### Key Code Highlights
1. **Clock Enabling for GPIO Port A:**

       *PAddress |= (1 << 0);  // Enable GPIOA clock

2. **PA0 as Input Configuration:**

        *PMode &= ~(3 << 0);    // Clear mode bits for PA0 (setting to 00 for input mode)

4. **Controlling the LED on PA1:**
   - If PA0 is grounded (button pressed), PA1 is set HIGH:

         *POut |= (1 << 1);  // Turn ON LED
     
   - If PA0 is connected to VCC (button released), PA1 is set LOW:

         *POut &= ~(1 << 1);  // Turn OFF LED

### Hardware Setup
- **Pin PA0**: Connect to a push button, VCC (3.3V), or GND. If using a button, one side should connect to GND, and the other to PA0.
- **Pin PA1**: Connect an LED with a suitable current-limiting resistor to ground.

### How to Modify the Code
You can easily modify this project by:
1. Changing the input pin from PA0 to any other GPIO pin by updating the `PIn` register.
2. Using the pin as either an input from VCC or GND by directly wiring it.
3. Adjusting the output behavior by modifying the `POut` register for different pins.

---

### Requirements
- STM32 microcontroller (such as STM32F0, STM32F1, etc.)
- STM32CubeIDE or any other development environment for STM32
- A push button or direct connections to VCC/GND
- An LED with a resistor

### Compilation and Usage
1. Clone this repository.
2. Open the project in STM32CubeIDE.
3. Compile and flash the code to your STM32 microcontroller.
4. Test the push button functionality by either pressing a button or connecting the pin to GND or VCC.

---

Feel free to edit the code for your specific needs or hardware configuration. Contributions and improvements are welcome!

--- 

This README should guide new users through the basic setup, functionality, and how to modify the project. Let me know if you'd like further changes!
