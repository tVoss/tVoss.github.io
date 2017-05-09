---
layout: post
title: "Linux for Everyday Use"
categories: linux
---
Back in high school I had way too much free time on my hands, and at the same time my family had an old computer laying around. This meant I was free to tinker, take apart, break, manipulate, and miraculously fix it all I wanted. As with a majority of computers at the time, it ran Windows. At school however, our computers ran this *thing* macOS which had similar functionality, but acted totally different. It seemed like it should be easy to get this thing on to my computer right? In a frantic search to accomplish this, I ended up down the rabbit hole of Linux which completely changed the way I used computers.

While my friends certainly weren't tinkering with their computers, they were subject to hearing about all the headaches and hurdles I encountered as I continued to mess around with mine. Of course there was a payoff as my nights of confusion often led to performant game servers on ancient computers for them, along with a passing knowledge of what those servers ran on. After going to college and meeting new people who hadn't heard my endless ramblings, I'd often get the question "What do you mean you run Linux?" whenever I'd start geeking out about my computer. I'm going to try to pick apart what running Linux means, and potentially make you reconsider what runs on your next computer. But first...

### Some Terms

**Operating System**

This is the base that every type of consumer grade computer comes with, and I guarantee you've used at least two different ones in the past day. The mobile phone market is controlled by iOS and Android. For desktops and laptops the market is populated with Apple's macOS running on all Macs, and Microsoft Windows on just about everything else. Included in these Operating Systems are mechanisms for adding and removing programs, the ability to tweak setting that have a global impact, as well as a collection of tools that most users take for granted.

| Tool                   | Windows              | macOS            |
| :--------------------: | :------------------: | :--------------: |
| Graphical File Manager | Explorer             | Finder           |
| Web Browser            | Edge                 | Safari           |
| Music / Video Player   | Windows Media Player | Quicktime Player |
| Text Editor            | Notepad              | TextEdit         |
| Command Line           | Command Prompt       | Terminal         |

<p style="text-align: center">
    <em>Some common utilities nearly everyone uses</em>
</p>

Now a nice suite of programs with the ability to add more is convenient, but what makes it special? Why can't someone just put the macOS programs on Windows, or vice versa? That's actually the case for some of those programs! Why not all of them? This description of an Operating System as a collection of important programs isn't quite complete without the element at the core...

**The Kernel**

<p style="text-align: center">
    <img style="width:400px;margin:5px 20px" src="{{ "/assets/img/corn-kernel.jpg" | prepend: site.baseurl }}" alt="Corn System Kernel" />
    <img style="width:300px;margin:5px 20px" src="{{ "/assets/img/kernel.png" | prepend: site.baseurl }}" alt="Operating System Kernel" />
    <br />
    <em>Two different kernels, both at the center of everything</em>
</p>

If the hardware is the brains of your computer, the kernel is the heart, keeping everything moving. It is what dictates what software is run, how it's run, and how that software has access to the hardware. The kernel has complete control over your computer, handing out control to everything else in discrete, traceable pieces. You wouldn't want some random website code to have complete access to your hard drive, and the kernel has conventions to ensure this doesn't happen. Different conventions lead to different bits of code needed interacting with the kernel. Let's take a look at a very basic program written in the language C.

```c
#include <stdio.h>

void main()
{
    printf("Hello World");
}
```
<p style="text-align: center">
    <em>No matter how much I learn I still have to search for a Hello World program</em>
</p>

Those without programming experience don't worry, this will be light. There's three important lines in this program that all say distinct things:

`#include <stdio.h>`: "I'm going to need things later that are defined in a file called **stdio.h**" (stdio stands for Standard IO)

`void main()`: "This is where the program starts and don't expect anything from me when I'm done"

`printf("Hello World");` "Call the function `printf` along with the text *Hello World*" (Defined in **stdio.h**)

The end result is the text *Hello World* being printed to screen, which is simple enough. A question that remains is how does `printf` know how to do this? The answer lies in the included file, happily abstracted away by the compiler for this simple program. Inside **stdio.h** is code for writing text to the screen that is specific to your kernel. Kernel A may have one function you have to call for writing text, while Kernel B may handle it a completely different way, it all depends on how they were designed. When trying to interact with more complicated aspects of the kernel such as graphics cards, hardware access, and user settings things can become much more complicated. This is what leads to some high end software only being developed for certain platforms.

**Licenses**

Code is a product of humans, and as with most thing humans make, they want credit for it. In the physical world this is handled by patents, in the intellectual work this is handled with copyrights and trademarks, and in the code world this is handled by licenses. At the end of the day, code is just text that is transformed into something functional by other tools. While the function is the final product and what is usually the main selling point, the text still needs to be protected. For the sake of our discussion there are two main licenses at play taking care of this.

* Proprietary License - This code belongs only to the person or company who first created it. No one is allowed to read or modify the code without permission from the sole owner. This is the license Microsoft and Apple go with.
* General Public License - This code is free and open for everyone to use. However, if you use this code in your project, then your code must also be free and open for everyone to use under the same conditions. The GNU Project and Linux use this.

Clearly these two options are polar opposites and will lead to very different evolutions of programs. Of course there are options that cut it down the middle, but instead of wasting time with that let's talk about...

### Some History
