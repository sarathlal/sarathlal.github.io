---
title: Find largest number in a list of numbers - Python
layout: post
tags:
  - Python
---

There are multiple ways to find the largest number in a list using Python. Here are 2 basic methods I have used regularly.

### Using max() function

    # list
    my_list = [10, 20, 4, 45, 99]
      
    # printing the last element
    print("Largest element is:", max(my_list))


### Sort the list in ascending order & print last element

    # list
    my_list = [10, 20, 4, 45, 99]
      
    # sorting the list
    my_list.sort()
      
    # printing the last element
    print("Largest element is:", my_list[-1])
