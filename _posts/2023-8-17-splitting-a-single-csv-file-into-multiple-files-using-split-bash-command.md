---
title: Split a Single CSV File into Multiple Files Using the Split Command - Bash
layout: post
tags:
  - bash
--- 

Working with huge CSV files? Need to split them for easier management and analysis? Look no further - I will show you how to split large CSV files using the `split` command in Bash. This quick guide will help you split your data like a pro!

### Step 1: Open Your Terminal

To begin splitting your CSV files, open your terminal. You can use `split` in Bash on Linux, macOS, or Windows with WSL (Windows Subsystem for Linux).

### Step 2: Navigate to the File's Directory

Navigate to the directory where your CSV file is located using the `cd` command:

```bash
cd /path/to/your/csv/directory
```

### Step 3: Splitting the CSV File

Use the `split` command to divide your CSV file by specifying the number of lines in each new file:

```bash
split -l 1000 large_data.csv smaller_data_
```

This command will split `large_data.csv` into smaller files, each containing 1000 lines. The new files will be named `smaller_data_aa`, `smaller_data_ab`, `smaller_data_ac`, and so on.

### Step 4: Verify the Split

To confirm that the split was successful, list the files in your directory:

```bash
ls
```
