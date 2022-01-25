# V386-Troubleshooting
One of our motor controllers was going into neutral (brake) at a very consistent period during forward driving, on the ground or on blocks. First we tested each motor/controller individually using the REV client and they acted normal. After checking every connection in the drive system's CAN bus an electrical issue seemed unlikely so it was ruled out. One of our software engineers tracked it down to one of our sub-systems causing a delay, and after removing it from the code the drive system was behaving normally again.

After this we noticed the can bus load was fluctuating from 35% to 70% in fractions of a second. This is definitely not normal, especially considering that by then we had removed practically everything except the drive code, so the can bus should be experience less than 35% load the entire time. We’re pretty stumped so any ideas at all would be greatly appreciated.

This is the code before the offending BallMovementSubsystem was removed. I've messaged Max, the guy who made the changes to get it working, to have him commit the code with the changes he made. From what he said it sounded like he believed the "periodic()" method was causing a delay that meant the malfunctioning motor controller wasn't getting commands when it expected to. I'm not as familiar as he is with the system, as it is left over from last year's code which I did not work on.

![Can Bus Load](/20220124_205635.jpg)


Update - max commited the updated code and I've added it here
