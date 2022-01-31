---
title: "Prime Checker"
date: 2021-12-26T02:27:17+10:30
draft: false
---

# 3 different ways to check if a number is prime.

I came up with three different algorithms for determining whether a number is prime, each of which is therefore coded differently:

1.	Exclude n if it is less than 2. Now, find its square root, then use a for loop in the range between 2 and that square root plus 1. If there is no number in the loop that is divisible by n, then n is prime.
2.	Exclude n if it is less than or equal to 1.
      -   If it is equal to 2, it is prime.
      -   If n is greater than 2, use a for loop in the range between 2 and n, if there is not any number in the loop that is divisible by n, then n is prime.
3.	Firstly, set an initial variable divisible = 0. Secondly, use a for loop in the range between 1 and n plus 1, if any number in that loop is divisible by n, add 1 to the variable divisible. When the loop is finished, if the variable divisible is equal to 2 (means only 1 and n is divisible by n), then n is prime.

In order to create a list of all prime numbers less than 10000 from those defined functions, I first make an empty list, then use a for loop in the range between 2 and 10000. If i fits the defined function, append i to that list. The same procedure is done for all three algorithms. After having the list of all prime numbers less than 10000, I slice it using the operator [n:m]  to print the first ten and the last 10 prime numbers of it.

I use the time module to measure the time taken to perform each function (including determining if the number is prime, creating the list of all prime numbers less than 10000 using the function, and printing the first and last ten numbers of the list). Taking n = 9999999 as an example, function a takes 0.0159 seconds, function b takes 0.8068 seconds, and function c takes over 9 seconds.

Since function a works on the square root which greatly minimises the range of the for loop, it takes by far the shortest time to run.

Since function a and function b are quite similar (they all use a for loop and divides n by the number i from the loop), function b also takes less time (less than 1 second). Nonetheless, as function a works on the square root of n, this makes it considerably quicker than function b.

Lastly, function c takes the longest time (over 9 seconds) because it takes an additional step which is working with the variable divisible. Therefore, the bigger the number n becomes (like 9999999), the longer the time taken.

# Output
![A typical example](output.jpg)

