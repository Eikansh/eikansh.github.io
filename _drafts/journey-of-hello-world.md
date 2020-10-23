---
layout : post
title : Journey of “hello world\n”
---

I wrote my first code 7 years ago. Many of you may have guessed it was our beloved “hello world.cpp” program. 

Screenshot of program in Turbo C++.
Yeah I used Turbo C++, judge me for that.

When I first compiled and executed the program, I couldn’t grasp what I have just seen on the screen. Well it just printed “hello world”, but all the technical details and human efforts that went into seeing these shining pixels on the screen was unfathomable.
3 years back I asked a question to myself, “What really happens when we run a program?” I couldn’t find the answer but this question 
Now I can’t express in words how amazed I am ...... but I can explain what happen under the hood and maybe through that you may get my enthusiasm.

Gracy hopes
Imagined how she would have compiled the compiler without the compiler(hint : bootstrapping)  

Structure
Intro
How prog is run : os compiler diagram
what is compiler
from c to prog
Compiler steps
history of gnu

objdump -t ./a.out for symbol table
objdump -h ./a.out for program header
objdump -d ./a.out for disassembly
gcc -S hello_world.c  to get assembly file
strace ./a.out 

System calls are like waiters (which lets you order the dishes which kernel can offer)in a restaurent, you just give the order and it is there task to fulfill it.

Thank you for being on this journey. This journey is so fascinating and long that multiple books will fall short to complete it. Consider this post as a map because this journey has to be taken alone. I have tried to include some links in the post, follow them to learn more or join a graduate program like me to know more about it. 
