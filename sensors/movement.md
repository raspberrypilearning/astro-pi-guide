# Movement

The Astro Pi has a movement sensor called an IMU. It can measure the kind of movement it is experiencing.

## What is an IMU?

IMU stand for *inertial measurement unit*. It's actually three sensors in one:

- A gyroscope (measures momentum and rotation)
- An accelerometer (measures acceleration forces and can be used to find the direction of gravity)
- A magnetometer (measures the Earths own magnetic field, so it's a bit like a compass)

Why is a movement sensor important though? When you're up in space there is one question of absolute importance that you must *always* know the answer to:

- **Which way am I pointing?**

If you don't know your orientation you are in big trouble. So an IMU sensor like this one is used on all spacecraft (manned and unmanned) to track movements and maintain an understanding of orientation. Even the earliest spacecraft had them. Ask your grandparents if they remember the [Apollo missions](http://en.wikipedia.org/wiki/Apollo_program). The missions that landed humans to the surface of the Moon.

Below is a picture of the IMU sensor from the Apollo command module. See how big it is compared to the tiny black cube on the Astro Pi? That's the difference between 1975 and 2015 technology. Incidentally the Astro Pi IMU is probably not as accurate as the Apollo one, however it's a million times cheaper!

![](images/apollo_imu.jpg)

## Which way am I pointing?

1. Open **Python 3** from a terminal window as `sudo` by typing:
  
  ```bash
  sudo idel3 &
  ```
1. Select `File > New Window` and enter the following code:

  ```python
  from astro_pi import AstroPi
  
  ap = AstroPi()
  ap.clear()
  
  orientation = ap.get_orientation()
  print("p: {pitch:.1f}, r: {roll:.1f}, y: {yaw:.1f}".format(**orientation))
  ```

1. Select `File > Save` and choose a file name for your program.
1. Select `Run > Run module`.
1. If you see the error `IMU Init Failed, please run as root / use sudo` (look on the last line of the message in red) it means you haven't followed the instructions above. Close everything and go back to step 1.
1. You should now see something like this: 
  
  ```
  IMU Init Succeeded
  p: 2.9, r: 339.8, y: 303.2
  ```
