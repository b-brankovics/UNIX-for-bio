# Introduction to bioinformatics

Bioinformatics is a fairly vague definition. In some sense it contains
everything that is related to biology and is done on a computer.

## How to keep notes
Like working in the lab it is a good idea to keep notes of what we do
and which protocols we use. These are crucial if we want to keep our
work reproducible.

In order to keep our notes in order, we need a format that looks
reasonably good both on graphical and command line text editors. That
is able to maintain a structure for the content and that can contain
links to files and websites, also it needs to be relatively simple to
remain readable and to make it easy for beginners to learn.

One of the most used language that is dedicated to link different
files and documents together is **HTML** (**H**yper**T**ext **M**arkup
**L**anguage). Markup languages are document types where you not only
see the text/content, but also the formatting of the content. The text
is marked up with formatting. Although, **HTML** is relatively easy to
learn and use, but typing your content can be hindered by the effort
you have to put in to properly format your text. This is the reason
why John Gruber has developed a language called **MarkDown**.


### [Markdown](https://daringfireball.net/projects/markdown/basics)
The idea behind **MarkDown** is to have a language where you have
decent control over the formatting, and the structure is apparent in a
command line editor, but keeps the formatting commands at a minimal level.
This language became very popular, because it keeps true to these
ideas. Besides the language itself there are lots of interpreter
programs that can turn this simple formatting to other document types,
such as **HTML** or **PDF**. This has become _the_ language to use
when creating documentation for software tools. One of the most
popular websites that is used to share software solutions is
**GitHub**, where you are probably reading this document.
GitHub employs a version of **MarkDown**, referred to as the ["_GitHub
Flavored Markdown_"](https://help.github.com/categories/writing-on-github/).

### Revision control
After we have found the documenting language of our choice, it is a
good idea to have a way of keeping track of the changes we make to our
documents. That is what revision control systems are used for. One of the
most popular system is [**Git**](https://git-scm.com/).

**Git** is the revision control that is used by **GitHub** and
**BitBucket** two websites that use **MarkDown** as primary
documentation language. These are great places to store your projects,
because you can access them via the internet and you won't have
problems like forgetting where you have put your files.

### GitHub and BitBucket
Which one should you use? **GitHub** is probably the most commonly
used one out of the two. If you are taking a course in data analysis
or bioinformatics you will come across this website. Either to get
access to documentations or to programs. Some of the courses also
require you to sign up to the website.

However, if you are working on a project that you do not wish to be
accessible to the public, you need to have private _repository_ (A
repository is "project" that is handled by a revision control
system). This will allow you to work on your project and access it
easily from different machines, and also to share it with
collaborators, who in turn can also work on the project, without
having to worry about exposing your work to the great public. This is
where it is a good idea to switch to **BitBucket**. Because
**BitBucket** offers you private repositories for free.

## Getting started
Unfortunately, reading is at best only the first step in solving any
kind of problem. So we need to get active and start implementing the
little theory that we have discussed so far.

Exercises:
1. Exercise: Registering

    Sign up to both websites:

    - Github: (https://github.com/)
	- Bitbucket: (https://bitbucket.org/)

2. Exercise: Create first repository

    Look around on [Bitbucket](https://bitbucket.org/) and figure
    out how to create your first repository. If you want you can
    even 	make your repository private.

3. Exercise: Experimenting with MarkDown via BitBucket

    1. Go to your first repository.
    2. You can edit the "README.md" file. This is a MarkDown file that
       is used to create the Home page of your repository. When you
       save changes to this file, then the website automatically
       converts the file to an HTML file, which is used to display the
       Home page of the repository.
	4. Start learning the
	   [MarkDown basics](https://daringfireball.net/projects/markdown/basics)
	   by following the link (the "_MarkDown basics_" is a link).
	   Take notes and experiment with the formatting using your
	   README.md file.
	5. To see the result of the changes save the file.
	6. Use this repo (short for repository) and README.md file to take
       notes that you think are good to have, as you explore more
       about in this tutorial.

4. Exercise: Learning more about **Git**, **GitHub** and **BitBucket**

    1. On **Bitbucket** when you register, you automatically get a
       "Tutorial" repo. Read what it has to say.
	2. Get a basic understanding how **Git** works by following the
       [introductory tutorial](https://try.github.io/levels/1/challenges/1).
	3. Check out what you need to know about
       [GitHub Flavored Markdown](https://help.github.com/categories/writing-on-github/).

## Conclusions
1. You have learned how to create and manage repos in
   **BitBucket**. Feel free to also check out how to do the same
   things with **GitHub**.
2. You have learned a new language (**MarkDown**).
3. You have all you need to keep notes of your work and your new
   knowledge.

Go back to the main page and begin with the next chapter, so you have
more things that are worth recording in this newly learned manner.
