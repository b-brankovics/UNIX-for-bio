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

### `cd` - change directory

The `cd` command modifies the current working directory.

If you issue without specifying anything, then it changes the working
directory to be your home directory.

When you want to change to another directory then you need to specify
an _argument_ or _parameter_ for `cd`, which tells where to go.

If you want to change to a directory inside the current directory,
named _dirname_, type the following.

    cd dirname

Then the working directory has been changed to that one. You can
verify this by issuing the `pwd` command. Which prints something like:
`/home/user/dirname`

From `/home/user` to `dirname` it was enough to specify the
`dirname`. But if you are somewhere in the filesystem you need to
specify a different **path**.

There are two types of paths:

- Absolute path: `/home/user/dirname`
- Relative path: `dirname`
    If you are in the `/home/user` folder.

    If you are in the `/home` folder, then the relative path to the
    same location becomes `user/dirname`.

A little bit about the filesystem on a Unix system:
- There is a **root** directory, "`/`". All the other directories are
  located inside this directory.
- All absolute path start from the root directory "`/`". In the
  absolute path above, `/home/user/dirname`, the first "`/`" is the
  root directory.
- You separate the levels of directories by "`/`".
- Every user has a **home** directory, "`~`" or `/home/username`. When
  you log in this is where you are by default. Also this is where you
  get if you issue `cd` without arguments.
- The current directory can be referred to as "`.`". This is used for
  relative paths.
- The parent directory is referred to as "`..`". This is used for
  relative paths.

You can take a look around if you like or read forward and get
familiar with `cd` by making new directories at the same time.

## Creating and removing files and directories
### `mkdir` - make directories

The `mkdir` command create directories.

    mkdir dir1

Creates a directory `dir1` inside the current directory.
You can also create multiple directories at the same time.

    mkdir dir2 dir3

This create two new directories: `dir2` and `dir2`.

You can create directories inside directories that are not there yet,
by using the `-p`, parents options. This will create all the
directories that are mentioned in the path.

    mkdir -p dir4/newone/child

This creates three directories: `dir4`, `newone` inside `dir4` and
`child` inside `dir4/newone`.

You can use `cd`, `ls` and `pwd` to explore what you have created.

### `touch` - change file timestamps

We will use this command to create empty files. To use for basic file
operations.

    touch file1

Creates a new file called `file1` if it did not exist before. If it
already existed, then it will change the _timestamp_. You can check
this using `ls -l`. Wait a minute or two and `touch` the file again,
you will see the timestamp has been changed.

### `cp` - copy files and directories
### `mv` - move (rename) files
### `rm` - remove files or directories
### `echo` - display a line of text

## Reading files
### `cat` - concatenate files and print on the standard output
### `more` - file perusal filter for crt viewing
### `less` - opposite of more
### `head` - output the first part of files
### `tail` - output the last part of files
### `wc` - print newline, word, and byte counts for each file
### `man` - an interface to the on-line reference manuals


# Summary
1. Learned the some of the basic commands:
    - `ls`
	- `pwd`
	- `cd`
	- `mkdir`
	- `touch`
    - `cp`
    - `mv`
	- `rm`
	- `echo`
	- `cat`
	- `more`
	- `less`
	- `head`
	- `tail`
	- `wc`
	- `man`
2. Learned that Unix commands can have options that modify how they work
2. Learned that Unix commands can have arguments that tell what to
   open, read or modify
3. Learned a few shortcuts:
    - `~` Home directory of the user
	- `.` This directory
	- `..` The parent directory of this directory
4. Learned the basics of the Unix filesystem
    - Relative path
	- Absolute path
	- What is the root directory
	- Why Unix users don't like spaces in the file names
