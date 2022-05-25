# commandLine 


![screenshots for some command](./sqlscreenshots/Screenshot(24).png)
![..](sqlscreenshots/Screenshot(26).png)
![..](sqlscreenshots/Screenshot(27).png)

### ls
##### this make you see what is inside this path  

Perform a listing of the given path or your current directory.
Common options: -l, -h, -a
 

## cd
##### this command to make you enter "go inside or outside" a path 

Change into the given path or into your home directory.
 

 ## here is some description for cd path :
### Path

it is A description of where a file or directory is on the filesystem.

### Absolute Path

One beginning from the root of the file system (eg. /etc/sysconfig ).

### Relative Path

One relative to where you currently are in the system (eg. Documents/music ).

### ~ (tilde)

Used in paths as a reference to your home directory (eg. ~/Documents ).

### . (dot)

Used in paths as a reference to your current directory (eg. ./bin ).

### .. (dot dot)

Used in paths as a reference to your current directories parent directory (eg. ../bin ).


## TAB completion
Start typing and press TAB. The system will auto complete the path. Press TAB twice and it will show you your alternatives.


## file followed with path 

Find out what type of item a file or directory is.

## Spaces in names

Put whole path in quotes ( " ) or a backslash ( \ ) in front of spaces.

## Hidden files and directories

A name beginning with a . (dot) is considered hidden.


## Manual Pages
#### man <command>

View the man page for a command.

#### man -k <search term>

Search for man pages containing the search term.
#### n
After performing a search within a manual page, select the next found item.
#### Press q to exit man pages

## File Manipulation
### mkdir <directory name>

this will Create a directory

### rmdir <directory name>

this will Remove a directory (only if empty).

### touch <file name>

Create a blank file.

### cp <source> <destination>

Copy the source file to the destination.

### mv <source> <destination>

Move the source file to the destination.
May also be used to rename files or directories.

### rm <path>

Remove a file or directory.

#### Common options: -r -f


## Filters
.head
Show the first n lines.
.tail
Show the last n lines.
.sort
Sort lines in a given way.
.wc
How many words, characters and lines.
.grep
Search for a given pattern.

#### also
>
Redirect STDOUT to a file.
>>
Append STDOUT to the end of a file.
2>
Redirect the STDERR to a file.
<
Pass the contents of a file to a program as STDIN.
|
Feed the STDOUT of the program on the left as STDIN to the program on the right.
Process Management 

### CTRL + C
Cancel the currently running process.

#### kill <process id>
Cancel the given process.
Include the option -9 to kill a stubborn process.
#### ps
Obtain a listing of processes and their id's.
Including the option aux will show all processes.
### CTRL + Z
Pause the currently running process and put it in the background.
jobs
See a list of current processes in the background.
#### fg <job number>
Move the given process from the background to the foreground.

##### du -sh ./*
Find the size of every directory in your current directory.
##### df -h
Display how much disk space is used and also free.
#### basename -s .jpg -a *.jpg | xargs -n1 -i cp {}.jpg {}_original.jpg
Make a copy of every jpg image file in the current directory and rename adding _original.
#### find /home -mtime -1
Find all files in the given directory (and subdirectories) which have been modified in the last 24 hours.
##### shutdown -h now

### cat
View a file.

 ### less <file>

less allows you to move up and down within a file using the arrow keys

### vi 
edit file 
![vi command](sqlscreenshots/Screenshot(25).png)


#### Wildcards may be used at any part of a path.
Wherever a path is used
Because wildcard substitution is done by the system, not the command, they may be used wherever a path is used.
##### ex: * ? [] 

### chmod
Change permissions on a file or directory.
 
 #### nl 
 ![]()
. nl - s ` . ` -w num 
-s specifies what should be printed after the number while the second one -w specifies how much padding to put before the number.
 #### word count wc 
  By default it will give a count of all 
  option : -l / -lw

  #### Stream Editor sed

 #### uniq
Remove duplicate lines.
#### tac
Print the data in reverse order.
#### top 
a program make snapshot of what is currently happening on the system


### egrep

egrep is a program which will search a given set of data and print every line which contains a given pattern
options : 
 . (dot) - a single character.
   ? - the preceding character matches 0 or 1 times only.
#####   * - the preceding character matches 0 or more times.
 #####  + - the preceding character matches 1 or more times.
   {n} - the preceding character matches exactly n times.
   {n,m} - the preceding character matches at least n times and not more than m times.
   [agd] - the character is one of those included within the square brackets.
   [^agd] - the character is not one of those included within the square brackets.
   [c-f] - the dash within the square brackets operates as a range. In this case it means either the letters c, d, e or f.
   () - allows us to group several characters to behave as one.
   | (pipe symbol) - the logical OR operation.
   ^ - matches the beginning of the line.
   $ - matches the end of the line.
 
  ### ps 
  which stands for processes. In it's normal usage it will show you just the processes running in your current terminal (which is usually not very much). If we add the argument aux then it will show a complete system view which is a bit more helpful.
  ##### option :
  ###### aux hen it will show a complete system view which is a bit more helpful.

#### jobs
Display a list of current jobs running in the background.

#### fg

Move a background process into the foreground

#!
Shebang. Indicates which interpreter a script should be run with.

##### echo
Print a message to the screen.

#### which
Tells you the path to a particular program.

##### $
Placed before a variable name when we are referring to it's value.
` `
Backticks. Used to save the output of a program into a variable.

##### date
Prints the date.

##### if [ ] then else fi
Perform basic conditional logic.