---
title: Write our first Selenium program with Python 3 & Firefox
layout: post
tags:
  - Python
  - Selenium
  - Test Automation
  - Firefox
---

*Prerequisite*

1. Linux Machine
2. Firefox Browser
3. Gecko driver

Create a directory for our projet.

    mkdir selenium-test
    cd selenium-test

Normally I use a virtual environment for python projects. So my first step is creating a virtual environment.

    python3 -m venv env

Then install selenium inside new virtual environment.

    pip install selenium

Lets create our program file.
    
    touch first_program.py

Open the new file in editor or command line. Add the below content in the file & save it.

    from selenium import webdriver
    from selenium.webdriver.common.by import By
    from selenium.webdriver.common.keys import Keys
     
    driver = webdriver.Firefox()

    #launch URL
    driver.get("https://www.google.com/")

    #identify search box
    m = driver.find_element(by=By.NAME, value="q")

    #enter search text
    m.send_keys("Open Source")

    #perform Google search with Keys.ENTER
    m.send_keys(Keys.ENTER)

Run the program.

    python first_program.py
