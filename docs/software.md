# Software

The software is the brains behind the operation. The code is built in a modular fashion with each class and task being described in their own individual files and the main code that is run only instantiates the classes and runs the scheduler.

Cotask.py and taskshare.py enable round robin multi-tasking and were provided to us by Dr. JR Ridgely.
The architecture of the software can be found in the following task diagram. 

<p align="center">
  <img src="/docs/assets/images/task_diagram.png" />
</p>

Each task is an external peripheral which either is being controlled or being analyzed for data. Each task has a set priority and frequency which means that there is a hierarchy in the importance of our tasks. A higher value indicates a higher priority. The period of each task defines how fast the task is run. Optimizing the priority and the frequency was highly crucial for the functioning of the robot, for example the motors have a higher priority than the reflectance sensors and thus should also be run at a higher frequency. The period value for each task was tuned through testing to see the response of the robot on the track. 
The task diagram also has arrows linking each task, these are called 'queues' which mean the tasks communicate key information about what they should be doing at any given moment. For example, the sensor data is communicated to the motors to tell them what velocity to be running at and thus controlling the speed and direction of the robot. This is important in being able to complete the various functions. In addition, having a limit switch allows it to communicate to the motors that it is approaching an obstacle and must proceed accordingly to avoid it.

The entire project was completed in an open loop control algorithm, ie, there is no attribute or variable that is being controlled or checked for errors. Ideally, either the motor velocity or the sensor data would be controlled in order to have a smooth line tracking. However, it was decided that this was an over-engineered solution for the scope of the project and that have a finite state machine based approach in open loop would suffice. 

The finite state machines for each task is as described below:
1. Motor Task
<p align="center">
  <img src="/docs/assets/images/mot_gen_fsm.png" />
</p>

2. Sensor Task
<p align="center">
  <img src="/docs/assets/images/sen_gen_fsm.png" />
</p>

3. Switch Task
<p align="center">
  <img src="/docs/assets/images/sw_gen_fsm.png" />
</p>

The detailed doxygen commented code for each python file can be found [here](https://ayush17318.github.io/Term-Project/)
