---
title: Manage package dependencies in Python project
layout: post
tags:
  - Python
---

If we share a python project with others, use a build system or restore an environment, we need to specify the external packages that the project requires.

The recommended approach is to use a `requirements.txt` file that contains a list of commands for `pip` that installs the required versions of dependent packages.

Note: My assumption is that you are using a virtual environment to set up your project. Developing python projects in a virtual environment is the recommended method.

There are multiple methods to generate `requirements.txt`.

## 1) pip freeze command

    pip freeze > requirements.txt

This command records an environment's current package list into `requirements.txt`. We can ship this file with our project & later every one can easily install dependent packages.

The drawback of this method is `freeze` command records all packages in the current environment to `requirements.txt`. There is a chance for unused packages.

## 2) Using pipreqs package

	pip install pipreqs

If we are in the same path with our file, we can just write `./`. Otherwise we need to give path of our file.

	pipreqs ./
	
or

	pipreqs /home/project/location

That will create a `requirements.txt` file for our project. The important advantage is `pipreqs` package only records packages that are imported in project files.
