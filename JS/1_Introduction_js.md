# JavaScript

>JavaScript, is a [high-level](#difference-between), [just-in-time compiled](#just-in-time-compiled), [object-oriented programming language](#object-oriented-programming) that conforms to the ECMAScript specification JavaScript has curly-bracket syntax, dynamic typing, prototype-based object-orientation, and first-class functions.



# History Of JavaScript
>`Brendan Eich`, a Netscape Communications Corporation programmer, created JavaScript in September 1995. It took Eich only 10 days to develop the scripting language, then known as `Mocha`.


## JavaScript History Turns to ECMA

>By 1996, JavaScript’s importance grew so much that it was handed over to an international standards scripting language body called `ECMA` (`European Computer Manufacturers Association`), which is responsible for the development and upkeep of this language to this day. As a result, the scripting language was officially given the name ‘ECMAScript’ (or ‘`ECMA-262`’), however people still call it `JavaScript`.

>ECMA standards process runs in cycles – ECMAScript 2 was released in 1998,and ECMAScript 3 was released in 1999, which evolved into today’s modern JavaScript. Even though Microsoft proceeded to implement some of the proposals in their JScript language, it became clear that Microsoft would not implement JavaScript in Internet Explorer.

# Difference Between
S.NO | HIGH LEVEL LANGUAGE | LOW LEVEL LANGUAGE
---------|----------|---------
 1 | It is programmer friendly language.	 | It is a machine friendly language.
 2  |   High level language is less memory efficient.| Low level language is high memory efficient.
 3  | It is easy to understand.	    |   It is tough to understand.
4   |   It can run on any platform.	    |   It is machine-dependent.
5   |   It needs compiler or interpreter for translation.	|   It needs assembler for translation.



# Just In Time Compiled
>just-in-time (JIT) compilation (also dynamic translation or run-time compilations) is a way of executing computer code that involves compilation during execution of a program – at run time – rather than prior to execution.

>Most often, this consists of source code or more commonly bytecode translation to machine code, which is then executed directly. 

>A system implementing a JIT compiler typically continuously analyses the code being executed and identifies parts of the code where the speedup gained from compilation or recompilation would outweigh the overhead of compiling that code.


# Object Oriented Programming
>Object-oriented programming – As the name suggests uses objects in programming. Object-oriented programming aims to implement real-world entities like inheritance, Encapsulation, polymorphism, etc in programming. The main aim of OOP is to bind together the data and the functions that operate on them so that no other part of the code can access this data except that function.






![Characteristice of Object Oriented Programming Lanaguage](https://media.geeksforgeeks.org/wp-content/uploads/OOPs-Concepts.jpg)

# ECMA Script Specification
>The ECMA-262 Specification defined a standard version of the core JavaScript language.

* JavaScript is a lightweight, interpreted programming language.
* Designed for creating network-centric applications.
* Complementary to and integrated with Java.
* Complementary to and integrated with HTML.
* Open and cross-platform




# Browser Components
![Browser Components](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/layers.png)

1. `The user interface`: this includes the address bar, back/forward button, bookmarking menu, etc. Every part of the browser display except the window where you see the requested page.

2. `The browser engine`: marshals actions between the UI and the rendering engine.

3. `The rendering engine` : responsible for displaying requested content. For example if the requested content is HTML, the rendering engine parses HTML and CSS, and displays the parsed content on the screen.
4.` Networking`: for network calls such as HTTP requests, using different implementations for different platform behind a platform-independent interface.

5. `UI backend`: used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. Underneath it uses operating system user interface methods.

6. `JavaScript interpreter`: Used to parse and execute JavaScript code.

7. `Data storage`: This is a persistence layer. The browser may need to save all sorts of data locally, such as cookies. Browsers also support storage mechanisms such as localStorage, IndexedDB, WebSQL and FileSystem.


# How The engine Works
![How the compiler and interpretor works](https://miro.medium.com/proxy/1*VqHSZhJ93Vhijkm_VCjHsw.gif)


# Current Major JavaScript Engines:

* `V8` — open source, developed by Google, written in C++

* `SpiderMonkey` — the first JavaScript engine, which back in the days powered Netscape Navigator, and today powers Firefox

* `JavaScriptCore` — open source, marketed as Nitro and developed by Apple for Safari



[Go To Top](#javascript) ->
