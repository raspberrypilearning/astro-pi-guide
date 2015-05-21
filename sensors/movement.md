# Movement

The Astro Pi has a movement sensor called an IMU, which can measure the kind of movement it is experiencing.

## What is an IMU?

IMU stand for *inertial measurement unit*. It's actually three sensors in one:

- A gyroscope (measures momentum and rotation)
- An accelerometer (measures acceleration forces and can be used to find the direction of gravity)
- A magnetometer (measures the Earth's own magnetic field, so it's a bit like a compass)

![](images/apollo_imu.jpg)

Why is a movement sensor important, though? When you're up in space there is one question of absolute importance that you must *always* know the answer to:

- **Which way am I pointing?**

If you don't know your orientation you are in big trouble, so an IMU sensor like this one is used on all manned and unmanned spacecraft to track movements and maintain an understanding of orientation. Even the earliest spacecraft had them. Ask your grandparents if they remember the [Apollo missions](http://en.wikipedia.org/wiki/Apollo_program) that landed humans on the surface of the moon.

Above is a picture of the IMU sensor from the Apollo command module. You'll notice how big it is compared to the tiny black cube on the Astro Pi; that's the difference between 1975 and 2015 technology. Incidentally, the Astro Pi IMU is probably not as accurate as the Apollo one, however it *is* a million times cheaper!

## How is orientation represented?

We all know the Earth rotates around an axis that runs between the North and South Poles. All objects in space or otherwise have *three* axes around which they can rotate. If you know how much rotation has happened on each axis, then you know which way the object is pointing.

The three axes are:

- **Pitch** (like a plane taking off)
- **Roll** (the plane doing a victory roll)
- **Yaw** (imagine steering the plane like a car)

Watch this short [video](https://www.youtube.com/watch?v=pQ24NtnaLl8) that shows where these axes are in relation to a plane. Try to imagine the plane pointing in any random direction. To get the plane into that position, you can rotate it by a known amount around each axis to get it into the orientation that you imagined.

Let's download and run a 3D demo program to explore this.

## Apollo Soyuz Demo

The image below shows the Apollo Soyuz module that was used to take humans to the surface of the moon during the 1970s. The 3D demo we're going to play with shows this same spacecraft (but with less detail).

![](images/apollo_soyuz.jpg)

You will need to have your Astro Pi connected to the internet in order to download the required software.

Enter the commands below into a terminal window:

```bash
sudo apt-get install python3-pip
sudo pip-3.2 install pi3d
git clone git://github.com/astro-pi/apollo-soyuz
cd apollo-soyuz
sudo ./soyuz.py
```

Pi 1 users will have to wait 3 to 4 minutes for this to load. For Pi 2 users it's about 30 seconds. When you see the spacecraft appear on the screen start moving the Astro Pi around with your hands. The the main booster is where the SD card slot is on your Astro Pi.

See if you can get the spacecraft to do the pitch, roll and yaw movements. Refer back to the [video](https://www.youtube.com/watch?v=pQ24NtnaLl8) if you need to remind yourself which is which.

The code behind this demo is basically calling the Astro Pi `get_orientation` function which accesses the IMU sensor. This then returns three angles between 0 and 360 degrees. One for each axis (pitch, roll and yaw). The spacecraft model is then rotated by those angles so that it points in the same direction. This is all repeating over and over very quickly to maintain the orientation of the model with what the IMU is reporting.

Press `Esc` to exit the demo. Let's try a simpler version of this ourselves in code.

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
  
  o = ap.get_orientation()
  pitch, roll, yaw = o.values()
  print(pitch, roll, yaw)
  ```

1. Select `File > Save` and choose a file name for your program.
1. Select `Run > Run module`.
1. If you see the error `IMU Init Failed, please run as root / use sudo` on the last line in red, it means you haven't followed the instructions above. Close everything and go back to step 1.
1. You should now see something like this: 
  
  ```
  IMU Init Succeeded
  (356.35723002363454, 303.4986602798494, 339.19880231669873)
  ```

1. We don't need all the numbers after the decimal point so let's round them off. Just before the `print(pitch, roll, yaw)` line, add these lines below:

  ```python
  pitch = round(pitch, 1)
  roll = round(roll, 1)
  yaw = round(yaw, 1)
  ```

## Monitor movement over time
