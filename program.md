# Astro Pi: first program

Connect the Raspberry Pi peripherals (keyboard, mouse, monitor, and power), and log in using the following login information:

  ```bash
  login: pi
  password: raspberry
  ```

  You will not see any text when typing the password; this is a security feature.
  
Load the graphical user interface by typing `startx`. Now, open Python 3 using `Menu > Programming > Python 3`. This will cause a Python Shell window to appear. Select `File > New Window`, and type in the following code:

  ```python
  from astro_pi import AstroPi
  ap = AstroPi()
  ap.show_message("Hello my name is Tim Peake")
  ```

Select `File > Save` and choose a file name for your program, then select `Run > Run module`. Your message should then scroll across the LED matrix in white text.

Why not try changing the message between the double quotation marks and running your code again? 
