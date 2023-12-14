# Analysis

In order to understand and predict the behaviour of the robot, a simplified differential drive model of the system was designed. A kinematic model was chosen over a full dynamic model in order to simplify the physics involved. As such motor torque and friction for example were ignored.

The following hand calculations describe the dynamics used for the simulations

<p align="center">
  <img src="/docs/assets/images/hw3-1.jpg" />
</p>

<p align="center">
  <img src="/docs/assets/images/hw3-2.jpg" />
</p>

<p align="center">
  <img src="/docs/assets/images/hw3-3.jpg" />
</p>

For a simulation of the robot moving in a circle, the following plots were described

<p align="center">
  <img src="/docs/assets/images/hw_x-t.png" />
</p>

<p align="center">
  <img src="/docs/assets/images/hw_y-t.png" />
</p>

<p align="center">
  <img src="/docs/assets/images/hw_h-t.png" />
</p>

<p align="center">
  <img src="/docs/assets/images/hw_x-y.png" />
<
  
The full jupyter simulation for the robot moving in a circle can be found [here](/code/HW0x03.ipynb).

The kinematic model is not sufficient for our purposes. The assumptions made about no slip and no drift may or may not be accurate. There can be variations in the power delivered by the motors to the wheels, friction, inertia, or jerk which could cause the kinematic model to be inaccurate. However, it is important to note that while the kinematic model is not good for detailed simulations, it is a good initial estimation due to the assumptions made which are a largely accurate for most cases. A closed loop system with a controller and motor encoders would aid in improving the kinematic model without having to model the weight, forces, friction, etc.

Drift can be accounted for in our simulation by adding noise. The noise can be added to the input wl and wr values of the wheel angular velocity. In the real world, we can account for it by the addition of sensors. In particular, an IMU would play a big role in fixing drift. It can be calibrated on startup and using the accelerometer and gyroscope data, the yaw position of robot can be taken and compared to expected values. This would allow us to note if there is drift occuring. A feedback control system can be implemented to ensure that the velocity and swept angle by the robot is as expected.

Inputs will be useful for feedback and b) How you might split up a complicated path into segments such as straight lines, circular arcs, in-place turns, etc
The term project will require a minimum of 4 reflectance sensors which will detect the white and black colours of the path. Their placement will be such that the outer two sensors will keep track of the white outside the line and the inner two sensors will keep track of the black within the line. With the relevant change in colour value, by implementing a finite state machine, the robot will either move forward, turn left, or turn right. In this manner it will be able to navigate straight lines, arcs, in-place turns, etc. without specifically defining a control loop with gains, but in effect acts as a controller.

It is important to have the time history of the wheels' speed because otherwise determining the orientation and location of the robot after it having traversed a specific path would be nearly impossible. This is because with just the angle swept there can be many different path combinations with different movements with time. Integrating the time history of the angular velocity, the position of the wheels can be used to obtained the position of the robot which in conjunction with the angle swept by the wheel can be used to track the orientation and location. In order to be able to track these values, the encoder data can be used to calculate the delta between an old and new position. In addition, using the quaternions or euler angles from an IMU, more accurate data can be tracked without worrying about drift.
