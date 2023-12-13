# Electronics

The electronics used for this project involve following:

### 1. Motors
Brushless DC motors which come with the Romi kit are used to drive the robot. They are small and low power but have a gear reduction of 120:1.

Further details about the motors can be found [here](https://www.pololu.com/product/1520).
### 2. Encoders
Encoders that are compatible with the Romi power board and the motors were purchased from [this link](https://www.pololu.com/product/3542).
### 3. Romi Power Board
Comes with the Romi kit.
### 4. STM32 Microcontroller
The STM32 NUCLEO-L476RG which was provided is the main microcontroller used for this project.

<p align="center">
  <img src="/docs/assets/images/STM32.png" />
</p>

### Shoe of Brian
The [shoe of brian](/assets/solidworks/ShoeOfBrian03E.step) is a board custom designed by Dr. JR Ridgely that interfaces with the STM32 and translates micropython code to C which can be read by the STM32.

<p align="center">
  <img src="/docs/assets/images/shoe_of_brian.png" />
</p>

### 5. Reflectance sensors
In order to track the line, which is a 2 inch wide black strip on white paper, [reflectance sensors](https://www.pololu.com/product/4246/pictures) were used.

This is 6 channel and 8 mm spaced with analog output from pololu. This was chosen after careful consideration of the line width and sensor separation. In this case, the sensor channels from which we collect data are 1,3,5,7,9,11. The even channels provide a weighted average of two neighbouring sensors which we did not have a need for. In a perfect orientation, 5 and 7 lie within the line and the rest are outside the line. This was the basis for the line tracking and error correction logic. Specifially in this case, an analog sensor works better than its digital counterpart to be able to finely distinguish the edge of the line.
### 6. Limit Switch


pins - motors, encoders, imu, sensors, limit switch

imu
stm
shoe of brian
limit switch
batteries
