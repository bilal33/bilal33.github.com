---
layout: page
title: "Introduction to functional programming"
sidebar: false
comments: true
---
<link rel="stylesheet" type="text/css" href="/stylesheets/fsurvival.css"/>

<ul style="list-style:none">
<li class="right">
<a href="\fsurvival\next">next</a>
</li>
<li style="float: right">
 | 
</li>
    <li class="right">
<a href="\fsurvival\introduction">previous</a>
    </li>
    <li style="float:right">
    |
    </li>
    <li class="right">
    <a href="\fsurvival\toc">Main</a>    
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


## What is Functional Programming?
Functional programming is a specific way to look at problems and model their solutions. 
Pragmatically, functional programming is a coding style that exhibits the following characteristics:

* power and flexibility -- we can solve many general real-world problems using functional constructs
* simplicity -- most functional programs exhibit a small set of keywords and concise syntax for expressing concepts
* suitable for parallel processing -- via immutable values and operators, functional programs lend themselves to asynchronous and parallel processing

Functional programming treats computation, e.g., running a program or solving a numeric calculation, as the evaluation of functions. 
Not surprisingly, in dealing with functional programming, we will use the term function quite often and in many contexts. 

So, before we continue, let's make sure we understand what a function is:

*A function is fundamentally a transformation*. It transforms one or more inputs into exactly one output.

An important property of pure functions is that they yield no side effects. 
This means that the same inputs will always yield the same outputs, and that the inputs are not changed as a result of the function. 
This idea of *no side effects* is one (of several) that makes functional programming particularly attractive when writing multi-process and multithreaded systems. 
As we go through the book, I will point out and explain the key concepts that make functional programming attractive for solving certain types of problems.

####Purely Functional?
>Some programming languages are *purely functional languages.* This means that they follow strict functional rules, e.g., 
no imperative looping constructs and no implicit way to introduce state changes. 
For example, Haskell, a pure functional language, disallows state changes and side effects altogether. 
Programs written in pure functional languages are almost solely made up of functions that accept arguments and return values. 
Unlike imperative and object-oriented languages, they allow no side effects and use recursion instead of loops for iteration. 
Languages like Haskell are often criticized as being too extreme in not allowing side effects, giving them limited penetration in mainstream development environments.  
Operations such as reading a file become awkward to code in a language where no side effects are allowed. 
In contrast, impure, multi-paradigm languages such as F# discourage side effects and imperative constructs, but make them available alongside their functional brethren.


From the abstract mathematical theory of functions comes a variety of interesting concepts that have broad application and use in functional computing. 
For example, functions can take other functions as arguments, and functions can return other functions as results.  
This ability results in flexible and powerful mechanisms that enable us to implement ideas simply and elegantly -- ideas that are difficult to express in non-functional languages. 
We explore these mechanisms throughout the rest of the text.

##Functional vs. Imperative
We can think of imperative programming as writing code that describes in exacting detail the steps the software must take to execute a given computation. 
These steps are generally expressed as a combination of statement executions, state changes, loops and conditional branches.

In contrast, functional programming looks at a program as a set of nested functions -- one *outer* function (the program) calling one or more *inner* functions to calculate a value to be returned as 
the result of the program. 
Functions take arguments and calculate return values, but do not maintain a *state of the program* per se.

Most modern programming languages support sufficient logic and data storage as to make them [Turing complete](https://en.wikipedia.org/wiki/Turing-complete). 
This means that in principle they can be used to write programs to solve any *computable* problem. 
F# is also a Turing complete language. The crux of choosing a language is not then one of capability, but of inherent applicability.

F# offers some advantages over other languages when working on certain classes of problems. 
Some general strengths of F# are as follows:

* The signal-to-noise ratio is high. F# is economically expressed, e.g., favoring whitespace over other grouping symbols. As a result, your code ends up being quite succinct.
* Powerful matching logic based not only on Boolean values but the *shape* and type of the data.
* Built-in support for *lazy evaluation* of expressions.
* Built-in support for writing thread-safe and asynchronous applications very simply via asynchronous workflows.

To help make things a little more concrete, and whet your appetite for the material to come, 
let's consider a few examples that help contrast how we'd look at and solve the same problem from the imperative vs. the functional perspective.

###Example 1: Filtering a List
Let's suppose we have a list of 10000 employee records in a list, and we want to find all the employees who salary equals or exceeds 100,000 dollars. 
Taking the imperative approach, we would most likely write a for- or while-style loop, examining each employee's salary to see if it met our criteria. 
For each employee meeting the criteria, we would append the record to a growing list of matches. As you can see, we delineate each and every step in detail.  
In contrast, from a functional perspective, we would describe this solution as applying a filter (function) to a list with the goal of producing a new resulting list.

###Example 2: Downloading Files Asynchronously
Asynchronous and parallel programming are difficult to do and even more difficult to get right. 
For example, to asynchronously download HTML pages from the Web via imperative languages requires us to create HTTP channels, issue asynchronous calls, 
write completion routines, and manage failures. 
Depending on the implementation, we may need to also manage our own threads. 
This results in a lot of complex, error-prone code. 
While we can't escape having to perform these tasks in some way, we can manage them much more succinctly and rigorously in functional languages by 
structuring and sequencing the calls using a concept called workflows.

###Example 3: Customizing Algorithms
A classic problem that functional languages address elegantly is that of arbitrary value comparison. 
When your program needs to sort or compare values, it needs a mechanism to determine whether two values are *equal* or 
if one value is *less than* the other. 
When using naturally ordered elements, such as numbers or letters, the natural ordering applies. 
In many business-style programs, however, we need to compare elements that have no natural ordering, e.g., Employees, Automobiles, Tickets, Movies, Concerts, etc. 
In these types of applications, it's extremely convenient to supply a comparison or sorting function that can be subsequently executed against two elements. 
This is one of the most powerful capabilities of functional programming -- the ability to not only pass and return simple values, but the ability to pass and return functions.

To solve this problem in a functional language, you merely pass the main comparison function a *sort function* that it can use to compare two elements. 
Depending on the context of the application, or the types being sorted, the program can pass along different *sort functions* without changing the main routine whatsoever. 
Functional languages tend to exhibit this compositionality in most aspects of their design and, ahem, function.

To address this problem in traditional imperative languages, we'd need to resort to function pointers or similar constructs. 
Again, this is possible to do, but not as clean or elegant as it can be. 
We should note here that C# now ships with some functional constructs, including anonymous functions and lambda expressions, which help to elegantly address this type of problem.

###Example 4: Creating Infinite Sequences
There are certain data sets that are *naturally infinite*, e.g., the set of all prime numbers, making their complete calculation impossible. 
Functional languages employ mechanisms such as lazy evaluation and delayed computation to make infinite sets both representable and efficiently computed in on-demand fashion. 
Again, while you can accomplish the same things in non-functional languages, the imperative implementations tend to be *less natural* and more convoluted.

##What Problem Spaces are Naturally Addressed by Functional Programming?
Growing up, I'd occasionally help my dad fix things around the house, paint, etc., and from the many things he taught me, *the right tool for the job* stands out clearly. 
When faced with a problem, you need to consider what you have in your *toolbox* and decide the best way to solve it. 
Certain problems can be solved easily with a hammer, whereas with others you need a saw. You need to apply the same thought process to choosing programming paradigms and the languages that support them.

Functional programming is appropriate for applications that exhibit one or more of the following characteristics: 
require significant computation (compute-bound) as they can be parallelized easily, are themselves parallel in nature, 
can benefit from asynchronous calls, need to be provable, or require sophisticated pattern matching. 
This means that functional programs are not generally applicable to typical line-of-business applications that deal with objects and their state over time; 
however, there may be portions of those programs, e.g., portfolio basket optimization for fixed-income securities, 
that would benefit greatly from using functionally-based libraries.  
We typically see functional programming applied to image processing, machine algebra, lexing and parsing, artificial intelligence, and data mining.

##Why Should I Care About Functional Programming?
While you can develop concurrent, scalable and asynchronous software without embracing functional programming, it's simpler, safer, and easier to use the right tool for the job. 
Functional programming enables you to take advantage of multi-core systems, develop robust concurrent algorithms, parallelize compute-intensive algorithms, 
and to readily leverage the growing number of cloud computing platforms.

In addition, if you've not already explored non-imperative programming, it's a great way to expand your problem solving skills and your horizons. 
The new concepts that you'll learn will help you to look at many problems from a different perspective and will help you to become a better and more insightful OO programmer.

A note of caution: I am not here to convince you how wonderful functional programming is, or how it will change your life. 
It is a tool -- nothing more, nothing less -- that helps to solve a certain class of problems. 
In this book, we will explore and explain these types of problems, and point out why functional programming applies.

We will explore functional concepts in depth in Chapter 8, Functions and Functional Concepts.  
To build up to that, we will first study F#'s syntax, primitive data types, control flow structures, loops, and basic collections.

Note: Each chapter ends with a What You Need to Know section, which is the thumbnail summary of the topics covered. Here's one now...

##What You Need to Know

* Functional programming is a way to implement software solutions. We contrast it with imperative and OO programming.
* Functional programs implement computation as nested and successive evaluation of functions.
* Functional programming languages discourage side effects.  Pure functional languages don't allow them.
* Pure functional programming languages like Haskell can be difficult to use.  F# is an impure functional or multi-paradigm language and has flexibility when you need it.
* By encouraging functional programming principles, F# makes writing concurrent, scalable, asynchronous applications simpler than writing these same applications using imperative and/or OO languages.

<ul style="list-style:none">
<li class="right">
<a href="\fsurvival\next">next</a>
</li>
<li style="float: right">
 | 
</li>
    <li class="right">
<a href="\fsurvival\introduction">previous</a>
    </li>
    <li style="float:right">
    |
    </li>
    <li class="right">
    <a href="\fsurvival\toc">Main</a>    
    </li>
</ul>
