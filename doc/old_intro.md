## Introduction

The aim of this course is to teach some basic computer skills for
people working molecular data such as DNA sequences.

- Learn to automate some simple tasks
- Learn the basics of Unix commandline and Perl 

## Softwear overview
### Unix shell

Unix shell refers to the command-line interface of a Unix based
operating system. Unix based operating systems are Linux distributions
(Ubuntu, Fedora, Suse, Red Hat, etc.), Mac OS and BSD distributions.

#### Using a unix based operating system

If you are using an operating system that is unix based, then you only
need to open a terminal window to gain access to the shell.

#### Using Windows

If you are using Windows you first have to install softwear that
emulates a unix system. Here is two ways you can do it (there may be
more, but these are the ones I am familiar with).

#### Running a virtual machine with Linux

For this option you need to install a virtualisation program that
allows you to create and run virtual machines. I personally use
Oracle's VirtualBox, which you can download from
[here](http://www.virtualbox.org/wiki/Downloads) (x86 for a 32-bit
system and **amd64** for a 64-bit system).


After installing the program you can create new virtual machines or
load/import a virtual machine. You may create a new machine with a new
virtual disk and install a linux distribution on it (I recommend
Ubuntu, 32-bit version is enough). Or you can import the virtual
machine which I will make available for you.


#### Cygwin

You can download the installation file from
[here](http://cygwin.com/install.html). Make sure that you select Perl
for installation!


After installation there are two ways to use the unix tools:

1.    Running cygwin. This will open a terminal window where you can
      type the commands.
1.    Adding cygwin's **bin** folder to the _path_ of your system and
      than open a command-line window.
	  

##### Adding cygwin's bin to the path

Go to **System Properties** > **Advanced** tab > **Environment
Variables...** button > in the new dialog window add a new variable by
pressing the **New...** button for your user type **Path** as variable
name and **C:\cygwin\bin** as variable value (Watch out! C:\cygwin\bin
is the default folder for cygwin, but if you installed it somewhere
else you have to insert the location of your installation). Hit **OK**
on all windows that are open then if you start a command-line window
and type `ls` hit enter and it should list all the files and folders
in the current directory.


## Text editors

During this course you will be learning to write programs (or
scripts), which will allow you to automate processes. To write these
programs we will need to use text editors and I strongly recommend
that you use a text editor that has syntax highlighting, which will
make the writing process and the debugging easier.


There are tons of text editors with syntax highlighting. You may use
whichever text editor that you wish. Here I will recommend three
fairly simple to use text editors.

Here are the [learning curves](http://www.manuelmagic.me/resources/Geek/Text-editors/text_editors.pdf) for a set of popular editors



![Learning curves](http://www.manuelmagic.me/geek/texteditors/files/text_editors.jpg)

### Notepad++

This is a text editor for Windows users, although it can be installed
on linux using wine. You can download the intallation file from here.


This program displays line numbers by default, which will be valuable
when we need to debug a program. Also it matches brackets, parentheses
and curly brackets (braces). And it allows you collapse blocks, this
can make reading your code easier. Finally it can display line
endings. You will see during the course what kind of problems line
endings can cause.

### Gedit

Gedit is the official text editor of the GNOME environment (for
example in Ubuntu). You can set the preferances so that line numbers
will be displayed.

### Nano

Nano is an easy to use command-line text editor that is available on
most unix systems by default. Unlike the previous two editors this one
can be run in terminal, it doesn't have separate window.


##  Basics
### Commands for command-line

Here are a few very basic and very important commands. The options
mentioned in the option column are not always neccesary, they change
how the given command works.


**Basic Unix commands:**

| Command | option | description |
| ------- | ------ | ----------- |
|pwd | | Print name of current/working directory|
|ls | -l | List directory contents|
|cd | | Change the current/working directory to the directory specified (by default to home folder)|
|mkdir | -p | Creat new directory|
|cp | | Copy files and directories|
|mv | | Move (rename) files|
|file | | Determine file type|
|cat | | Concatenate files and print on the standard output|
|less | | Displays content of the file and allows you to scroll throught and search for patterns|
|chmod | +x | Change file mode bits (We need this to make files executable)|
|which | | Locate the executable file of the given command|
|man | | An interface to the on-line reference manuals|
|wc | -l | Print newline, word, and byte counts for each file|
|rm | -r | Remove files or directories|

#### A quick exercise to show what the above commands do

Open a terminal.

- Type `pwd` This will show where you are at the moment.

- Type `cd ..` This will move you to the parent directory of the
  current directory

- Type `pwd` you will see that you have moved up one folder in the path

- Type `ls` this will list all the files and directories in the
  current directory

- Type `ls -l` this will also list all the files and directories, but
  now. it also displays the file mode bits, owner, file size, last
  modification and name.

- Now go back to your home directory by typing `cd`

- Create a new directory called **new_dir** by typing `mkdir new_dir`

- Type `ls` so you can see that the new directory is created

- Change to the new folder by typing `cd new_dir`

- Now creat a text file with containing a list of all the files and
  folders in your home directory by typing

        ls -a ~ >list

	(the `-a` option changes the behaviour of `ls`; `~` is a shorthand for the
  _path of your home folder_; `>` this symbol tells the shell that
  instead of printing the output of the program to the screen, save it
  to a file)
  
	- You can check that a new file is created by typing `ls -l`

- You can make a copy of the file by typing

        cp list ls_output.txt
		
    and you can rename the file by typing

        mv list original_file

    You can delete a file by typing

        rm file_name

    _But be carful because unlike in Windows or graphical environments
  in general the **deleted file doesn't end up in the trash, but is
  deleted permanently!**_
    
- Type `file list` this will tell you that it is a **UTF-8 Unicode
  text file**; this a simple so called **plain text file**, which
  means if you open it with any text editor you can make sense of it
  (not like **binary files** which are _illegible_)
  
- Now to see what's inside the file we could use a text editor to open
  it, but now let's see what `cat list` does, and you can also check
  what `tac list` does, see if you can figure out the difference
  
- Let's go back to our home folder by typing `cd` and delete the newly
  created folder, because it is a folder we can't just use
  `rm new_dir`, we need to type `rm -r new_dir`. You can also try
  `rm new_dir` and see what happens.
  
- Now to see how valuable the `cat` command are for dealing with sequences,
  head over to the **sequences** folder by typing `cd sequences/ITS`
  and take a look around with `ls` and examine a few files with
  `cat`. Then type `cat *.fas >ITS.fas` this command creats a
  multifasta file from the 134 single sequence records. (the `*`
  character is a so called **wild card character** which will match
  anything, so all the files that end with `.fas` will be read by
  `cat`)
  
- The `cat` command prints everything to the screen (which is the so
  called **standard output(STDOUT)**), but sometimes the output is to
  long and you can only see the last part of the file/output. In this
  case you can use the `less` command, try it by typing `less ITS.fas`
  
- This program loads the file into a new screen, you can scroll the
  file line by line using the **up** and **down arrows** or page by
  page using the **page up** (also the **b key**) and **page down**
  (also the **f key**). Jump to the end of the file by typing
  **G**(Shift + G) and to the beginning by typing **g**. You can view
  the _help of the_ `less` program by typing **h** and find out how
  you can **quit/exit** the program (don't worry the answer is in the
  first paragraph of the help). When you exited the program, you will
  see that there is now output on the screen just like when you saved
  the output to file.
  
- Now let's see two commands that let us peek into the file. By typing
  `head file_name` (_**replace file_name with the name of a file of
  your choice**_) the first ten lines of the file will be printed to
  the screen, if you want to see the end bit of the file use the
  `tail` command
  
- Now let's go to the parent directory of the current one by typing
  `cd ..` and examine the original multi fasta file, `ITS.fasta`, that
  I used to generate the sequences in the `ITS` **folder**. This file
  contains ITS sequences of _Penicillium_ strains, let's see what
  _Penicillium rubens_ strains were used by typing
  `cat ITS.fasta | grep rubens`.This prints all the lines conatining the pattern
  rubens. And this is the first pipeline you used for this course, the
  `cat` command reads the file and the _**output**_ is given to `grep`
  as an _**input**_, the `|` symbol tells the shell to use the output
  of the first program as the input for the second one. (You could get
  the same result by typing `grep rubens ITS.fasta`)
  
- Now let's see how many ITS sequences from _P. rubens_ strains are in
  the file by typing `cat ITS.fasta | grep rubens | wc -l` (You could
  also use `cat ITS.fasta | grep -c rubense` or
  `grep -c rubens ITS.fasta`). The `wc -l` command counts the number of lines in the
  input. If you want to check if there are really 134 sequence records
  in the file, type `cat ITS.fasta | grep ">" | wc -l`. (This will
  count the number of lines containing `>` and we need to use
  **quotation marks** to tell the shell that `>` is for `grep` and we
  don't want to save anything to a file, see above.)
  
- You can find out more about the commands by typing `man command_name`

## Perl :camel:
### Test installation

To test you have **perl** up and running paste the following into the
shell and execute it by pressing the enter key (or return key).

    perl -e '$a = "!snoitalutargnoC"; $c = "*" . "=" x (length $a) . "*\n"; $b = reverse $a; print $c, "|", $b, "|\n", $c'

### Writing source code

Source code is a fancy name to refer to text file that contains a
program or script.

Using a text editor of your choice, create a file containing the
following:

    #!/usr/bin/perl
    use warnings;
    use strict;
    
    print "Hello, World!\n";


Save the file with a name like `hello`. Using the command-line find the
file and test if it's working properly by typing `perl hello`. Now make
the file executable so you won't have to type perl before it to
execute it by typing `chomd +x hello`. Now to type `./hello` to execute it
and `ls -l hello` to check that we have added execution permission to
the file (**x**).

Congratulations! You have wrote a program using perl!

Now a little explanation.

The first line starts with a shebang `#!` followed by the location of
perl command. This tells the shell that it needs perl to execute the
program. To find the location of any command use the which command,
you can try it by checking the location of perl by typing `which perl`.

The lines starting with `use` are telling perl to use the given **pragmas**,
which are really not necessary at this point, but I think it's good to
get use to them, because they are helpful when developing code.

The real action happens on the last line. The print command tells perl
to print things coming after the command to the screen, in this case
the string `"Hello, World!\n"` which when printed will be `Hello, World!`
followed by a **newline**. An important thing to remember in perl you can
use **whitespace** (spaces, tabs, newlines) freely, but you must separate
the different commands using semicolons (`;`). If you forget to put a
semicolon after a command you will receive an error and your program
will not execute. (Except for the last command in the file and the
last command in a block, but that is further in the course.)

### Pseudocode

First let's learn to walk be for we start running. Before learning the
language for programming in Perl, let's learn to think like a
program. Pseudocode is a good way to design a program or algorithm
before writing the actual code.

The program in the previous paragraph could be written in pseudo code
like this: Print to the screen the message "Hello, World!" followed by
a newline.

Pseudocode is not meant to be read or executed by any program, but to
be read by humans.

This method allows you to break a complex problem into simple
problems. Let's take another example, in the Unix shell exercise above
you used a pipeline to count the number of _Penicillium rubens_ strains
in a multifasta file. Let's write the **pseudocode** for this problem:

- You can start by writing the whole problem: Count the number of
    _Penicillium rubens_ strains in a multi fasta file

    1. Read the file
	2. Only keep the lines that contain _Penicillium rubens_ (by
	    screening for the word "rubens")
	3. Count the number of lines

Now we have the recipe for our analysis, let's collect the necessary
commands and use it. But it is important to check whether the
individual steps work correctly, before accepting the output. The
first part is very simple, just type `cat file_name` and it indeed
prints the content of the file. Next step add our filter which
searches for "rubens" in the lines, by using `| grep rubens`, check the
output and we find that each line has contains "Penicillium rubens"
and not only "rubens". So we won't be counting strains that have the
same epithet but belong to a different genus. And finally count the
number of lines left by using `| wc -l`.

