---
title: "Udacity: C++ for Programmers - Lesson 1"
description: ""
author: "Vaibhaw Singh Chandel"
date: 2018-08-13T07:28:12-04:00
tags: ["C++", "Udacity", "MOOC"]
draft: true
---

## Lesson 1: Basics

### 1.4 What makes C++ different?

- works directly on hardware
- really strong abstraction mechanisms

### 1.6 Textbook

- `The C++ Programming Language - 4th Edition` - good for professionals or people who already know how to code
- `Programming: Principles and Practice Using C++ - 2nd Edition` - good for people who don't know how to code
- `A Tour of C++` - quick overview of C++ for people who already know C++

### 1.7 Program Structure

```
#include <iostream>
// <> tells the compiler to look in the directory where standard libraries are kept

#include "iostream"
// "" tells the compiler to look in current directory,
// then where standard libraries are kept
```
include is preprocessor directive. there can be many/other pre-processor directives too

### 1.8 Comments

```
// single line comment
```

```cpp
// comment block
/*
...
...
*/
```


```cpp
// not necessary but better to use
/*
** ...
** ...
*/

```

### 1.15 Using namespace
Use namespace to avoid writing std:: each and every time you use cout etc. but this may result into namespace collision.
```
#include <iostream>

using namespace std;

cout << "meh" << endl;
```
TODO: write what's the best practice

### 1.16 Writing to console
#### Writing string, number and variable together
```cpp
using namespace std;

int x1 = 2;
int x2 = 3;
cout << "roots of x2 - 5x + 6 = 0 are " << x1 << " and " << x2;
```

#### Newline (\n) vs Endline (std::endl)
```cpp
cout << "what's going on?" << "\n";
// OR
cout << "what's going on?" << endl;
```
TODO: give source to stackoverflow discussion

### 1.20 sizeof
```
cout << sizeof(int) << endl;
```
int - 4, short - 2, long - 8, float - 4, double - 8, char - 1, bool - 1 (on my machine)
TODO: figure out whether this depends on architecture

### 1.22 constants
constant variables can't be changed later in the program
```
const int age = 23;
```

### 1.23 enumerated constants
```cpp
// define
enum MONTH {Jan, Feb, Mar, .... , Dec}
// define
MONTH first;
// assign
first = Jan;

cout << first;  // 0
cout << Jan;  // 0
cout << Feb;  // 1
```
Microsoft recommends singular for naming enums; hence MONTH not MONTHS

### 1.24 Format Output
"\n" for newline, "\t" for tab
```cpp
#include <iostream>
#include <iomanip>

std::cout << "a" << std::setw(15) << "b" << std::setw(15) << "c" << std::endl;
// setw = set width
```

### 1.25 File IO

>- Include the <fstream> library 
>- Create a stream (input, output, both)
>     - ofstream myfile; (for writing to a file)
>     - ifstream myfile; (for reading a file)
>     - fstream myfile; (for reading and writing a file)
>- Open the file  myfile.open(“filename”);
>- Write or read the file
>- Close the file myfile.close();

```cpp
    string line;
    //create an output stream to write to the file
    //append the new lines to the end of the file
    ofstream myfileI ("input.txt", ios::app);
    if (myfileI.is_open())
    {
        myfileI << "\nI am adding a line.\n";
        myfileI << "I am adding another line.\n";
        myfileI.close();
    }
    else cout << "Unable to open file for writing";

    //create an input stream to read the file
    ifstream myfileO ("input.txt");
    //During the creation of ifstream, the file is opened. 
    //So we do not have explicitly open the file. 
    if (myfileO.is_open())
    {
        while ( getline (myfileO,line) )
        {
            cout << line << '\n';
        }
        myfileO.close();
    }

    else cout << "Unable to open file for reading";
```

```cpp
    // write at the beginning of file - overwrite
    fstream myfileI ("input.txt", fstream::out);
    // write at the end of file - append
    fstream myfileI ("input.txt", fstream::app);
    // read file
    fstream myfileO ("input.txt", fstream::out);
    // read or write (append)
    fstream myfileIO ("input.txt", fstream::in | fstream::out | fstream::app);
```
[source](https://stackoverflow.com/a/30388637/925216)
The first case helps with the semantics: a std::fstream could be opened in input, output or both. Because of this you need to check the declaration to be sure while using std::ifstream and std::ofstream will make it clear what you're doing. The second case has more room for human error which is why it should be avoided.

My own rule of thumb is to use a std::fstream when you need both read and write access to the file and only in this case.

### 1.32 User Input
```cpp
// for writing to the console
cout << "meh" << endl;
// for reading from the console
cin >> x;
// write to console, whatever we read
cout << x << endl;
```
`cin` assigns value in buffer to variables. This is called extraction.
It doesn't validate the input with variable type and also treats whitespace as end of input. Because of this behaviour it breaks sentences to words and assigns incorrectly.

### 1.35 String Input
`getline` reads characters from `std::cin` until newline or "\n" is detected and assigns to input
```cpp
std::getline(std::cin, variableName)
```

### 1.38 StringStream
Convert string variable to other variable types such as int, float etc.
```cpp
#include <sstream>
std::getline(std::cin, stringVariable);
std::stringstream(stringVariable) >> numericVariable;
```