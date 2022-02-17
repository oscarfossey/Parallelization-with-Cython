# Parallelization-with-Cython

*Oscar Fossey (ENSAE), [Charles Caneilles](https://github.com/ccaneilles) (ENSAE)*

## Goal ##

Parallelization of computations using Cython to speed up the image generation of a rotating 3D object. Application to the rotation of a 3D Cube. We aim to vizualise how fast a Cython program will be next to a Python programm. To visualize image generations seems suited.

## Motivation##

Python is by far the programmation language with the most useful packages for Data Science and Machine Learning. However it is very slow comparing to other languages. This project aimed to visualize the difference of speed between Cython and Python.

## Python version for rotating the Cube ##

The goal is to rotate a 3D shape around an axis. The application will be done with a function defining a cube with the axis that vertically crosses it in its center.

- R0 reference of the space in which the curve will turn
- RC space of the curve where the curve is centered in [0,0,0]
- Rpix space of the pixels on the 2D plane [u,v].

**Explanatory diagram of the program :**
![alt text](https://github.com/oscarfossey/Parallelization-with-Cython/blob/main/Images/python_diagram.JPG)

To go trough this space we have a 3D step of [[eps_x],[eps_x],[eps_x]], thus the complexity of our algorithme in O(1/(eps_x^3)).

## Cython Version ##

**Explanatory diagram of the program :**
![alt text](https://github.com/oscarfossey/Parallelization-with-Cython/blob/main/Images/cython_diagram.JPG)

We have parallelized with the **function cython prange**, to improve the speed we will also disable the gill with **nogil = True**.

Moreover with cython we can desactivate the bounds checking and the negative indexing to speed up even more.

**Differences in the code :**
![alt text](https://github.com/oscarfossey/Parallelization-with-Cython/blob/main/Images/code_diagram.JPG)

## Speed up ##

By definition the speed up is the time of execution of the python version devided by the time of the cython version. The measurement have been made with 110 computatations with 11 differents epsilons of the main function.

**WARNING : Be carefull the results about the the Speed up can largely change with the machine.**

Obviously the speed up is still huge on every machine. We invite you to plot the diagram with your own machine by executing our code.

**Speed up results on our machine :**
![alt text](https://github.com/oscarfossey/Parallelization-with-Cython/blob/main/Images/speedup%20diagram.JPG)

## Visualization of the Speed up between the two outputs##

Using the speed up score measurement we can simulate the speed difference between the two program. When executing the program  we can see that the cython version rotate smoothly while the python version struggle to do one single frame.

## Used packages ##

![alt text](https://github.com/oscarfossey/Parallelization-with-Cython/blob/main/Images/Packages.JPG)

## Credits ##

This project as been made and lead by Oscar Fossey and [Charles Caneilles](https://github.com/ccaneilles)
