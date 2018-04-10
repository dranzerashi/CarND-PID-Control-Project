# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

You can also use the build.sh and run.sh files to build and run respectively.


## Project Instructions and Rubric

Note: regardless of the changes you make, your project must be buildable using
cmake and make!

More information is only accessible by people who are already enrolled in Term 2
of CarND. If you are enrolled, see [the project page](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/f1820894-8322-4bb3-81aa-b26b3c6dcbaf/lessons/e8235395-22dd-4b87-88e0-d108c5e5bbf4/concepts/6a4d8d42-6a04-4aa6-b284-1697c0fd6562)
for instructions and the project rubric.


## Reflection

A video of the simulation result can be found [here](https://github.com/dranzerashi/CarND-PID-Control-Project/blob/master/result.mp4)

A proportional–integral–derivative controller (PID controller)
consists of three basic coefficients: proportional, integral and derivative which are varied to get optimal response. A PID controller is used here to control the steering angle of the car.

* The proportional term corrects instances of error and brings the car back towards the centre. However this can cause large oscillations if Kp is large, while if the Kp is too small the car takes a long time to reach the centre.
* The integral corrects accumulation of error. For eg. the system bias can cause the P term to oscillate around a point shifted from the centre. Integral accumulates error over time and corrects this shift and brings the car back to centre. If Ki is too low then the car takes longer to get back to centre after turns as well as stays at the sides of lanes for longer. Whereas large Ki values introduce more Oscillations.
* The derivative corrects present error versus error the last time it was checked. The derivative term Kd smoothens out the oscillations and makes the car achieve convergence faster by slowly decreasing the steering angle as it nears the centre. High Kd values makes the car achive the convergence very slowly while low values of Kd causes car to overshoot more.

I ran the computations on a very mediocre machine. Initially I started with the values given at the end of class (0.2, 3.0, 0.004) However the machine was too slow and had a response rate of less then 1 per second. This caused the car to always turn too much. I therefore reduced the speed of the car to about 0.05 from 0.3 to achieve more response rate. I adjusted the values of P, I and D. I started with just Kp and found that it performed well in the range of 0.05 to 0.1 I chose 0.05. This ran the car till the bridge. But the car was oscillating too much and couldn't handle turns.
Next I added Kd values and tried to correct the oscillations. High values of Kd caused no difference to the original P controller, I settled for about 0.01 which slowly but surely converged. 
Next I added Ki to correct the bias as well as help correct the car after taking turns. High Kd values generally caused the car to wobble more. I settled for 0.004 as the right amount.

I think the Kp, Kd, and Ki values are highly dependent on the systems performance as I am sure that the car could be controlled more accurately if 10 to 20 responses are completed every second. For these values from the class might be more appropriate as there is more opportunity to make corrections every second.

 

