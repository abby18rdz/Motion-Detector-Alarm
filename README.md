# Motion-Detector-Alarm
How to build a Motion Detecting Alarm with Breadboard, Raspberry Pi, LED, Pushbutton, and UltraSonic Sensor.
The following are instructions to follow to make a flashing motion detecting alarm using a breadboard and a Raspberry pi. This includes an LED, pushbutton, and ultrasonic sensor. When the ultrasonic sensor detects motion, the LED will flash to alert and you can use the pushbutton to reset the alert. 
To build this detector, you will need:
  * Raspberry Pi
  * Breadboard
  * LED
  * Pushbutton
  * Ultrasonic Distance Sensor
  * 2 330 ohm resistors
  * 1 470 ohm resistor
  * 1 Male-to-Male jumper cables
  * 11 Male-to-Female jumper cables

The following image is a schematic for how you will wire your Raspberry Pi, Breadboard, and Unltrasonic Distance Sensor.

<img width="1163" height="611" alt="Screenshot 2025-12-02 at 11 05 04 AM" src="https://github.com/user-attachments/assets/deb2992a-bee5-4b53-9861-b1ded700b9c6" />

**WARNING** You could permanently your pi, so please read carefully:
  * Make sure that your Pi is turned off when connecting cables to the GPIO ports.
  * Make sure to use the correct resistor. The LED will consume as much voltage as it can, which may damage your Pi.
  * Make sure you do not bend the GPIO pins
  * Make sure that you ground yourself electrically beore proceeding.

## Step One

First, you are going to connect your LED. Reference the following image for how to connect your LED.


![IMG_6359](https://github.com/user-attachments/assets/6f46b44d-1891-4146-8188-f510b62f1d33)

Place one of your 330 ohm resitors in such a way that it lines up with the cathode (positive) LED. This will prevent your LED from drawing a detrimental amount of power from the Raspberry Pi. Then place one of your Male-to-Female jumper cables in such a way that that it aligns with the anode (negative) of the LED. In the photo above, it is connected to GPIO 17. 

## Step Two

Next, you will connect the pushbutton to the Breadboard. Reference the follwoing image for how to connect your pushbutton.

![IMG_6360](https://github.com/user-attachments/assets/b8482ddd-ed51-41c0-bd30-2c97df871d77)

Using you Male-to-Male jumper cable, ground one side of the pushbutton. Then, with a Male-to-Female jumper cable connect the other side of the button to the Raspberry Pi. In the photo above, it is connected to GPIO 10.

## Step Three

Next, you will connect the Ultrasonic Distance Sensor to the Breadboard and Raspberry Pi. Reference the follwoing image for how to connect your sensor.

![IMG_6361](https://github.com/user-attachments/assets/adadbaef-fe0c-4c8b-bd92-0a22f6bdf413)

This is where you use the 470 ohm resistor and the last 330 ohm resistor. Ensure that both reistors are in line so that you can ground them. Using four Male-to-Female jumper cables to connect the Ground, Echo, Trig, and VCC to the Breadboard. Then, use your last four Male-to-Female jumper cables to connect the Breadboard to the Raspberry Pi. In the above photo, the VCC is connected to 5V.Trig is connected to a GND pin. Echo is connected to GPIO 24. The Ground on the sensor is connected to a GND port on the Pi. 

## Step Four

Now you will need to input this code to activate your Motion Detector Alarm.
