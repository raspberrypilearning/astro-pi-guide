# Movement

The Astro Pi has a movement sensor called an IMU. It can measure the kind of movement it is experiencing.

## What is an IMU?

IMU stand for *inertial measurement unit*. It's actually three sensors in one:

- A gyroscope (measures momentum and rotation)
- An accelerometer (measures acceleration forces and can be used to find the direction of gravity)
- A magnetometer (measures the Earths own magnetic field, so it's a bit like a compass)

Why is a movement sensor important though? When you're up in space there is one question of absolute importance that you must *always* know the answer to:

- **Which way am I pointing?**

If you don't know your orientation you are in big trouble. So an IMU sensor like this is one used on all spacecraft to track movements and maintain an understanding of orientation. Even the earliest spacecraft had them. Ask your grandparents if they remember the [Apollo missions](http://en.wikipedia.org/wiki/Apollo_program)? The missions that first took humans to the surface of the Moon.

Below is a picture of the IMU sensor from the Apollo command module. See how big it is compared to the tiny black box on the Astro Pi?

  ![](images/apollo_imu.jpg)
