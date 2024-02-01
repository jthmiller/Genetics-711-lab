---
output: pdf_document
---


1. Open vscode
2. Go to 'File --> Open workspace from file'
3. Go into your gen711 folder on the desktop
4. Select the workspace you saved last week.
5. Open terminal (menu bar --> terminal --> new terminal )
6. Determine if the terminal is in 'gen711_lab' folder

## Today:
- Navigating Files and Directories (review and new)
- Practice practical question


### Having touble changing directories in terminal to your lab folder? Try:
cd ~
cd gen711


# Navigating Files and Directories
- How can I perform operations on files outside of my working directory?
- What are some navigational shortcuts I can use to make my work more efficient?

## Objectives:
- Use a single command to navigate multiple steps in your directory structure, including moving backwards (one level up).
- Perform operations on files in directories outside your working directory.
- Work with hidden directories and hidden files.
- Interconvert between absolute and relative paths.
- Employ navigational shortcuts to move around your file system.

## More navigation
- We got an idea for moving around using cd and the name of the folder to move into. 
- But how to we go back out? We dont see the folder we are in.
- We have a special command to tell the computer to move us back or up one directory level.

### We have a special command to tell the computer to move us back or up one directory level. 
- we use 'cd ..'
```  
cd untrimmed_fastq
ls
```
- then, lets do the exact opposite to go back to where we were
```
cd ../
ls
>sra_metadata    untrimmed_fastq
```  

- Navigation seems pretty slow, if you have to type cd every time if your data is like ten folders deep.
- Or the opposite is equally slow; navigating out one directory at a time with '../'
- lets go back into 'untrimmed_fastq' 
```  
cd untrimmed_fastq
```  
- To navigate out two folders from here, we can double it up with 
```  
cd ../../
ls
shell_data
```  

## Hidden files
- Sometimes, its better to hide files from the command line. Like system files that shouldn't be messed with by the command line user.
- Somewhere in 'shell_data' is a hidden file. 
- Mention ls -aF and ls -Fa are the same, but case matters alot

### Navigate by multiple directories
- if you are in gen711_lab, navigate one folder out. 'cd ../'
```  
pwd 
>/Users/jeffreymiller/Desktop/gen711_lab
```  
- if you are in 'shell_data', navigate one folder out. 'cd ../../'
- if you are in 'untrimmed_fastq' or '.hidden', navigate two out with 'cd ../../'

### The tilda shortcut takes you home
- green yellow esc (~)
```  
cd ~
cd gen711/shell_data
```  
- The /, ~, and .. characters represent important navigational shortcuts.
- Hidden files and directories start with . and can be viewed using ls -a.
- Relative paths specify a location starting from the current location, while absolute paths specify a location from the root of the file system.

### The / by itself, takes you all the way back to root. 

- This is an absolute path:
```  
cd /Users/jeffreymiller/Desktop/gen711_lab/shell_data
```  

- We have been navigating using relative paths
- You can use absolute paths anywhere, and they will get you there
- relative paths only work if you can see the folder that you want to be in

## Relative path
```  
cd untrimmed_fastq
```  
## Absolute
```  
cd /Users/jeffreymiller/Desktop/gen711_lab/shell_data/untrimmed_fastq
```  


# Working with Files and Directories

### We are interested in looking at the FASTQ files in this directory. We can list all files with the .fastq extension using the command:
Questions
    How can I view and search file contents?
    How can I create, copy and delete files and directories?
    How can I control who has permission to modify a file?
    How can I repeat recently used commands?

Objectives
    View, search within, copy, move, and rename files. Create new directories.
    Use wildcards (*) to perform operations on multiple files.
    Make a file read only.
    Use the history command to view and repeat recently used commands.


Now that we know how to navigate around our directory structure, let’s start working with our sequencing files. We did a sequencing experiment and have two results files, which are stored in our untrimmed_fastq directory.

``` 
cd ~/shell_data/untrimmed_fastq
``` 

- We are interested in looking at the FASTQ files in this directory. 
- We can list all files with the .fastq extension using the command:

``` 
 ls *.fastq
 > SRR097977.fastq  SRR098026.fastq
``` 

The wildcard works with more than just the file extension name. Similar to the way the tab works by filling in as much as it can without making decisions for you. 

``` 
 ls *977.fastq
 > SRR097977.fastq
``` 

You can use this to see files that match in far directories too. Lets ls on an absolut 

ls /Users/jeffreymiller/Desktop/gen711_lab/shell_data/untrimmed_fastq/*fastq


## EXERCISE 
1. Do each of the following tasks from your current directory using a single ls command for each:
    - List all of the files in /Applications that start with the letter ‘c’.
    - List all of the files in /Applications that contain the letter ‘a’.
    - List all of the files in /Applications that end with the letter ‘o’.
    - Bonus: List all of the files in /Applications that contain the letter ‘a’ or the letter ‘c’.

2. 'echo' is a built-in shell command that writes its arguments, like a line of text to standard output. The 'echo' command can also be used with pattern matching characters, such as wildcard characters. Here we will use the echo command to see how the wildcard character is interpreted by the shell.  What does echo say when you try to match something that is not there? What about ls?

Don't Scroll To Bottom! ANSWERS ARE BELOW

# COMMAND HISTORY

- If you want to repeat a command that you’ve run recently, you can access previous commands using the up arrow on your keyboard to go back to the most recent command. 

- Likewise, the down arrow takes you forward in the command history.

### To cancel something that wont run:
- ctrl + c (cancel command when stuck)
- ctrl + r (find in your command history)
- ctrl + L (clear)

## Exercise:
- Find the line number in your history for the command that listed all the .fastq files using the absolute path . Rerun that command.













## ANSWERS 
1. 
ls /usr/bin/c*
ls /usr/bin/*a*
ls /usr/bin/*o
Bonus: ls /usr/bin/*[ac]*

2. 
echo *.fastq
> SRR097977.fastq SRR098026.fastq
echo *.missing
ls *.missing