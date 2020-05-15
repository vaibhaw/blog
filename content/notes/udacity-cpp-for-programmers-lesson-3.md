---
title: "Udacity: C++ for Programmers Lesson 3"
date: 2018-08-28T04:22:10-04:00
draft: true
---

## Lesson 3: Arithmetic Operators

### 3.3 Arithmetic Operations

```cpp
#include <cmath>
// + - * / %
// % is called modulo
// std::pow(5, 4) // = 625
// value of PI // M_PI
```

### 3.6 Implicit Assignment
```cpp
// integer can be assigned to a float
// integer can be treated as a char
// float can be assigned to int (with truncation)
// float can be assigned to char but it prints wierd on terminal  - TODO read more about it

int a = 4;
int b = 8;

int c = a/b; // == 0
float d = a/b; // == 0
float d = a*1.0/b; // == 0.5
```

### 3.11 Prefix and Postfix

Prefix operators:

- increment the value of the variable, then 
- return the reference to the variable.

Postfix operators:

- create a copy of the variable
- increments the value of the variable, then
- returns a copy from BEFORE the increment.

### 3.13 Assignment Operators
+= -= \*= /= %=


## Lesson 4: Control Flow

### Relational Operators
== != > < >= <=

### Logic Operators
and && 
or ||
not !

