# Spring 2020 Project 00 - Checking the Project Workflow 

This project should take you through the workflow for 3353 for Spring 2020.  

## What you need to do

1. Accept the assignment invitation from Github Classroom.  Since you're reading this, you've probably alredy done this. 
2. Clone the repo to your local dev machine and load the project in your chosen dev environment/IDE. 
3. Open the main driver and modify it to achieve the following:
    - Scenario: Create a histogram for a dataset of normalized performance scores for a scientific instrument on the range of [0,99].
    - argv[1] is the name of the input data file. 
    - argv[2] is the name of the output file containing the histogram. 
    - Histogram Characterisitics:
        - See the example below... 
        - Height of y axis should be 10 units.  If frequency of one range exceeds 10, scale all frequency values to be within the range of [0,9]. 
        - Below the histogram, output the number of data items in the dataset. 

**Important:** Make sure to read the section below on Input and Output file.  You'll need to modify the `CMakeLists.txt` file and the `build.yaml` file for Github actions. 


### Sample Histogram

```txt
 |
 |
 |
 |
 |                             *
 |                             *      *
 |                      *      *      *
 |        *             *      *      *             *
 |        *             *      *      *             *
 |        *      *      *      *      *      *      *             *
 |  *     *      *      *      *      *      *      *      *      *
 |--------------------------------------------------------------------
   0-9  10-19  20-29  30-39  40-49  50-59  60-69  70-79  80-89  90-99
 
   n = 99
```


## Input and Output Files

As you begin using input files and output files with this project, 
you'll need to modify the `CMakeLists.txt` file and the `.github/workflows/build.yaml`
files.  

Place any input files in the folder that contains your source code.  When your project is built, it will be copied into
the build directory by CMake. 

- `CMakeLists.txt`
    - Open it and look for the commented section (with `#` signs).  Edit the `set(input01 "")` etc.
    based upon how many files you need.
    - there should be one `set(...)` statement per input file
    - you DO NOT need to list output files in `CmakeLists.txt`.
    
- `.github/workflows/build.yaml`
    - Open this file and look for the `INPUT_FILES:` command near the top.
    - List the input file names in the order they should be sent to argv of main. 
    - OUTPUT file need to be listed here as well in the `OUTPUT_FILES:` section. 
    - For example:
        ```yaml
        INPUT_FILES: train.csv train_target.csv
        OUTPUT_FILES: output01.txt
        ```
      would be equivalent to the following execution command:
      ```yaml
      ./executableName train.csv train_target.csv output01.txt
      ```      
