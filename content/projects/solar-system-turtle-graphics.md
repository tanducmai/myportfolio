+++
date = "2021-08-25"
title = "Solar System Turtle Graphics"
slug = "solar-system-turtle-graphics"
thumbnail = "images/solar-system-turtle-graphics.jpg"
description = "Solar System Turtle Graphics"
tags = ['python']
categories = ['python']
aliases = "/solar-system-turtle-graphics/"
+++

### → [GitHub](https://github.com/tanducmai/solar-system-turtle-graphics)

### Table of Contents

1. [Aim](#aim)
1. [Implementation](#implementation)
1. [Output](#output)
1. [Video Production](https://raw.githubusercontent.com/tanducmai/solar-system-turtle-graphics/main/assets/video_production.mp4)

### Aim

Use Turtle graphics to draw an illustration of the Solar System, with
appropriate scaling.

### Implementation

There are two algorithms that I constantly use when working with a Python Turtle
project, which is making a turtle and moving it. Accordingly, I define the two
functions to eliminate repetitive code and put them into a new Python file. This
is to make it possible to break up such a large program into manageable sized
parts, and to keep related parts together. I then use the import statement to
use those functions in the **main** module.

Firstly, since I use a scale of 1 : 2,000,000,000,000 (turtle unit :
centimetre), I create a variable called *scale*, and assign 2,000,000,000,000 to
it. Next, I create a list of eight planets with four elements being (the name of
the planet, distance from each planet to the sun (measured in million
kilometres), colour of the planet, orbital period (measured in Earth days).

I now set the window and write the title on the top right corner of it. After
that, I come to the left-right corner to write the scale I use for the
representation with a border around it.

Regarding the main representation, I first draw the kernel, which is the Sun,
simply really small (r = 25) and coloured in yellow. Afterwards, it comes to the
drawing of eight other planets, I first create two variables: set *x* to 25 and
set *size* to 2 for further usage. I now use a for loop to iterate over the
defined list of eight planets, with each element being called name, distance,
colour, days. This allows me to draw each planet one by one, from the one
closest to the sun to the farthest.

As for each planet:

```text
1.  Choose its colour from the defined list.
2.  The first planet being drawn has its pen size equal to size = 2.
3.  Scale the actual distance from the sun by 1 : 2,000,000,000,000.
4.  The calculation {distance * 10 ** 6} makes it become million kilometres.
5.  Then * 10 ** 5 makes it become million centimetres
6.  Then / scale and we get the scaled distance.
7.  Use the user-defined function to move the turtle down –x – distance, so that
    each planet it shows the relative distance between each planet. The –x means
    the further subtract the distance by the sun radius.
8.  Now draw a circle with radius x + distance and we get the representation of a
    planet.
9.  The below code is used to set the turtle into the right position before the
    next iteration.
10. Lastly, add 25 to x and 1.5 to size to the space between each planet is
    equal before subtracting it with the scaled distance and to increase the pen
    size by 1.5 every iteration.
```

The last part is to go to the right side of the window and draw a legend table.
I again use the same for loop iterating over the defined list of eight planets.

### Output

![The output of the program](/images/solar-system-turtle-graphics.jpg)

### Video Production

[Execute the **main**
module](https://raw.githubusercontent.com/tanducmai/solar-system-turtle-graphics/main/assets/video_production.mp4)
