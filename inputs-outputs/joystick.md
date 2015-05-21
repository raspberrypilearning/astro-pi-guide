# The Joystick

The Astro Pi joystick is mapped to the four keyboard cursor keys, with the mouse middle-click being mapped to the Return key. This means that moving the joystick has exactly the same effect as pressing those keys on the keyboard. Remember that the down direction is with the HDMI port facing downwards.

  ![](images/cursor_keys.jpg)
  
## Keyboard mapping

1. Open **Python 3** from a terminal window as `sudo` by typing:
  
  ```bash
  sudo idel3 &
  ```
  
1. A Python Shell window will now appear.
1. Select `File > New Window`.
1. Type in the following code:

  ```python
  import pygame
  
  from pygame.locals import *
  from astro_pi import AstroPi
  
  pygame.init()
  pygame.display.set_mode((640, 480))
  ap = AstroPi()
  ap.clear()
  
  running = True
  
  while running:
      for event in pygame.event.get():
          print(event)
          if event.type == QUIT:
              running = False
              print("BYE")
  ```

1. Select `File > Save` and choose a file name for your program.
1. Then select `Run > Run module`.

  Note that we are using the [pygame](http://www.pygame.org/docs/) Python module to detect the key presses.

1. A blank window will appear. Use the mouse to move it to one side of your screen so that the Python Shell window is also visible.
1. Keep the blank window selected but move the mouse over it, press and release some keys on the keyboard and waggle the Astro Pi joystick. Try pressing and holding a key for a moment and then releasing it a few seconds later. You should notice that two events occur when you do this: one for the key going down, and another for the key being released. For this program you will only use the **KEY DOWN** event.
1. Click the `x` in the corner of the blank pygame window. You should see the `BYE` message appear in the *Python Shell* window but the blank window does not close. 

We're consuming the pygame event queue using the `for event in pygame.event.get():` syntax. This will loop through all keyboard and mouse events that occur. Inside the loop, we display what the event was by using `print(event)` and then test to see if the event type is `QUIT`. If it is, we set `running` to `False` which causes the `while` loop to end and the program to finish. The program should print a line of text in the Python Shell window whenever we move the mouse, click the mouse, and press or release a keyboard key.
  
## Detecting movement of joystick with code

Think about how a joystick might work. You can use the LED matrix to help you think about it. Let's make a pixel white and use the joystick to move the pixel around the 8x8 matrix. To do this you can use an event to detect a key press. For example, if a key is pressed DOWN what steps need to happen to move the pixel? 

    - Turn OFF the LED using current `x` and `y`
    - If DOWN then add 1 to `y`
    - If UP then subtract 1 from `y`
    - If RIGHT then add 1 to `x`
    - If LEFT then subtract 1 from `x`
    - Turn ON the LED using updated `x` and `y`

1. Start by just adding the code for the DOWN key. Delete the `print(event)` command that you used in the previous section and insert the code below at the same indentation level:

  ```python
  if event.type == KEYDOWN:
      ap.set_pixel(x, y, 0, 0, 0)  # Black 0,0,0 means OFF
      
      if event.key == K_DOWN:
          y = y + 1
      
      ap.set_pixel(x, y, 255, 255, 255)
  ```

1. Save and run the code. You should be able to move the pixel point down using the `DOWN` key or the joystick. If you keep going, you'll eventually see this error:

  `ValueError: Y position must be between 0 and 7`

1. Our `y` value can only be between 0-7, otherwise it's off the edge of the matrix and into empty space! So that's why the error happens; the Astro Pi doesn't understand values outside this range. Our code just keeps adding 1 to `y` every time the DOWN key is pressed, so we need to stop `y` going above 7. 

  We can achieve this by adding the syntax `and y < 7` (and `y` is less than 7) to the key direction test:
  
  ```python
  if event.key == K_DOWN and y < 7:
      y = y + 1
  ```

1. Save and run the code again; this time, the code should not allow the point to go beyond the edge of the screen.

1. Now that this works, you will need to add the other directions for the joystick. Where you have `if event.key == K_DOWN:` in your code, you can also use:

  - `K_UP`
  - `K_LEFT`
  - `K_RIGHT`
  - `K_RETURN`

1. We can add a section for each direction to complete your code:
  
  ```python
  import pygame
  
  from pygame.locals import *
  from astro_pi import AstroPi
  
  pygame.init()
  pygame.display.set_mode((640, 480))
  
  ap = AstroPi()
  ap.clear()
  
  running = True
  
  x = 0
  y = 0
  ap.set_pixel(x, y, 255, 255, 255)
  
  while running:
      for event in pygame.event.get():
          if event.type == KEYDOWN:
              ap.set_pixel(x, y, 0, 0, 0)  # Black 0,0,0 means OFF
              
              if event.key == K_DOWN and y < 7:
                  y = y + 1
              elif event.key == K_UP and y > 0:
                  y = y - 1
              elif event.key == K_RIGHT and x < 7:
                  x = x + 1
              elif event.key == K_LEFT and x > 0:
                  x = x - 1
              
              ap.set_pixel(x, y, 255, 255, 255)
          if event.type == QUIT:
              running = False
              print("BYE")
  ```

1. When you run your code, you should now be able to move the pixel point anywhere on the matrix.
