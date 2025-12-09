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
  * 12 Male-to-Female jumper cables

The following image is a schematic for how you will wire your Raspberry Pi, Breadboard, and Unltrasonic Distance Sensor.

<img width="969" height="552" alt="Screenshot 2025-12-09 at 11 32 11 AM" src="https://github.com/user-attachments/assets/18547586-8521-4d65-8b15-3bd4891eda69" />


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

![IMG_6375](https://github.com/user-attachments/assets/b42ee700-fa8d-4c41-8d58-459067b5fcac)


Using your Male-to-Female jumper cable, ground one side of the pushbutton. Then, with another Male-to-Female jumper cable connect the other side of the button to the Raspberry Pi. In the photo above, it is connected to GPIO 10.

## Step Three

Next, you will connect the Ultrasonic Distance Sensor to the Breadboard and Raspberry Pi. Reference the follwoing image for how to connect your sensor.

![IMG_6361](https://github.com/user-attachments/assets/adadbaef-fe0c-4c8b-bd92-0a22f6bdf413)

This is where you use the 470 ohm resistor and the last 330 ohm resistor. Ensure that both reistors are in line so that you can ground them. Using four Male-to-Female jumper cables to connect the Ground, Echo, Trig, and VCC to the Breadboard. Then, use your last four Male-to-Female jumper cables to connect the Breadboard to the Raspberry Pi. In the above photo, the VCC is connected to 5V.Trig is connected to a GND pin. Echo is connected to GPIO 24. The Ground on the sensor is connected to a GND port on the Pi. 

## Step Four

Now you will need to input this code to activate your Motion Detector Alarm.

```python
from gpiozero import DistanceSensor
from time import sleep
from gpiozero import LED, Button


led = LED(17)
button = Button(10)
sensor = DistanceSensor(echo=24, trigger=23, max_distance=2.0)

button.when_pressed = led.on
button.when_released = led.off

while True:
        distance = sensor.distance * 100
        print("Distance: %.2f" % distance)
        sleep(0.5)
        
        if distance < 10:
            led.on()
            button.wait_for_press()
            led.off()
            
```

## Explanation of Result

With this code, your distance sensor acts as the motion detector. When an object comes within 10 cm of the distance sensor, the light will illuminate. Then when you press the button, the script will reset and the lght will turn off until there is an object detected within that 10 cm parameter. 
