# How to access the command-line

## Unix shell

Unix shell refers to the command-line interface of a Unix based operating system. Unix based operating systems are Linux distributions (Ubuntu, Fedora, Suse, Red Hat, etc.), Mac OS and BSD distributions.

### Using a Unix based operating system

If you are using an operating system that is Unix based, then you only need to open a terminal window to gain access to the shell.

Using Ubuntu you can open the terminal in the following ways:
* `Alt`+`F2` and type **gnome-terminal**
* `Control`+`Alt`+`T`
* **Applications**->**Accessories**->**Terminal**
* If you have a gnome environment and you have installed **Guake** by `F12`
    
Also you can change from the graphical interface to only command-line. First finish reading this paragraph and only then start experimenting with what you read. In the case of Ubuntu there are multiple screens that you can use. You can switch between these using key-combinations. The graphical interface can be reached by pressing `Control`+`Alt`+`F7`. Also there are 6 command-line screens: `Control`+`Alt`+`F1`, `Control`+`Alt`+`F2`, ... `Control`+`Alt`+`F6`. Just remember that on the command-line screens there is no clipboard.

### Using Windows

If you are using Windows you first have to install software that emulates a Unix system or environment. Here are a few ways you can do it:
* **[Cygwin](cygwin.md)**
* **[Running a virtual machine](virtual.md)**
* **[Docker](docker.md)**
* **[PuTTY](http://www.putty.org/)** to connect to a server running a
  Unix based operating system

### [Using a server running Unix](server.md)

You will need an **ssh** program to connect to your server.
On such program is [PuTTY](http://www.putty.org/)
(If you are
working on a Linux based system it is better to stick with the command
line of your system for the moment.) PuTTY provides access to the command line of the server, but you cannot access your files straight away. You have to establish a file transfer connection between your system and the server.

### [Using Docker](docker.md)

Docker can be used with Linux or OS X operating systems as well. The installation becomes more complex as we move from Linux to OS X and to Windows. Docker requires a Linux kernel (the core or base of the operating system) to communicate with. So when you install it on OS X you need an additional program that provides the substitute for the Linux kernel, it is called [boot2docker](http://boot2docker.io). On a Windows operating systems there, first an operating system is needed that can interface with **boot2docker**, so a virtual machine is needed, this is created via [VirtualBox](https://www.virtualbox.org). All these tools are packaged together for Windows users in [Docker Toolbox](https://www.docker.com/products/docker-toolbox).

The following [documentation](https://docs.docker.com/windows/step_one/) shows how to install Docker on a Windows system. There are to requirements: it has to be a 64-bit system and the system must support Hardware Virtualization. These are also explained in the documentation.