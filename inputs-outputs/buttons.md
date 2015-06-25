# Flight Buttons

The Astro Pi flight case as six general purpose buttons that you can also use in your programming. These are simply push buttons wired directly to GPIO pins in a pull up circuit, you can easily recreate this setup using a breadboard, some buttons and wires.

  ![](images/flight_buttons.jpg)
  
## GPIO mapping

The buttons are wired to the last six pins at the bottom of the GPIO header pins on the Pi.

  ![](images/buttons_GPIO.png)
  
  *Note the orientation of the pin diagram is with the Ethernet and USB ports facing downwards and the row of pins being on the right hand side of the Pi.*
  
This means that this set up cannot be exactly replicated if you're using an old Model A or B Pi. If this applies to you then you can just choose other pins but be sure to modify the pin numbering in your code so that it will work on a flight unit before you submit via the competition website.

These are the pin assignments:

- Top quad
  - UP: GPIO 26, pin 37
  - DOWN: GPIO 13, pin 33
  - LEFT: GPIO 20, pin 38
  - RIGHT: GPIO 19, pin 35
- Bottom pair
  - A (left): GPIO 16, pin 36
  - B (right): GPIO: 21, pin 40

You will need to comply with these in order for your code to *just work* on the flight hardware that Tim Peake will have on the ISS.
  
## How to detect a button press

GPIO pins can be set up as an input or an output. Output mode is used when you want to supply voltage to a device like an LED or buzzer. With input mode, a GPIO pin has a value that we can read in our code. If the pin has voltage going into it, the reading would be 1 (`HIGH`); if the pin was connected directly to ground (no voltage), the reading would be 0 (`LOW`).

The goal is to use a push button to switch voltage on and off for a GPIO pin, thus making the reading of the pin change in our code when we press the button.

When a GPIO pin is in input mode the pin is said to be *floating*, meaning that it has no fixed voltage level. That's no good for what we want, as the pin will randomly float between `HIGH` and `LOW`. For this job, we need to know categorically whether the button is up or down. So we need to fix the voltage level to `HIGH` or `LOW`, and then make it change only when the button is pressed.

The flight hardware buttons are all wired in a *pull up* configuration. Which means we pull the GPIO to `HIGH` and only short it to `LOW` when we press the button.

  ![](images/pull_up.png)
  
  In the diagram above we wire the GPIO pin to 3.3 volts through a large 10k ohm resistor so that it always reads `HIGH`. Then we can short the pin to ground via the button, so that the pin will go `LOW` when you press it.
  
  So `HIGH` means button *up* and `LOW` means button *down*.
  
Fortunately, the Raspberry Pi has all the above circuitry *built in* and we can select a pull up circuit in our code for each GPIO pin. This sets up some internal circuitry that is too small for us to see. So you can get away with just using two jumper wires here, although you're welcome to wire it up the way shown above if you wish.

All we now need to do is create the above circuit six times for each of the GPIO pins.
  
## Breadboard Wiring

The diagram below shows how to wire up the six buttons on a breadboard so that they match the flight hardware. As always, wire colour does not matter. The numbers next to each button indicate the GPIO number that they are connected to. Every button requires a one side to be connected to ground so that the HIGH pin can be shorted to LOW when the button is pressed, these are the black wires.

  ![](images/buttons_breadboard.png)
  
  ![](images/buttons_GPIO_small.png)

## Detect the button press in code

1. Open **Python 3** from a terminal window as `sudo` by typing:
  
  ```bash
  sudo idel3 &
  ```
  
1. A Python Shell window will now appear.
1. Select `File > New Window`.
1. Type in the following code:

  ```python
  import
  ```

1. Select `File > Save` and choose a file name for your program.
1. Then select `Run > Run module`.
  
