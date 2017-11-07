---
title: Using recursion to add digits of a number
layout: post
tag:
  - programming
  - c
  - recursion
  - function
category: blog
image: null
headerImage: false
author: srijaljoshi
description: >-
  Learn how to construct a simple recursive function to add digits of a number
  repeatedly
externalLink: true
publish: true
published: true
---
## Adding digits of a number recursively

In this post I am going to write a C program that adds digits of a positive integer recursive approach.

First, I'll start with a simple recursive function that adds the digits of a positive interger just once.

<script src="//repl.it/embed/NshP/0.js"></script>

In this solution, the digits of the input integer *x* will be added just once. The recurrence relation involves extracting the last digit(done using ```x mod 10```) and adding it to the result of the recursive call to the number without its last digit(done using ```x / 10```).  The base case involves checking whether *x* has been reduced to a single digit. Let me explain the flow of the program below.

The first time *recursive_sum()* is called, 891 is passed as an argument. It checks against the base case and as it is not true, the *else* portion runs. This block of code separates the last digit and adds it with the result of recursive_sum() call on the first two digits i.e 89. In code: ``` 1 + recursive_call(89) ```. The state of the current function call is saved before it jumps to the newer recursive call involving ```recursive_call(89)```. Now, the previous steps repeat until the last remaining digit i.e 8 is separated. Then it checks against the *if* condition which actually tests whether the passed integer is a single digit number. Since, 8 is a single digit, it run the *if* code block and returns the digit itself i.e. 8 to previous instance of the recursive call, that is, ```recursive_sum(8)```. Now, the previous saved instance of the recursive function, that is, ```recursive_sum(89)``` runs, and evaluates ```9 + recursive_sum(8)``` where ```recursive_sum(8)=>8```. Thus, the expression is now ```9 + 8```. After evaluating ```recursive_sum(89) => 17```, the previous call i.e. ```recursive_sum(891)``` is resumed. The call to ```recursive_sum(891)``` actually evaluates ```1 + recursive_sum(89)``` which is, ```1 + 17```, thus giving us the answer => 18.