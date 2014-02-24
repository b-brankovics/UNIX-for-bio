# Cygwin

You can download the installation file from [here](http://cygwin.com/install.html). Make sure that you select Perl for installation!

After installation there are two ways to use the Unix tools:

* Running cygwin. This will open a terminal window where you can type the commands.
* Adding cygwin's bin folder to the path of your system and then open a command-line window.

### Adding cygwin's bin to the path

Go to **System Properties** > **Advanced** tab > `Environment Variables...` button > in the new dialogue window add a new variable by pressing the `New...` button for your user type **Path** as variable name and **C:\cygwin\bin** as variable value (Watch out! C:\cygwin\bin is the default folder for cygwin, but if you installed it somewhere else you have to insert the location of your installation). Hit `OK` on all windows that are open then if you start a command-line window and type `ls` hit enter and it should list all the files and folders in the current directory. Done.
