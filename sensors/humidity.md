# Humidity

## What does humidity mean?

1. Look at the image below and listen to your teacher explain what humidity is and the two different ways that it can be measured.

  - Absolute (grams of water per cubic meter of air)
  - Relative (percentage of actual water vapour present compared to the maximum possible)

  ![](images/condensation.jpg)

## what is the current humidity?
1. Open **Python 3** from a terminal window as `sudo` by typing:
  
  ```bash
  sudo idel3 &
  ```
1. Select `File > New Window` and enter the following code:

  ```python
  from astro_pi import AstroPi
  
  ap = AstroPi()
  ap.clear()
  
  humidity = ap.get_humidity()
  print(humidity)
  ```

1. Select `File > Save` and choose a file name for your program.
1. Select `Run > Run module`.
1. If you see the error `Humidity Init Failed, please run as root / use sudo` (look on the last line of the message in red) it means you haven't followed the instructions above. Close everything and go back to step 3.
1. You should see something like this:

  ```bash
  Humidity sensor Init Succeeded
  34.6234588623
  ```

1. Just before the `print(humidity)` line add this line below:

  ```python
  humidity = round(humidity, 1)
  ```

1. You should now see something like this (without all the numbers after the decimal point):

  ```bash
  Humidity sensor Init Succeeded
  34.6
  ```
1. It would be good to monitor the humidity as it changes, so let's put our code into a `while` loop and run it again.

  ```python
  while True:
      humidity = ap.get_humidity()
      humidity = round(humidity, 1)
      print(humidity)
  ```
1. Exhale slowly onto the sensors. The water vapour in your breath should cause the readings to jump up.
1. Keep watching and it should slowly fall back to the background humidity of the room.
1. Press `Ctrl - C` to stop the program.
1. The next task would be to show the humidity on the LED matrix in some way. 

*Note: Please note that it is possible to get a value higher than 100 from the humidity sensor.*
