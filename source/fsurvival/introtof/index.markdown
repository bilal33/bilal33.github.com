---
layout: page
title: "Introduction to F# & Essential tools"
comments: true
footer: true
sidebar: false
---

##Introduction
In this chapter, we introduce the F# language and learn how to get our first program up and running. 
In doing so, we will discuss the basic rules around F# program structure and the essential tools you will need to develop rudimentary applications. 
As we progress through the book, and our experience grows, we will delve more deeply into code examples, tool examples, etc.

##Overview of F#
F# is a strongly typed, first-class .NET programming language designed by Don Syme and others at Microsoft Research.
It has its origins in the [ML approach to language design](http://en.wikipedia.org/wiki/ML_programming_language) and is a close relative of [OCaml](http://en.wikipedia.org/wiki/OCaml).

While billed primarily as a functional language, F# is in actuality a multi-paradigm language. 
This means that it supports imperative, OO, and functional styles of programming. 
A fully supported .NET language in its own right, F# interoperates naturally with code written in other .NET languages such as C# and VB.NET.

F# is available as part of Microsoft Visual Studio 2010. 
You can find the most recent F# Language Reference [here](http://msdn.microsoft.com/en-us/library/dd233181). 
For this book, all the code was tested with build 4.0.40219.1 in Visual Studio 2010.

Please consult the language reference for the basic rules and regulations of F#, e.g. the rules around defining a valid symbolic name, etc.

## F# Program Structure
You create F# programs using a standard text editor or IDE. With an IDE such as Visual Studio 2010, you get the benefit of syntax highlighting, IntelliSense, etc. 
As with other programming languages, F# adheres to a specific set of syntax and structural rules, uses a well-defined set of keywords, etc. 
We will cover the core keywords, syntax, and structure of F# programs starting in this chapter, and will continue to build on this knowledge throughout the rest of the text.

### #light
Due to its heritage, F# is compatible with OCaml. This means that you can write F# programs that are fully compliant with OCaml's syntax and semantic rules. 
Many developers, however, find OCaml's syntax to be quite *chatty* or *heavy*; 
therefore, F# supports a more streamlined programming syntax and semantic, known as **light** mode. 
You instruct F# to adhere to this light mode by placing the #light directive at the top of each of your F# program files.

For all intents and purposes, all of the F# programs that you encounter and write will use the #light directive. 
If you fail to use place the #light directive at the top of each of your F# program files, you will default to OCaml-compatible *verbose mode.* 
This will require the use of particular keywords and symbols to terminate expressions, etc.  
In the spirit of keeping things streamlined and to the point, we will not cover the verbose mode syntax in this book, nor will we cover structures and/or symbols that are in F# solely 
to support OCaml compatibility.

### Whitespace Matters
When you write F# programs and use the #light[1] directive, whitespace becomes significant to the structure and execution of the program. 
Whereas other languages, e.g. C#, use braces or other symbols to group compound statements, F# uses whitespace indentation for the same purpose.[2]

Code that is vertically aligned by whitespace indentation is considered to be semantically related. 
Python programmers will feel right at home with this concept. 
Note that F# does not recognize TAB as a valid whitespace character when used for aligning code blocks in #light mode. 
This means that you need to use spaces to align your code. Before you groan too loudly, read the next two points:

1. The number of spaces doesn't seem to matter. You can use 1 or more. I typically use 4, which matches the equivalent TAB.
2. When working in a Visual Studio F# Project (more on this shortly), the IDE converts TAB to spaces automatically. 
So, you can use the TAB key to align your code, and Visual Studio does the right thing in terms of ensuring your F# files have the right kind of whitespace.  
I assume you can set up your editor of choice to replace TABs with spaces as well.

### Comments
F# provides several different types of comment structures: single line comments, multiline comments and document (doc) comments. 
Let's take a look at each type below.

#### Single Line Comments
Single line comments begin with a //. Everything following the // is considered to be a comment. The comment extends to the end of the source code line.

``` 
// This is a single-comment. Everything from the start is treated as a comment.
```

#### Multiline Comments
Multiline comments begin with (* and end with *).

```
(* This is a multiline comment with only one line *)
(* This is another
multiline comment *)
```

#### Document (Doc) Comments
Doc comments start with '///' and are used to embed comments in the code from which XML or HTML documentation can be produced automatically. 
These comments are normally placed before the definitions of functions, data types, classes, discriminated unions, etc. 
We will discuss each of these structures in depth in future chapters.

```
/// This is a doc comment that can be converted to useful documentation.
```

### Keywords
F# has a small set of reserved keywords. 
These keywords cannot be used as value or identifier names, as they have special meaning to the compiler: