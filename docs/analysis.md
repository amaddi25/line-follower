# Analysis

In order to understand and predict the behaviour of the robot, a simplified differential drive model of the system was designed. A kinematic model was chosen over a full dynamic model in order to simplify the physics involved. As such motor torque and friction for example were ignored.

The following hand calculations describe the dynamics used for the simulations

<p align="center">
  <img src="/docs/assets/images/hw3-1.JPG" />
</p>

<p align="center">
  <img src="/docs/assets/images/hw3-2.JPG" />
</p>

<p align="center">
  <img src="/docs/assets/images/hw3-3.JPG" />
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
</p>
  
The full jupyter simulation for the robot moving in a circle can be found [here](/code/HW0x03.ipynb).

The kinematic model is not sufficient for our purposes. The assumptions made about no slip and no drift may or may not be accurate. There can be variations in the power delivered by the motors to the wheels, friction, inertia, or jerk which could cause the kinematic model to be inaccurate. However, it is important to note that while the kinematic model is not good for detailed simulations, it is a good initial estimation due to the assumptions made which are a largely accurate for most cases. A closed loop system with a controller and motor encoders would aid in improving the kinematic model without having to model the weight, forces, friction, etc.

Drift can be accounted for in our simulation by adding noise. The noise can be added to the input wl and wr values of the wheel angular velocity. In the real world, we can account for it by the addition of sensors. In particular, an IMU would play a big role in fixing drift. It can be calibrated on startup and using the accelerometer and gyroscope data, the yaw position of robot can be taken and compared to expected values. This would allow us to note if there is drift occuring. A feedback control system can be implemented to ensure that the velocity and swept angle by the robot is as expected.

It is important to have the time history of the wheels' speed because otherwise determining the orientation and location of the robot after it having traversed a specific path would be nearly impossible. This is because with just the angle swept there can be many different path combinations with different movements with time. Integrating the time history of the angular velocity, the position of the wheels can be used to obtained the position of the robot which in conjunction with the angle swept by the wheel can be used to track the orientation and location. In order to be able to track these values, the encoder data can be used to calculate the delta between an old and new position. In addition, using the quaternions or euler angles from an IMU, more accurate data can be tracked without worrying about drift.



To comprehend and predict the robot's behavior, a simplified differential drive model was devised, opting for a kinematic model to streamline the physics involved. This choice facilitated the exclusion of factors such as motor torque and friction, simplifying the calculations.

## Kinematic Model Dynamics

The following hand calculations elucidate the dynamics employed for the simulations:

<p align="center">
  <img src="/docs/assets/images/hw3-1.JPG" />
</p>
<p align="center">
  <img src="/docs/assets/images/hw3-2.JPG" />
</p>
<p align="center">
  <img src="/docs/assets/images/hw3-3.JPG" />
</p>

For a simulation depicting the robot moving in a circle, corresponding plots were generated:

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
</p>

Access the full Jupyter simulation for the robot moving in a circle [here](/code/HW0x03.ipynb).

## Kinematic Model Limitations and Enhancements

While the kinematic model serves as a valuable initial estimation, its limitations arise from assumptions about no slip and no drift. Variations in motor power, friction, inertia, or jerk may render the model inaccurate. A closed-loop system with a controller and motor encoders can enhance the kinematic model by accounting for weight, forces, friction, etc.

Drift, a common concern, can be addressed in our simulation by introducing noise to the wheel angular velocity inputs. In the real world, sensor integration, particularly with an IMU, proves instrumental in combating drift. An IMU, calibrated on startup, utilizes accelerometer and gyroscope data to track the yaw position of the robot, allowing for drift detection. A feedback control system ensures the robot's velocity and swept angle align with expectations.

## Path Navigation Strategy

The term project necessitates a minimum of four reflectance sensors to detect white and black path colors. Placed strategically, the outer two sensors track white outside the line, while the inner two sensors track black within the line. Utilizing a finite state machine, the robot dynamically adjusts its course—moving forward, turning left, or turning right—based on color changes. This approach facilitates navigation through straight lines, arcs, in-place turns, etc., acting as an implicit controller without explicit control loops and gains.

## Wheel Speed Time History

Maintaining the time history of wheel speeds is crucial for determining the robot's orientation and location after traversing a specific path. Merely considering the angle swept would yield multiple path combinations. Integration of the time history of angular velocity enables tracking the position of the wheels. Encoder data calculates the delta between old and new positions, while quaternions or Euler angles from an IMU enhance accuracy and mitigate drift concerns.
