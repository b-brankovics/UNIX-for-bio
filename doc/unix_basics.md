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

    mkdir -p house/first_floor/kitchen

This creates three directories: `house`, `first_floor` inside `house` and
`kitchen` inside `house/first_floor`.

You can see that we used "_" to separete "first" and "floor" instead
of a " ". Many Windows users are surprised when they get files from
Linux users like `My_project` instead of "My project". Let's see why.

Try issuing the following:

    mkdir -p house/first floor/kitchen

This command creates a folder inside `house` called `first` and
creates `floor` inside the working directory plus `kitchen` inside
`floor`.

If we really want to create a "first floor" with a space, we need to
_escape_ the space, otherwise mkdir will think we specified to
arguments. The escape character is `\`.

    mkdir -p house/first\ floor/kitchen

This created the expected result. But if we use `ls` we won't see the
escape character in the folder name, but we have to use it when we
want to `cd` into the folder. So it is better to avoid spaces inside
file names and folder names.

You can use `cd`, `ls` and `pwd` to explore what you have created.

### `touch` - change file timestamps

We will use this command to create empty files. To use for basic file
operations.

    touch stove

Creates a new file called `stove` if it did not exist before. If it
already existed, then it will change the _timestamp_. You can check
this using `ls -l`. Wait a minute or two and `touch` the file again,
you will see the timestamp has been changed. You can also specify a
file as an argument for `ls`, such as `ls -lh stove`.

### `cp` - copy files and directories
To copy a file we need to use the `cp` command with two arguments: the
source file(s) and the where we want to have them or the name.

    cp stove chair

This created a copy of `stove` in the same directory, and the new file
is `chair`.

Let's go to the `first_floor` and create a few rooms and add
some furniture to them.

    cd house/first_floor
	mkdir living_room study_room bathroom
	touch chair1 chair2

Now we have a few rooms and two chairs.

Let's create a second chair and copy them to the living_room.

    cp chair chair2
	cp chair* living_room/

We used a **glob** by adding a **wildecard** character `*`.
With the help of **wildecard** characters you can specify more then
one files or directories in a single argument. This is interpreted by
the command line interface and all possible _matches_ are handed to
the command as separate arguments. In this case we used `*`, which
represents "any character(s)". So it will match both `chair` and
`chair2`. These will be both copied to the directory `living_room`.

Let's create a `bedroom` and add a `bed` to it.

    mkdir bedroom
	touch bedroom/bed

We also one to have a second floor with a bedroom with a bed
inside. We need to use a special option to copy folders `-r`,
recursive.

    mkdir ../second_floor
	cp -r bedroom/ ../second_floor/

Let's add chairs to all of the rooms.

    cp chair* *room/

Now we have two chairs in the `living_room`, `study_room`, `bedroom` and
`bathroom`. Oops, I guess we should have used `_room*` instead of
`*room`, because now we have two chairs in the bathroom.

### `mv` - move (rename) files
The `mv` command can move files from one location to another. This
means you can move file from one folder to another or that you rename
the file. Because both of these will change the path that leads to the
file.

Let's remove a chair from the bathroom.

    mv bathroom/chair1 .

We moved a chair from the bathroom to the current directory.

Let's rename the other one to a bath.

    mv bathroom/chair2 bathroom/bath

We are expanding the house and we add a new floor, and we want to move
the bedroom to the new floor.

    mkdir ../third_floor
	mv bedroom ../third_floor/.

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
