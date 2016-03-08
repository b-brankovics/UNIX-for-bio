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

Let's go to the `first_floor`

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

Copy the stove to the kitchen

    cp stove kitchen/stove

Create a few rooms and add some furniture to them.

    cd house/first_floor
	mkdir living_room study_room bathroom
	touch chair1 chair2

Now we have a few rooms and two extra chairs.

Let's create a second chair and copy them to the living_room.

    cp chair chair2
	cp chair* living_room/

We used a **glob** by adding a **wildecard** character `*`.
With the help of **wildecard** characters you can specify more then
one files or directories in a single argument. This is interpreted by
the command line interface and all possible _matches_ are handed to
the command as separate arguments. In this case we used `*`, which
represents "any character(s)". So it will match both `chair`, `chair1` and
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

    cp chair* living_room
    cp chair* study_room
    cp chair* bathroom

Now we have two chairs in the `living_room`, `study_room` and
`bathroom`. Oops, I guess we should remove the chair from the bathroom.

### `mv` - move (rename) files
The `mv` command can move files from one location to another. This
means you can move file from one folder to another or that you rename
the file. Because both of these will change the path that leads to the
file.

Let's remove two chairs from the bathroom.

    mv bathroom/chair? .

`?` is another wildcard character, it represents a single
character. So in our case it represents `chair1` and `chair2`, but not `chair`.

We moved two chairs from the bathroom to the current directory.

Let's rename the other one to a bath.

    mv bathroom/chair bathroom/bath

We are expanding the house and we add a new floor, and we want to move
the bedroom to the new floor.

    mkdir ../third_floor
	mv bedroom ../third_floor/.

The bedroom is gone from the first floor, but there is one now on the
third floor.

### `rm` - remove files or directories
It is also important to remove files or directories. But we have to be
careful, because unlike in a graphical environment, where the deleted
files are moved to the trash. On command line interface the files are
completely removed. So be careful, especially with wildcard
characters.

Let's remove the chairs that are outside of the rooms on the first
floor.

    rm chair*

We can also use the `-v`, verbose, option. So we see what we delete.

    rm -v stove

We want to clean up the mess inside the house and remove the floor
that was created by mistake. But these are directories, so we need the
`-r` option as with copy.

    cd ..
	rm -r first first\ floor
	rm -rv ../floor

The second remove command remove to folders:
- `../floor/kitchen`
- `../floor`

That is why we needed to run `rm` in a recursive fashion, so first the
content is removed and the empty folder is removed as last.

### `echo` - display a line of text

The `echo` command can print some text.

    echo "some text"

So far, we have worked with empty files. Let's create one with bit of
text, using `echo`.

    echo "The content of the file is one line" >text

We have created a file `text` with a single line of text "_The
content of the file is one line_" by telling the shell to put the
output of the command in a file. This is done by using the `>`
character.

Let's create a new one and add extra text to it.

    echo "The content of the file" >new
	echo "Line two" >>new

The `>>` character is similar to `>`, but this one will append to the
file, if it already exists. The other one replaces its previous
content with the new one.

So we can write files and add content to them. It is time to learn to
read as well.

## Reading files
### `cat` - concatenate files and print on the standard output

This command takes the content of all the files that are specified as
arguments, concatenates them and prints them.

    cat text
    cat new
	cat text new

Let's create file with a single line and concatenate it many times to
the new file. And add line with "The End".

    echo "Extra line to make it longer" >line
	cat line line line line line line line >lines
	cat lines lines lines lines lines lines >>new
	echo "The End" >>new

So `new` is 45 lines long.

### `head` - output the first part of files
Sometimes we want to see only a part of the content.

    head new

This will print the first ten lines of `new`.

We can specify that we want to see only the first line:

    head -1 new

or

    head -n 1 new

We can also specify how many lines should be left out from the
end. Let's print it without the "The End".

    head -n -1 new

### `tail` - output the last part of files
The "opposite" of `head` is `tail`. We can check the end of the file.

    tail new

We can check the last line:

    tail -1 new

We can also specify which should be the first line that is printed. So
`tail -n +1 new` is the same as `cat new`.

    tail -n +2 new

This prints everything starting with the second line.

We can now print selected lines if we use a **pipe**, `|`. Let's print
only the second line

    head -2 new | tail -1

The head command read the `new` file and printed the first two lines,
which were not printed on the screen, bit were fed to the tail
command, which printed the last line of what it got.

Let's create an extra long file by using parts of the `new` file.

    head -n -1 new >other
	head -n -1 new | tail -n +3 >>other
	head -n -1 new | tail -n +3 >>other
	head -n -1 new | tail -n +3 >>other
	tail -1 new >>other

### `more` - file perusal filter for crt viewing
Sometime a file is to big to display at once, but we still want to see
the whole content. Simply sometimes we want to see more, so we use
`more`.

    more other

This will display as many lines as can fit on the screen then it
waits. If you hit "return"/"enter" then it move one line further in
the file. If you hit "space" or use "Ctrl+D" it moves by one page. If
you hit "q" or "Ctrl+C" then it will quit. Otherwise it will quit when
it has displayed everything.

The problem is that you sometimes want to move back as well.
### `less` - opposite of more
Then you need `less`. With `less` you can move back and forth in the
file, also you can search.

    less other

Similar to `more` it displays the first part of the file and waits for
your instructions, which are somewhat similar. Next "return" you can
use the down arrow as well to move down. The only way to quit is by
typing "q". If you type "h" then you get the help to learn more about
what you can do with `less`.

### `wc` - print newline, word, and byte counts for each file
We already know that `other` is a relatively long file, but how long
is it. We can check that using `wc`.

    wc other

This will print the number of lines, the number of characters and the
size in bytes of `other`.

If we only want to print the number of lines than we can use the `-l`
option.

    wc -l other

## Learning more about commands
If we want to learn more about a given command we can ask the command
for some help. Which we can do with the `--help` option or sometime
with `-h`.

    wc --help

### `man` - an interface to the on-line reference manuals
We can also check their manual if they have that.

    man wc

This will display the manual in a `less`-like manner.

Some commands don't have it:

    man cd

But what do you think? Does `man` have a `man`?

    man man

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
5. Learned how to **pipe** (`|`) the output of one command to another
   command and to store the output in files (`>` and `>>`).

# Further material

- [Online tutorial](https://www.codecademy.com/learn/learn-the-command-line)
- [More about Unix command line](empty.md)
   
