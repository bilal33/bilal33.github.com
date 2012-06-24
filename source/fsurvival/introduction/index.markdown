---
layout: page
title: "Introduction to functional programming"
sidebar: false
comments: true
---
<link rel="stylesheet" type="text/css" href="/stylesheets/fsurvival.css"/>

<ul style="list-style:none">
<li class="right">
test
</li>
<li style="float: right">
 | 
</li>
    <li class="right">
next
    </li>
</ul>

## Introduction
There are many ways to examine problems and model their solutions. 
In software, we tend to look at problems through the lens of our experiences and the tools that we have at our disposal. 
In other words, our experiences and the tools we know influence how we approach solving problems. 
For example, in the days of structured programming, we solved many problems using procedural decomposition and subroutines, focusing on internal cohesion and loose coupling. 
Building on these successful techniques, we transitioned to modeling solutions using objects and object-oriented techniques, further encapsulating imperative code and its data.

While object-oriented design and object-oriented programming will continue to play a significant role in years to come, 
I believe we are facing challenges that require new ways of thinking and new ways of implementing solutions. 
For example, massive computing power via multi-core architectures and cloud computing will make developing concurrent systems and parallel algorithms a virtual necessity. 
Functional programming provides us with many of the tools and technique we need to make this a reality. 
Additionally, functional programming gives us new ways of developing scalable systems that are easy to debug and test.

## Why This Book?
While there are several books in print, and some Web-based resources for learning F#, I have not found a single one that's altogether clear, concise, and easily digestible by mainstream developers. 
Few, if any, of these resources takes a bottoms-up approach, methodically building up a conceptual and practical framework that builds skills and confidence in a systematic way. 
Additionally, most of the F# materials that I've read are to some extent academic, with a bent towards describing F# in terms of esoteric constructs 
(check out the Maybe monad on the Web for a good dose of newbie confusion!). 
In my (humble) opinion, much of the existing material doesn't resonate naturally with OO application developers. 
These are the issues that I've tried to address with this book.

Also, whenever I read technical books, I ultimately have questions that roll through my head as I go. 
The books I tend to love anticipate my *rolling questions* and answer them quickly and clearly. 
I will do my best to anticipate your rolling questions and answer them in kind. 
I've also made it a point to keep the chapters relatively short, covering one or two related topics at a time.

Lastly, I tend to dislike books that introduce new concepts and syntax without first establishing a solid foundation. 
One of the goals I have for this book is to wait until I've covered a topic before using it in examples, etc. 
I get frustrated when books throw in a new concept in the middle of an example -- it's very distracting and usually takes away from the point that the author is trying to make. 
Therefore, I will use data structures, syntax and concepts only after we've discussed them.  
Because certain language features are so highly interconnected, this may not always be possible; however, I think we can go a long way here.

Instead of lamenting over the dearth of palatable materials and complaining about what I don't like (that's too easy), 
I've decided to do something about it and contribute to the development community as best I can. 
I've chosen this particular topic because I feel quite strongly that functional programming will play prominently in the next decade of computing. 
Why? Two words: multicore processors.

In order to increase compute speeds and throughput cycles, technology manufacturers such as Intel, AMD, Dell, HP, etc. have taken to shipping computers with multiple CPUs and CPUs with multiple cores. 
Given this trend, it is not unreasonable to assume that near-future desktops will contain 8, 16, 32 and more cores.  
Beyond the desktop, there is **the cloud**, with virtually unlimited computing resources available.

In order to take advantage of all this computing power, we developers will need to think differently about how we design and write our software. 
I feel this way because writing concurrent, multi-process, multithreaded, asynchronous applications is already famously difficult, and it will only become more so with the continued scale and 
adoption of compute-rich hardware.

By learning functional programming concepts in the context of a rich, fully-supported language and tool chain, and learning how to apply these properly, 
you are well on your way to preparing for the next generation of software development.

## Intended Audience
This book is intended for professional software developers, students of computer science, and advanced enthusiasts who want to gain a foundation in functional programming and fluency in F#. 
It will be especially useful to those coming from a mainstream imperative/OO background. 
I have found that the *functional guys* love to explain things in mathematical and sometimes obtuse terms. 
I don't think that it's intentional -- it stems from what the Heath brothers call *the curse of knowledge* in their (wonderful) book [Made to Stick](https://en.wikipedia.org/wiki/Made_to_Stick). 
Coming from an imperative/OO background myself, I know how *we* think about problems, hopefully explaining things in terms that are somewhat familiar and comfortable to you.

I assume that you have developed software in the past, and have a working understanding of fundamental programming concepts such as variables, conditional structures, expressions, loops, 
collections, linked lists, etc. 
You will have programmed in C, C++, Python, etc. 
I also assume that you are familiar with at least one object-oriented language such as C++, C#, Java, etc.  
Lastly, to get the most out of this book, you should be familiar with core .NET programming concepts and libraries.

## About the Authors
John Puopolo has been developing software professionally for over 20 years. He started developing on IBM AS/400s in C and quickly moved to the then-new PC platform and Windows (3.1).  
Over the years, John has developed enterprise software for financial institutions, consumer applications, mobile carriers and handset OEMs, enterprise search, GPS and LBS systems, 
and most recently, leads a team in the design and development of a next-generation ad network. 
He has practical and professional experience developing in C, C++, Java, Python, C# and F#. 
He lives outside of Boston, MA with his wife Jill, three daughters, and a funny little dog named Sugar. 
For feedback and comments, please leave a comment on the blog.

Sandy Squires is a software consultant with more than 20 years experience.  
He has worked on developing systems of all different sizes - mainframe, minicomputer, PC, mobile, and embedded in more than 20 different computer languages.  
Sandy enjoys working on scientific and applied engineering systems, especially designing algorithms for digital signal processing, computational geometry, and machine vision.  
He resides in the greater Boston area with his wife, Susan, three daughters, a dog named Chaos, and two cats.

## Useful Links and Resources
While there are many F# resources on the Web, they are at different stages of maturity and complexity. 

As you are coming up to speed, I recommend sticking to a small set of recognized sites, and branching out as you become more comfortable with the material.
In this spirit, I recommend the following sites:

+ [Microsoft F# Developer Center](http://msdn.microsoft.com/en-us/vstudio/hh388569.aspx)
+ [Don Syme's Blog](http://blogs.msdn.com/b/dsyme/) (creator of F#)
+ [F# Programming on Wikibooks](https://en.wikibooks.org/wiki/F_Sharp_Programming)
+ [Real World Functional Programming](http://www.functional-programming.net/) by Tomas Petricek
