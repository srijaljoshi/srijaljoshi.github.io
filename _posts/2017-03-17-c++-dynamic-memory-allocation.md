---
title: "Demystifying dynamic memory allocation in C++."
layout: post
tag:
- programming
- c++
- dynamic memory allocation
- fundamentals
category: blog
image:
headerImage: true
author: srijaljoshi
description: "Learn dynamic memory allocation and deallocation with me"
externalLink: false
publish: true
---

I will begin my first post by examining and explaining how dynamic memory allocation works in C++.
First, let me define two concepts related to memory (RAM): **Stack** and **Heap**.

Think of Stack as a place to store records of local variables and functions. The Stack (few KBs or MBs in size) is significantly smaller in size compared to the Heap (as much free RAM as you have - GBs). You have no control over the stack; it is managed by the compiler. Remeber how you don't have to manually destroy local variables after creation? The compiler does that for you.

Enter Heap. This is the part of your computer's memory that is available for you to request (allocate) and revoke (deallocate).

Let's see how you can allocate memory for a variable in C++.
{% highlight c++ %}
int* ptr = new int; // new allocates a memory location in the Heap
{% endhighlight %}

The `new` operator is used to request a chunk of memory from the OS, for the current program. It then returns the address of the allocated memory location. This location is then stored on the integer pointer variable `ptr`. Now the local variable `ptr` will hold the address of the memory location that is in the Heap - something like `0xfffc20`. This should be different in your case. To find out type the following:
{% highlight c++ %}
cout << "Heap location held by ptr: " << ptr << endl;
{% endhighlight %}

Now you can use `ptr` to change states by changing the value in the memory location. You may want to do something like
{% highlight c++ %}
*ptr = 345; // any valid int value is okay
{% endhighlight %}

All this time the location held by `ptr` was at your program's disposal. If you do not free this memory, then you will run into [memory leaks][1]. This happens because you ask the OS for the memory and use it. Now if you do not return it back, the OS will have less of it to distribute to other programs, thus affecting performance. So, let's deallocate the the memory using `delete` operator.
{% highlight c++ %}
delete ptr;
{% endhighlight %}
Thus, deallocation takes place; the memory held by `ptr` is returned to the OS. Note that you can still refer to the address on the heap using `ptr` but it is no more under your control. Modifying it after deallocation will result in unexpected behavior.

You can running the code below and see what's going on.

<script src="//repl.it/embed/GYmJ/5.js"></script>

Please leave your comments below if you have anything to say (questions/suggesstions).



[1]: https://en.wikipedia.org/wiki/Memory_leak
