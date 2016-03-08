# Unix basics
This introduction shows some of the basic file and folder operations
on a Unix command line.

## Looking around and moving around

### `ls` - list directory contents
To see what files are located in the current working directory, we
have to use the `ls` command.

    ls

The block you see above this paragraph is a command line block. This
uses a monospace font type (every character has the same width). These
blocks show what should be typed on the command line.

The `ls` command will list all the files and directories that are found
in the current directory. Usually, regular files, executables and
directories are displayed in different colors by the shell (command
line interface).

If you want to know a bit more about the files, then you can use `-l`
option, which shows more information

    ls -l

This is the long format, displaying Unix file types, permissions,
number of hard links, owner, group, size, last-modified date and
filename

The file size by default printed in bytes, but you can add an extra
option `-h`, human readable, to print the size in a the largest unit
that has a value greater than or equal to one.

    ls -lh

### `pwd` - print name of current/working directory

The `pwd` command prints the current directory where you are
located. If you have just logged in then it is probably going to be
your _home directory_.

    pwd

Prints something like: `/home/user`



# Summary
1. Learned the some of the basic commands:
    - `ls`
	- `pwd`
	- `cd`
	- `mv`
	- `rm`
	- `touch`
	- `echo`
	- `cat`
	- `less`
	- `head`
	- `tail`
	- `wc`
	- `man`
2. Learned that Unix commands can have options that modify how they work
3. Learned a few shortcuts:
    - `~` Home directory of the user
	- `.` This directory
	- `..` The parent directory of this directory
4. Learned the basics of the Unix filesystem
    - Relative path
	- Absolute path
	- What is the root directory
	- Why Unix users don't like spaces in the file names
