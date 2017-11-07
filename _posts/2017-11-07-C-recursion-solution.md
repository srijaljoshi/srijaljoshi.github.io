---
title: "Using recursion to add digits of a number repeatedly"
layout: post
tag:
- programming
- c
- recursion
- function
category: blog
image: 
headerImage: false
author: srijaljoshi
description: "Learn how to construct a simple recursive function to add digits of a number repeatedly"
externalLink: true
publish: true
---
## Repeatedly adding digits of a number recursively

In this post I am going to write a C program that adds digits of a positive integer __repeatedly__ until it becomes a one-digit integer using recursive approach.

First, I'll start with a simple recursive function that adds the digits of a positive interger just once.

<script src="//repl.it/embed/NshP/0.js"></script>

In this solution, the digits of the input integer *x* will be added just once. The recurrence relation involves extracting the last digit and adding it to the result of the recursive call on the number without its last digit.  The base case involves checking whether *x* has been reduced to a single digit. Let me explain the flow of the program below.

The first time *recursive_sum()* is called, 891 is passed as an argument. It checks against the base case and as it is not true, the *else* portion runs. This block of code separates the last digit and adds it with the result of recursive_sum() call on the first two digits i.e 89. In code: ``` 1 + recursive_call(89) ```. The state of the current function call is saved before it jumps to the newer recursive call involving ```recursive_call(89)```. Now, the previous steps repeat until the last remaining digit i.e 8 is separated. Then it checks against the *if* condition which actually tests whether the passed integer is a single digit number. Since, 8 is a single digit, it run the *if* code block and returns the digit itself i.e. 8 to previous instance of *recursive_sum()*. 
