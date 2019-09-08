---
layout: post
cover: 'assets/images/cover4.jpg'
navigation: True
title: Welcome to the instruction of URDF 101
date: 2019-09-07 02:18:00
tags: education
subclass: 'post tag-URDF'
logo: 'assets/images/ghost.png'
author: Gilwon Kim
categories: URDF
---



# Welcome to the instruction of URDF 101

### Goals
1. Set the boundary conditions in Solidworks for URDF.
2. Generate URDF files from Solidworks.

Below instructions would walk you through the whole steps to generate URDF model from the SolidWorks. 

You may need following to acheive the goals: 
1. Solidworks program
2. Solidworks assembly parts
3. Solidworks SW2URDF add-ins





### Instructions

###### 1. Get SolidWorks model ready
The model consists of four parts(Body, Load, Right Wheel, Left Wheel, and Front Wheel). These parts are free to download [here](http://). The assembly parts should be properly mated as a functioning piece to carry URDF translation successfully. 

![1](https://static.wixstatic.com/media/ed6580_5b60591ba852432583b70adb9389de89~mv2.png/v1/fill/w_1601,h_800/1.png)

###### 2. Set the 'axsis' and 'point' of the parts
Setting the coordinate system is very important in URDF conversion. The wheel parts must have 'points' along with the centeral axsis, because we will apply 'continuous' boundary condtion on the wheel. I created the 'axsis' and the 'point' at the center of the wheel. 

![2](https://static.wixstatic.com/media/ed6580_691fb367f1a949c0b8781d21afdeeae3~mv2.png/v1/fill/w_1600,h_800/2.png)

###### 3. Set the coordinate systems
Come back to the assembly model. Find 'Coordinate System' from the menu.

View -> Reference Geometry -> Coordinate System

![3](https://static.wixstatic.com/media/ed6580_bc1e7ec3aa1940a998db36ac7f68a917~mv2.png/v1/fill/w_495,h_727/3.png)

Select the point and axsis as it is shown below to create the coordinate system. 

**Sidenote. You could select the coordinate system anywhere along the axsis line at the center. As long as the coordinate system is along the center axsis of the wheel, you are fine.*

![4](https://static.wixstatic.com/media/ed6580_00dda885e5dd4f8698d1c86b54cb752f~mv2.png/v1/fill/w_1600,h_801/4.png)

Once it is done, you can see the coordinate system as below in the assembly model. 

![5](https://static.wixstatic.com/media/ed6580_16318b27e446431ea92b6add56a12b05~mv2.png/v1/fill/w_1600,h_802/5.png)

Likewise, set the coordinate systems on the other wheels, body, and load parts. **You have to remember that all the coordinate systems must be set in the assembly model tree.**

The photo below shows the coordinate system of Body part. You could set the coordinate system anywhere you want unlike the wheels. 

![6](https://static.wixstatic.com/media/ed6580_18c663d8743f4ccf843c5d1bcf7bf9cf~mv2.png/v1/fill/w_1601,h_800/6.png)

The photo below shows the coordinate system of Load part. You could also set the coordinate system anywhere you want in the part. 

![7](https://static.wixstatic.com/media/ed6580_c39defb3e7fc4c4e8fcdc70756301678~mv2.png/v1/fill/w_1599,h_801/7.png)

###### 4. URDF conversion
Solidworks could convert URDF with URDF add-ins(SW2URDF). SW2URDF add-ins must be installed in Solidowrks.

These five coordinate systems must be seen in your assembly tree. 

The names of each coordinate system to the parts are represented as follow:

Coordinate System2 <- Right Wheel part

Coordinate System3 <- Left Wheel part

Coordinate System4 <- Front Wheel part

Coordinate System5 <- Body part

Coordinate System6 <- Load part
**Sidenote. Your coordinate system names may different than mine. You could change the names of coordinate systems to the above names to easily understand the rest of parts.*

**I am going to set 'Load part' to be ++the parent link++ of all.**

![8](https://static.wixstatic.com/media/ed6580_9b1d73d3a582468b9b80858f3eaa4395~mv2.png/v1/fill/w_1599,h_803/8.png)

Open URDF setting tool.
File -> Export as URDF

Once you open URDF Exporter, we will firstly manage 'Number of child links' to set the hierarchy of links. 

Set 'Number of child links' to 1 for Load part, and set 3 child links for Body part. You can see the final hierarchy tree as it is shown below.

For Load part,
1. Change 'Global Origin Coordinate System' to Coordinate System6.

![9](https://static.wixstatic.com/media/ed6580_bb447341c521487ba72b5dcab0483e33~mv2.png/v1/fill/w_1600,h_801/9.png)

For Body part,
1. Change 'Reference Coordinate System' to Coordinate System5.
2. Change 'Joint Type' to fixed.

![10](https://static.wixstatic.com/media/ed6580_0f2bdd7cf74c4cdea9df9d37ece57f1c~mv2.png/v1/fill/w_1600,h_802/10.png)

For Right Wheel part,
1. Change 'Reference Coordinate System' to Coordinate System2.
2. Change 'Joint Type' to continuous.

![11](https://static.wixstatic.com/media/ed6580_88622a4f03e849029470dfd02db96456~mv2.png/v1/fill/w_1604,h_800/11.png)

For Left Wheel Part,
1. Change 'Reference Coordinate System' to Coordinate System3.
2. Change 'Joint Type' to continuous.

![12](https://static.wixstatic.com/media/ed6580_5cf06c41d8a04ab889ca2a9407a71c4e~mv2.png/v1/fill/w_1600,h_801/12.png)

For Front Wheel part,
1. Change 'Reference Coordinate System' to Coordinate System4.
2. Change 'Joint Type' to continuous.

![13](https://static.wixstatic.com/media/ed6580_8e1d7fe8e614468aa2984562c74b7efe~mv2.png/v1/fill/w_1602,h_800/13.png)

Once all the boundary conditions are set, hit 'Preview and Export' button, and URDF Exporter will bring up another pop-up window. Click Next button.

![14](https://static.wixstatic.com/media/ed6580_5a19da0c0f2c4befb034cf8d015e1cc3~mv2.png/v1/fill/w_1602,h_804/14.png)

The properties below are to manage the physics conditions of the model. You could set the properties and conditions as you intended. In this instruction, I only changed the mass(kg) to 1kg of all parts.

![15](https://static.wixstatic.com/media/ed6580_ab1bf54b658a459684a5bca2d06d12c1~mv2.png/v1/fill/w_1600,h_802/15.png)

Hit 'Export URDF and Meshes..." button to create and save URDF files of the model.

![16](https://static.wixstatic.com/media/ed6580_3121724bf5f7461ea0dd5d7545bd8b0a~mv2.png/v1/fill/w_1601,h_801/16.png)

I saved URDF files with the name of 'Tricycle'. Congratulations, you have your URDF files.

Next, the instruction will be continued with running URDF model in gazebo.