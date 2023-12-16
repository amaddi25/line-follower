# R4D5 Line-Following Astromech
### Collaborators: Ayush Kakkanat & Akanksha Maddi

Click [here](https://Ayush17318.github.io/line-follower/) for the website version.

This is the summarized documentation for the R4D5 robot and will discuss the process, logic, and tools used. The project was completed in a span of 5 weeks and has the following functions to execute:
- Linear line tracking
- Turn various sized curves
- Not be affected by line breaks
- Not be affected by intersections
- Avoid obstacles
- Stop in an end-zone
- Find its way back to the start-zone
  
The goal of the project was for the robot to navigate any track with the above stated elements arranged in a randomized order with sufficient speed and reliability.

The following links will discuss the hardware, electronics, software, and analysis involved with building the robot pictured below.
- [Hardware & Design](hardware-and-design.md)
- [Electronics](electronics.md)
- [Software](software.md)
- [Analysis](analysis.md)

put in naked romi and r4d5 romi photos
![here](./assets/images/naked_romi.png)

![here](./assets/images/r4d5_isometric.png)

![here](./assets/images/r4d5_front.png)

![here](./assets/images/romi_inside_shell.png)

The objective of this robot is to traverse two courses from start to finish and back to the start position by following a line and navigating around an obstacle. The two courses both involve solid, dashed, straight, curved, and crossed lines. 
![here](./assets/images/track1.png)

![here](./assets/images/track2.jpg)

Our robot uses an array of 6 reflectance sensors to detect if the robot is over a black or white area. Using analog QTR sensors from Polulu (https://www.pololu.com/product/4246), the robot uses logic to parse through "black" or "white" data from each of the six sensors to determine which direction it should head in. This simple logic resulted in a total of 17 combinations of velocities and headings that the robot is pre-programmed to decide between. 

Final results

(show a video/gif of the robot completing both tracks)

Challenges

(talk about the period causing motors to pulsate and not reach the desired duty cycle, closed loop)

suggestions

talk about these
(add closed loop, use bno055 to keep track of robots absolute position and be able to find its way back to the start, get more sensors, a more robust obstacle detection algorithm using a time of flight sensor)



checklist:
finish readme
software page - doxygen, fsm, task diagram
analysis page - math
upload code
