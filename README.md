# HeliFlightController
This Arduino sketch is a simple flight controller for a 4ch RC heli based on an [MPU6050 6-axis gyroscope/accelerometer](https://invensense.tdk.com/products/motion-tracking/6-axis/mpu-6050/). Even though the MPU has an accelerometer, this data is ignored and only the gyroscope data is used. This means the flight controller is more akin to a flybarless stabilization unit than the flight controllers found on multirotors. 

In light of this, the program only improves the short-term stability of the helicopter, up to the point that a human can easily stabilize the vehicle in the long-term. Still, as with any helicopter a minimum degree of skill is required in order to pilot the aircraft. Stabilization about pitch and roll is accomplished via a PID loop using the Gyro measurements from the MPU6050 as the proportional term. Stabilization about the yaw axis uses a PI loop along with a torque-offset term that increases with throttle (revo mixing). That is, as more throttle is added, the tail rotor is commanded to apply more counter-torque. 

The program is designed to receive 4 PWM inputs from an RC receiver (operating in MODE 2) and outputs 3 PWM signals. Two of these signals go to the cyclic servos of the helicopters and a third goes to a either a tail-servo or an RC speed controller. Since it is assumed only two servo motors are used for controlling the rotor, only a 90-degree swashplate is supported. 

MODE 1 can also be used with this program. It is only a matter of swapping the RX connections to the arduino. Lastly, The program was written for an Arduino Nano but it should be compatible with other boards. See the attached schematic for an example of the required circuit.

<img src = "heli_flight_control_schem.png" width = "80%" height = "80%"> 

See these links for flight videos of a helicopter that uses this software:
  
- https://www.youtube.com/watch?v=qZ7qUPAXkvc
- https://www.youtube.com/watch?v=zrrgVdPAhFI


Finally, below are images of the helicopter this code was initially writen for:

<img src = "/example_pictures/front_view_res.JPG" width = "30%" height = "30%"> <img src = "/example_pictures/side_view_res.JPG" width = "30%" height = "30%">


