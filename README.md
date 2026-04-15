# Robotics-T2
README: VEX EXP marble Sorter
Project Overview:

The Fast Colour Sorter is an automated system designed for the VEX EXP platform. It utilizes the VEX Optical Sensor to identify the color of an object (specifically Blue, Red, and Green marbles) and triggers a mechanical response using two motors to sort the objects into designated zones.

Build Instructions
Hardware Requirements
1x VEX EXP Brain

1x VEX Optical Sensor (Connected to Port 1)

2x VEX EXP Motors (Connected to Ports 2 and 3)

1x VEX Inertial Sensor (Built-in or external for seeding)

Assembly
Optical Sensor: Mount the sensor approximately 5-10mm from the marble path to ensure consistent brightness readings.

Motor 2 (The Selector): Attach to a rotating tray or arm. Calibrate it so that 0°, 120°, and 240° align with your three collection bins.

Motor 3 (The Ejector): Attach to a gate or plunger mechanism. The code expects 0° to be "closed" and -90° to be "eject."

Usage
Power On: Turn on the VEX EXP Brain and load the Python project.

Calibration: Observe the Hue and Brightness values on the Brain screen. If your environment has different lighting, update the a_bounds, b_bounds, and c_bounds lists in the bounds() function.

Operation:

Place a marble in front of the sensor.

The screen will display the detected color.

Motor 2 will move to the correct bin.

Motor 3 will actuate to release the marble.

Reset: The system automatically resets the ejector and buffer after every successful sort.

Task Implementation Details
Fast Polling: The loop runs every 50ms to ensure high-speed detection.

Stability Logic: The code uses a "rolling buffer" (a list of the last 3 readings). It only sorts when it sees 2 identical color readings in a row, preventing "flicker" errors or false positives from motion.

Calibrated Bounds: Unlike simple color sensing, this uses specific Hue/Brightness ranges to differentiate between similar-looking objects.


Code Setup:
The code is compiled and downloaded to the vex brain using VexcodeEXP v5

References:
1.Lam, D. K., Ngo, N. M., & Ngo, H. Q. T. (2023). Profile generation using the filtering technique for the fast motion and smooth performance in the hardware level of autonomous system. IET Science, Measurement & Technology.
 Provides the theoretical justification for your "Rolling Buffer" logic. It explains how software filters mitigate noise and physical limitations to ensure smooth hardware actuation.
 https://digital-library.theiet.org/doi/full/10.1049/smt2.12158
 2. model design inspired by:
 https://youtu.be/W9dm_WjWROg?si=ybwX4cw-IeKXgCwF
 
