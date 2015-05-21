# Astro Pi: software setup

This guide assumes you have an SD card loaded with NOOBS/Raspbian. If not, see [the Downloads section](http://www.raspberrypi.org/downloads/) to download NOOBS/Raspbian and use the [NOOBS setup guide](http://www.raspberrypi.org/help/noobs-setup/) for help with installation.

[Connect](assemble.md) your Astro Pi HAT and boot it up.

## Astro Pi driver installation

Ensure your Pi is connected to the internet, then run the following command (from the command prompt or a Terminal window) to download and start the Astro Pi installation script:

```bash
wget -O - http://www.raspberrypi.org/files/astro-pi/astro-pi-install.sh --no-check-certificate | bash
```

This will take about 5 minutes on a Pi 2 and about 15 to 20 minutes on a Pi 1.
When it's finished you'll see the following message:

```
You must reboot to complete the Astro Pi installation
Type:
sudo reboot
and press Enter when ready
```

Reboot the Pi to complete the installation:

```bash
sudo reboot
```

The rainbow pattern on the LED matrix should now turn off during boot up.

## What's Next?

Now you are ready to write your first [program](program.md) for the Astro Pi board.
