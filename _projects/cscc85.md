---
layout: project
title: CSCC85 - Fundamentals of Robotics
description: Compilation of every project in this course
---

CSCC85 was divided into a few exercises and 3 major projects (with an optional project 0). Instead of a dedicated links section, I'll walk through each one since they are all pretty unique. A course overview can be fond [here](https://www.cs.toronto.edu/~strider/CSCC85.html) for those interested. All these projects were in groups of 2, my partner being [Noor Nasri](https://github.com/Noor-Nasri)

### Project 0: Chocolate Launcher
The goal here was to get familiar with the tools we would be using in later projects, such as the Legos themselves and the bluetooth API in C. What we were supposed to build was a chocolate launching machine, with points awarded for creativity and 'coolness'. The solution I came up with was a catapult where the release is controlled by rubber bands, and a disengage/reengage mechanism for actually launching.

<video width="200" controls>
    <source src="/assets/videos/Catapult Demo_ CSCC85 Project 0.mp4" type="video/mp4">
</video>

#### Links
- [Github](https://github.com/Choose-the-Napkin/CSCC85_Project0_Catapult)

### Project 1: Lander
The point of this project was to write a control program to successfully land a rover on goal on a surface as shown

![Planet Surface](/assets/images/lander.png)

We were supposed to take into account sensor noise as well as control noise (from the rockets) as well as total failure of any of these components. I can't share tha code since it could easily be copied, so just take my word that we did succeed in most scenarios :)

### Project 2: Robot Localization
In this project, we were to build a robot that could read color mappings on a field so it could figure out where it was, then move to a defined location. This was done using a Markov localization, which uses probabilities to factor both control and sensor error. Below was our robot
![robot](/assets/images/localisation1.png)

<video width="200" controls>
    <source src="/assets/videos/CSCC85 Project 2 Final.mp4" type="video/mp4">
</video>

#### Links
- [Github](https://github.com/Choose-the-Napkin/CSCC85_Project2_Localisation)

### Project 3: Robosoccer
For this project, we were to build a robot to compete in 'robosoccer' - a simplified version of soccer where the goal was to put the ball in a 'net', as can be seen in the videos. The robot I built is as shown. More details about the robot are in the README of the github.
![soccer bot](/assets/images/robosoccer.png)

Field info was given through a computer vision API provided, which ran the control sequence each processed frame of an overhead camera. The robot was autonomous, controlled by a FSM that transitioned with each frame.

<video width="200" controls>
    <source src="/assets/videos/CSCC85 Robosoccer Choose the Napkin Penalty 2.mp4" type="video/mp4">
</video>

<video width="200" controls>
    <source src="/assets/videos/CSCC85 Robosoccer penalty.mp4" type="video/mp4">
</video>

<video width="200" controls>
    <source src="/assets/videos/CSCC85 Scoring on another team.mp4" type="video/mp4">
</video>

#### Links
- [Github Repo](https://github.com/Choose-the-Napkin/CSCC85_Project3_Robosoccer)