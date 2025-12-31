# Engineering-Workplace-Optimizer
An Arduino based IoT system which was created to optimize cognitive skills by monitoring environmental health (Through the DHT11) and managing workflow using the Pomodoro Method.

System Hardware: MicroController: Arduino Uno 
Display: 16 x 2 LCD 
Sensors: DHT11 

1. Verified analog contrast control using a square trimmer potentiometer which can adjust brightness of text.

2. Setting up Data connection using LCD display
Successfully implemented a 4-bit parallel data bus between the Arduino and the LCD.

3. Environmental Monitoring System 
Integrated a DHT11 sensor to provide real-time environmental data acquisition. 

4. Added a Pomodoro focus-timer to mitigate cognitive fatigue

How I made this: This system is built around an Arduino Uno which acts as the central controller for two distinct modules, environmental awareness and workflow management. I used a DHT11 sensor to pull live temperature data, which is then processed and sent to a 16x2 LCD display. To manage the workflow, I programmed a machine logic to switches from 'Idle' to 'Focus' via an push button trigger. When activated, the system initaties a countdown timer and switches a set of visual LED indicators (red for focus and yellow for rest). This system provides an easy to comprehend dashboard which keeps users aware of both their environment and how they are managing their time. 

Why I made this: I noticed that my focus when working on tasks usually fluctuates depending on my working environment. Heat, humidity, and poor time management seemed to drain my energy during long work sessions. I wanted to build a tool that didn't just tell time, but constantly monitored the ergonomics of my workspace. Since I used environmental data to structure work and rest loops, I aimed to create a system that reminds the user to stay productive while remaining aware of the physical conditions that might be causing cognitive fatigue. For me, this project was a first step into exploring how engineering can be used to optimize workplace ergonomics.  

https://github.com/user-attachments/assets/00bd622e-f7bc-444b-8e4d-cda9394edab9

![IMG_7164](https://github.com/user-attachments/assets/087b4ff6-f4b5-4eff-9c21-29ec739f5f38)

