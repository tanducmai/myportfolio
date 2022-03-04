+++
date = "2021-08-12"
title = "Three Different Prime Checker"
slug = "three-prime-checker"
thumbnail = "images/three-prime-checker.jpg"
description = "Three Different Prime Checker"
tags = ['python']
categories = ['python']
aliases = "/three-prime-checker/"
+++

### → [GitHub](https://github.com/tanducmai/three-prime-checker)

### Table of Contents

1. [Introduction](#introduction)
1. [Algorithms](#algorithm)
1. [Sample Output](#sample-output)

### Introduction

I came up with three different algorithms for determining whether a number is
prime. After running the three, I use a special procedure to time the efficiency
of each algorithm to find out which is better than another. The core of this
project is to adopt different perspectives on a problem, with each way of
handling a problem will have pros or cons over another.

### Algorithms

```text
1. Exclude n if n<2. Now, find its square root, then use a for loop in the range
   between 2 and the square root + 1. If there is no number in the loop that is
   divisible by n, then n is prime.
2. Exclude n if it is less than or equal to 1.
      -   If it is equal to 2, it is prime.
      -   If n is greater than 2, use a for loop in the range between 2 and n,
          if there is not any number in the loop that is divisible by n, then n
          is prime.
3. Firstly, set an initial variable divisible equating to 0. Secondly, use a for
loop in the range between 1 and n+1; if any number in that loop is divisible by
n, add 1 to the variable divisible. When the loop is finished, if the variable
divisible is equal to 2 (means only 1 and n is divisible by n), then n is prime.
```

### Sample Output

-> [PDF
Version](https://raw.githubusercontent.com/tanducmai/three-prime-checker/main/sample_output.pdf)

```text
A program to check if a number is prime.
Return True if it is, False otherwise.
Also compares which function is the fastest.

Enter a number for evaluation: 9999999
-----------------------------------------------------------------------
9,999,999 is False
In a list of all prime numbers less than 10,000:
The first ten are: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
The last ten are: [9887, 9901, 9907, 9923, 9929, 9931, 9941, 9949, 9967, 9973]
Function A: time taken = 0.028 seconds.
-----------------------------------------------------------------------
9,999,999 is False
In a list of all prime numbers less than 10,000:
The first ten are: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
The last ten are: [9887, 9901, 9907, 9923, 9929, 9931, 9941, 9949, 9967, 9973]
Function B: time taken = 0.6074 seconds.
-----------------------------------------------------------------------
9,999,999 is False
In a list of all prime numbers less than 10,000:
The first ten are: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
The last ten are: [9887, 9901, 9907, 9923, 9929, 9931, 9941, 9949, 9967, 9973]
Function C: time taken = 7.2864 seconds.
```
