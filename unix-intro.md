# Unix - An Introduction

## Important notes!!! 

1. Instructions, file names, arguments, options, etc. are all case sensitive
2. Press {{Key press|Enter}} at the end of an instruction
3. TAB-completion will save time, use it!
4. Copy-paste from/to terminal is {{Key press|Ctrl|Shift|c}} and {{Key press|Ctrl|Shift|v}}

## Concepts
### Command-line and shell
__prompt:__ a symbol indicating that you can type input to the computer. Yours probably says something like:
``` bash
thomas@vm:~$
```
__In the exercises, anything that is after a prompt (`~$`) is something you can try on the terminal yourself.__

__command line:__ the prompt is the actual text that appears on your screen at the beginning of a command line, which is a place where you can type commands to the computer. What you type is "interpreted" by the computer (by a program called a "shell", actually) which tries to do what you asked it to do.

__shell:__ any time you log in to a Linux system, you will start a piece of software called a "shell". This is a simple interpreter (a piece of software that turns human readable commands into computer operations) which allows you to access the computer, read and move files, run other programs, etc. The more familiar Windows and Mac operating systems are somewhat like graphical shells in this regard. The one you are running is called "bash", and is one of the more modern and popular shells (Mac users generally also have bash as their default shell for the MacOS terminal).

### Options, arguments and flags 
Anything that comes after the name of a command are arguments.
``` bash
      /---------/ -> arguments
~$ ls -l -a data
   |   |  |   #-> target
   |   |  |
   |   #--#--> flags
   |
   #--> command
```
This is a very simplified overview and if you want to learn more, there is much more information on [Wikipedia](http://en.wikipedia.org/wiki/Command-line_interface)

## Commands 
### Who am I? Where am I? What's here?
``` bash
~$ who
```
Tells you who is logged in to your computer
``` bash
~$ whoami
```
Tells you your login name
``` bash
~$ pwd
```
Tells you what your __current working directory__ is
``` bash
~$ echo Hello World!
```
display a line of text on screen
``` bash
~$ echo Hello World! > welcome.txt
```
Writes the text 'Hello World! to a file 'welcome.txt'
``` bash
~$ ls
```
Tells you which files are in the current working directory
``` bash
~$ cat <filename>
```
Prints the content of a file to the screen, for example
``` bash
~$ cat welcome.txt
```
### Damage control
``` bash
~$ clear
```
Clears the window and the line buffer
``` bash
~$ reset 
```
Reset the terminal <br>
press `Ctrl + c` to terminate the currently running program
## Getting help
If you are at any point uncertain how to use a certain command or what the arguments are, there are several ways to find that out.
Using the build in *man*ual pages.
``` bash
 ~$ man <name of the command>
```
Using the command *whatis* command
``` bash
 ~$ whatis <name of the command>
```
Often the program has a build in help function that you can use with the argument '--help'. For example to know what _man_ does:
``` bash
~$ man --help
```
 General syntax:
``` bash
 ~$ <name of command> --help
```
## Exercises
1. Who are you? Or maybe more accurate, what is your login name? 

2. What does the command `date` do? 

3. What does the command `echo` do? 

4. Use `echo` to write "Hello World" to the screen. 

5. What is your current working directory? 

6. Which files are available in your current working directory? 

7. What does the welcome.txt file say? 

8. Run the following command

``` bash
sleep 3600
```

It appears your terminal is asleep, get your terminal back alive.

Everything in unix is a file, the goal of these exercises is to learn how to navigate the file system and how to manipulate files.

## Special files
Directories are special files that form the hierarchical structure of the file system.

Programs are files that can be executed by the shell and perform a particular task.

There are three special symbolic directories that always have the same meaning.
```
.   -> current directory
..  -> parent directory, i.e. one level higher in the hierarchy
~   -> your home directory, e.g. /home/thomas/
```

## Recap
``` bash
~$ pwd
```
Tells you what your current working directory is, i.e. where you are in the file system.
``` bash
~$ ls
```
Tells you which files are in your current working directory.
``` bash
~$ ls <pathname>
```
Tells you which files are in a particular path.
For example, do a regular
``` bash
~$ ls
```
to see which directories are available, then do
``` bash
~$ ls <directory name>
```
to see which files are in that directory.
## Navigating around
``` bash
 ~$ cd <directory name>
```
Go to the specified directory
``` bash
Tab-completion!
Relative vs. absolute paths!
```
For example:
``` bash
~$ cd ~
```
bring you to you home directory. Once you are in your home directory 
``` bash
~$ cd Documents
```
will get you in the Documents directory.

## Creating and editing files
``` bash
~$ nano <filename>
```
Edits the specified file, if they file does not exist, it will be created when saved.
``` bash
 ~$ nano small_file.txt
 ```
This will open the nano text-editor, type some text, press {{key press|Ctrl|x}} to quit, reply {{key press|y}} when asked to save changes.
``` bash
~$ mkdir <directory name>
```
Makes a new directory with the specified name, for example
``` bash
~$ mkdir test_directory
```

## Copying files 
``` bash
~$ cp <original file(s)> <target file/directory>
```

for example:
``` bash
 ~$ cp cp small_file.txt test_directory/
```

You can copy complete directories recursively using the '-r' option, for example:
``` bash
~$ cp -r test_directory/ test_directory2
```

## Moving and renaming files 
Moving and renaming files are identical operations in Linux.
``` bash
~$ mv <original file> <target file>
```

Renames/moves the original file to the target file name, for example:
``` bash
~$ mv small_file.txt test_file.txt
```
## Removing files and directories
``` bash
~$ rm <filename>
```

Removes the target file, for example:
``` bash
~$ rm test_file.txt
```

To remove empty directories, you can use 'rmdir', for example
``` bash
~$ rmdir test_directory2
```

This will not work because the test_directory2 is not empty. Either delete the file, or you could use the 'rm' command recursively.
``` bash
~$ rm -r test_directory2
 ```
This will delete test_directory2 and anything contained therein. __Be very careful when using `rm -r` because it has the potential to ruin your day__

## File permissions
Move to the directory 'test_directory' and do a detailed directory listing:
``` bash
~$ cd test_directory
~$ ls -l
```

You should get an output that looks similar to this one, probably a bit more extensive.	
``` bash
-rw-rw-r--. 1 genomics genomics 10 Oct 30 09:24 small_file.txt
```

The first column of this listing shows what the file permissions are for the file.
You can change file permissions with the command ''chmod'', for example:
``` bash
~$ chmod 000 small_file.txt
```

This make the file completely inaccessible to anybody and trying to view the file will result in an error. You can test this with for example:
``` bash
~$ cat small_file.txt
```

To turn the file back to the default permissions execute this instruction:
``` bash
~$ chmod 755 small_file.txt
```

## Exercises
1. Make sure you're in your home directory

2. Make a directory ''unix'' and check what's there.

3. Copy the file welcome.txt in the home folder to directory unix

4. Go into the ''Unix'' folder.

5. Copy the file welcome.txt to the Documents folder.

6. Move to the ''Documents'' folder and check what's there.

7. Delete the directory and files in the folder.

6. Go back to your home directory.
