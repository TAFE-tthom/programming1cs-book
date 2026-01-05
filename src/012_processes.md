
# Commands, Programs and Processes

## Commands

When opening up the shell you will be presented with a blinking cursor something that looks similar to the following:

Windows (GitBash):

```
user@hostname MINGW64 ~/
$ 
```


Windows (Powershell):

```
PS C:\Users\username>
  
```


Linux (Bash):

```
[user@hostname ~]$  

```

This is the usual first screen that many experienced computer users who have had to use the command line will be familiar with. It is where you can start writing commands and navigating the filesystem.

### What are commands?

Commands are programs that your shell has access to and do not require knowledge in where they live. You can add new commands to your computer and even remove them if you want however that is likely unadvisable.

This now gets into the details of what a **Program** and **Process** is.

* *Program* - This is a file that holds computer instructions native to the cpu and operating system. Simply, it is a container of instructions that can be loaded and executed. (We will expand this definition later on to encompass different kinds of programs).

* *Process* - A process is an *instance* of a *Program*. In the sense that, the same program can be ran multiple-times and usually concurrently and that each time we run a program, we are creating a process in which it executes the instructions that the program holds.

### Commanding the filesystem

Let's finally dive into command line now! We will cover some basic commands that are used to navigate the filesystem.

We will cover the following:

* `pwd` - Print Working Directory
* `cd` - Change Directory
* `ls` - List contents of a directory
* `mkdir` - Make directory
* `touch` - Create a file
* `rm` - Remove a file (and with flags, directories)
* `mv` - Move a file (or rename it)
* `cat` - Reads a file and outputs it to *standard output*
* `echo` - Print to *standard output*


#### The Tour!

The following will be using a unix shell, it is expected that the same commands will work with Windows however, there are going to be some changes to acknowledge.

**Let's start!**

The `~` represents out home directory, usually where the the current `user` will store their files. We will find out what the *path* is by using `pwd`.

```
[user@hostname ~]$ pwd
/home/user
```

*Viola!*, We have observed that we are currently in `/home/user`.

Do note: On your own system it won't be 1:1, for example, `user` will likely be the same as the username you use to login to your computer.

To get the contents of our `home` directory. We will use `ls`.

```
[user@hostname ~]$ ls
Documents    hello.txt    Pictures    Videos
Downloads    Music        Public       
```

We observe the above folders and single file called `hello.txt`. On your own system it is unlikely you have this file, however you can create it by using `touch` and remove it by using `rm`.

Let's remove it!

```
[user@hostname ~]$ rm hello.txt
[user@hostname ~]$ ls
Documents    Music    Public
Downloads    Pictures Videos       
```

**Take note!**, prior to this command, we have been just using commands without inputting **Command Line Arguments**. We have now just specified our first argument with the `rm` command. This allows us to communicate that the filename to `rm` knows what is to be removed.

We can observe the effects of changes we have made to our directories and files by using `ls` to see what has been added and removed.

Since we have just removed it (or in your case, you probably want to do this step first!), let's recreate it!

```
[user@hostname ~]$ touch hello.txt
[user@hostname ~]$ ls
Documents    hello.txt    Pictures    Videos
Downloads    Music        Public       
```

It is now back! Let's now get ready for all our big projects we will start working on! Let's create a `Projects` folder. To do this, we can use `mkdir`.

```
[user@hostname ~]$ mkdir Projects
[user@hostname ~]$ ls
Documents    hello.txt    Pictures    Public
Downloads    Music        Projects    Videos   
```

We gave `Projects` as an argument for the `mkdir` command, it then created a new directory under that name.

Let's now `m`o`v`e the file `hello.txt` to `Projects`. However, let's first observe what is in `Projects`!.


```
[user@hostname ~]$ ls Projects

```

Nothing! Well, it is to be expected but we are seeing how the commands we use can handle data we specify. Now, we will move `hello.txt` using a *relative path*.

```
[user@hostname ~]$ ls
Documents    hello.txt    Pictures    Public
Downloads    Music        Projects    Videos

[user@hostname ~]$ mv hello.txt Projects/hello.txt 
[user@hostname ~]$ ls
Documents    Music    Projects    Videos
Downloads    Pictures Public
     
[user@hostname ~]$ ls Projects
hello.txt
```

We have now observed that the file has moved from `~` to `~/Projects`. Or another way we can look at this is that the file at `/home/user/hello.txt`
is now at `/home/user/Projects/hello.txt`.

```
[user@hostname ~]$ cd Projects
[user@hostname Projects]$ pwd
/home/user/Projects

[user@hostname Projects]$ ls
hello.txt
```

We have moved our **current working directory** (cwd) to `/home/user/Projects`. 

Now to complete our little journey, let's do something to remember what we did here! Let's celebrate with `echo`.

```
[user@hostname Projects]$ echo "Woohoo, using the command line"
Woohoo, using the command line
```

We can observer we have printed the text we inputted as an argument for echo. Now let's keep this text, we will use a little symbol that allows us to redirect output of a program to different destination.

`>` - While this operating is going to seem strange for first time users, within the context of bash, it allows us to take the output of a program and write it to a file.


```
[user@hostname Projects]$ echo "Woohoo, using the command line" > hello.txt
```

We notice then, that the program doesn't output to the shell again. So! Let's confirm that it wrote to `hello.txt` by running `cat`.

```
[user@hostname Projects]$ cat hello.txt
Woohoo, using the command line
```

There we go! We have now saved the text to a file and read it back out.

