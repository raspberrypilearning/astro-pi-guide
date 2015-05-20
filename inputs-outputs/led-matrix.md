# LED Matrix

## Simple Colour mixing

  ![](images/additive_color_mixing.png)

1. In a new **Python 3** window, type in the following code:

  ```python
  from astro_pi import AstroPi
  ap = AstroPi()
  r = 255
  g = 255
  b = 255
  ap.clear((r, g, b))
  ```

1. Select `File > Save` and choose a file name for your program.
1. Then select `Run > Run module`.
1. The LED matrix will then go bright white.
1. The variables `r`, `g` and `b` represent the primary colours red, green and blue. The numbers they contain specify how bright each colour should be. They can be between zero and 255. So in the above code we've asked for maximum red, green and blue so the result is white.
1. Change the values to specify 255 red but zero green and blue. Then run the code again.
1. What other colours can you make?

## Changing foreground and background colours

1. This colour mixing system is used all throughout the Astro Pi programming module.
1. Open the code file from the previous lesson and modify it like so:

  ```python
  from astro_pi import AstroPi
  ap = AstroPi()
  ap.show_message("Hello my name is Tim Peake", text_colour=(255, 0, 0))
  ```

  Note the addition of the syntax `, text_colour=(255, 0, 0)`.
  
  Don't forget the comma!
  
1. You can also modify the background colour for the message like so:

  ```python
  from astro_pi import AstroPi
  ap = AstroPi()
  ap.show_message("Hello my name is Tim Peake", text_colour=(255, 0, 0), back_colour=(255,255,255))
  ```

  Don't forget the comma!
  
## Pixels

  ![](images/closeup_of_pixels.jpg)


1. Select `File > New Window`.
1. Type in the following code:

  ```python
  from astro_pi import AstroPi
  ap = AstroPi()
  ap.clear()
  x = 0
  y = 0
  ap.set_pixel(x, y, 255, 255, 255)
  ```

1. Select `File > Save` and choose a file name for your program.
1. Then select `Run > Run module`.
1. This will turn one LED in the corner white.
1. Remember that you can change the colour if you wish.
1. Your teacher will explain how to use the `x, y` co-ordinate system.

  0|1|2|3|4|5|6|7
  ---|---|---|---|---|---|---|---
  1|||||||
  2|||||||
  3|||||||
  4|||||||
  5|||||||
  6|||||||
  7|||||||

1. See if you can get a different colour in each corner of the LED matrix. You will need to use the `set_pixel` command multiple times in your code.
1. You may be tempted to try and draw shapes or patterns using the `set_pixel` command over and over in your code. There is a `set_pixels` command though and with it you can change all 64 LEDs using one line of code! Your teacher will show you how to use it. You can copy and paste this code get yourself going:

  ```python
  creeper_pixels = [
  O, O, O, O, O, O, O, O,
  O, O, O, O, O, O, O, O,
  O, O, O, O, O, O, O, O,
  O, O, O, O, O, O, O, O,
  O, O, O, O, O, O, O, O,
  O, O, O, O, O, O, O, O,
  O, O, O, O, O, O, O, O,
  O, O, O, O, O, O, O, O
  ]
  ```
