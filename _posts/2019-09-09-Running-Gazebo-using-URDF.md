---
layout: post
cover: 'assets/images/cover4.jpg'
navigation: True
title: Running Gazebo using URDF from Solidworks
date: 2019-09-09 22:37:00
tags: Gazebo
subclass: 'post tag-URDF'
logo: 'assets/images/ghost.png'
author: Gilwon Kim
categories: Gazebo
---


### Goals
1. Running URDF model in Gazebo.


OS and Gazebo version of mine are shown below.

1. unbuntu 16.04 LTS
2. gazebo6.desktop





### Instructions

###### 1. Preset.

Drag and drop 'Trycicle' folder in src folder. You could find src folder in home -> catkin_ws -> src.


![1](https://static.wixstatic.com/media/ed6580_9e1ced377ca6428ca771d5ed0c6800a5~mv2.png/v1/fill/w_1920,h_1080/1.png)

We have to edit the code in 'package.xml' to properly run Gazebo. This step is important, skipping this step would make you fail to run Gazebo. 

Open the terminal(CTRL+ALT+T) 

![2](https://static.wixstatic.com/media/ed6580_d1cc2446335746b0849708136935c1a5~mv2.png/v1/fill/w_1920,h_1080/2.png)

Type 'cd ~/catkin_ws/src/Trycycle' in the terminal. You could see that the terminal folder has changed to Trycycle.

![3](https://static.wixstatic.com/media/ed6580_806a70dec7e942d0b038c5bc156bffa8~mv2.png/v1/fill/w_1920,h_1082/3.png)

Type gedit package.xml to change the code inside. We are going to change all of 'depend' in to 'run_depend'.

![4](https://static.wixstatic.com/media/ed6580_664ed05c2de04cbebd638bbe1b36d5e1~mv2.png/v1/fill/w_1920,h_1080/4.png)

The final code for 'package.xml' would be look like below.

![5](https://static.wixstatic.com/media/ed6580_81bdb280c32d43e592fd8534f82afeee~mv2.png/v1/fill/w_1920,h_1080/5.png)

###### 2. Launching Gazebo.

Type 'cd ~/catkin_ws/src/Trycycle/launch' in the terminal. We are going to roslaunch 'gazebo.launch'. 
![6](https://static.wixstatic.com/media/ed6580_71f3411e0efa4740b112cd9879416599~mv2.png/v1/fill/w_1920,h_1080/6.png)

Before launching Gazebo, we have to run 'roscore' in the other terminal. Open the new terminal and run 'roscore'.

![7](https://static.wixstatic.com/media/ed6580_2a67969ed4f84de2b6eb6fb0ca262986~mv2.png/v1/fill/w_1920,h_1080/7.png)

When roscore is running in the back, come back to the original terminal to lanuch URDF model in Gazebo. 

Type 'roslaunch gazebo.launch' in the terminal.
![8](https://static.wixstatic.com/media/ed6580_041cfb6f46014daeacde866baefdbcbe~mv2.png/v1/fill/w_1920,h_1080/8.png)

###### 3. Check URDF model in Gazebo.

You could observe your URDF model in Gazebo. The model should be in one piece if link properties are properly managed when generating URDF in Solidworks. 

![9](https://static.wixstatic.com/media/ed6580_fda91ad8a3f64439a73ff1408e472d25~mv2.png/v1/fill/w_1920,h_1080/9.png)