---
title: Solve "ValueError invalid literal for int() with base 10" - Python
layout: post
tags:
  - Python
---

Normally "ValueError: invalid literal for `int()` with base 10" error occurs when we try to convert an invalid object into an integer.

The cases are,

1. Passing a string containing anything that is not a number, like letters and special characters.
2. Passing a string-type object that looks like a float type.

Example

    int_var = int("...")

The solution is to ensure that we do not pass any letters or special characters to `int()` function.

### Solution 1

    import re
    myInput= "123a"
    matched=re.search("[^\d]",myInput)
    if matched==None:
        myInt=int(myInput)
        print("Output Integer is:")
        print(myInt)
    else:
        print("Input Cannot be converted into Integer.")


### Solution 2

    myInput= "123a"
    if myInput.isdigit():
        print("Output Integer is:")
        myInt=int(myInput)
        print(myInt)
    else:
        print("Input cannot be converted into integer.")
