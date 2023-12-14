# Analysis

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

Access the full Jupyter simulation for the robot moving in a circle [here](/docs/code/HW0x03.ipynb).

## Kinematic Model Limitations and Enhancements

While the kinematic model serves as a valuable initial estimation, its limitations arise from assumptions about no slip and no drift. Variations in motor power, friction, inertia, or jerk may render the model inaccurate. A closed-loop system with a controller and motor encoders can enhance the kinematic model by accounting for weight, forces, friction, etc.

Drift, a common concern, can be addressed in our simulation by introducing noise to the wheel angular velocity inputs. In the real world, sensor integration, particularly with an IMU, proves instrumental in combating drift. An IMU, calibrated on startup, utilizes accelerometer and gyroscope data to track the yaw position of the robot, allowing for drift detection. A feedback control system ensures the robot's velocity and swept angle align with expectations.

## Path Navigation Strategy

The term project necessitates a minimum of four reflectance sensors to detect white and black path colors. Placed strategically, the outer two sensors track white outside the line, while the inner two sensors track black within the line. Utilizing a finite state machine, the robot dynamically adjusts its course—moving forward, turning left, or turning right—based on color changes. This approach facilitates navigation through straight lines, arcs, in-place turns, etc., acting as an implicit controller without explicit control loops and gains.

## Wheel Speed Time History

Maintaining the time history of wheel speeds is crucial for determining the robot's orientation and location after traversing a specific path. Merely considering the angle swept would yield multiple path combinations. Integration of the time history of angular velocity enables tracking the position of the wheels. Encoder data calculates the delta between old and new positions, while quaternions or Euler angles from an IMU enhance accuracy and mitigate drift concerns.
