# Command Line

Depending on your operating system, you will have access to a commandline interface. However, not all these interfaces are *exactly* the same.

On **Windows**, you will have access to **Powershell** and **Command Prompt**, the former being a lot more powerful and closer to a *unix shell*. However, you can get access to a *unix shell* by install **Git Bash** which will provide some amount of compatibility with your 

On **Linux** or **MacOS**, you will have access to a **Unix Shell**, which can come in the form of **Bash**, **Zsh**, **Fish** and **Sh**.

This book will assume you are using a *unix shell* .

## Why a "Unix Shell"?

This is because the standard deployment platform for applications is Linux. If you deploy a web application, it will likely be on a linux server.

In addition to deployment, most tooling and scripts have been setup for these shells where Windows is not always given the same amount of consideration.

The *unix shell* is used in informatics heavily as a lot of commands available and features allow for composition and piping of data between each other.

## How do I access the shell?

On Windows, you can access the shell by doing the following:

1. Click the Windows Button

2. Write as part of the search "Bash", if *Git Bash* is installed, it should show up as the top suggested program.

Alternativesly, you can use *Powershell*.


On MacOS, you can do the following:

1. Click on the Launchpad Icon in the Dock

2. Type "Terminal", this should give you access to the terminal application which will open up *Zsh*.

Alternatively, you can access it in `/Applications/Utilities` folder and click on `Terminal`.

On Linux, if you are on Gnome or KDE, both provide search functionality to open up a shell.



## Basic Commands and Concepts.

Each chapter and topic will usually outline the following concepts that you will learn and want to make sure you understand.

### Concepts

You will learn about the following first.

* Filesystem, Directories and Files

* Pathing and Naming

* Commands, Programs and Processes

* Command Line Arguments and Flags

### Filesystem

A primary usecase with the shell is to interact with the *Filesystem*. The *Filesystem* is a representation of what is on your hard-drive.

This representation is made up of *Files* and *Directories*.

* A *File* holds data, this could be an image or text file or even a program itself.

* A *Directory*, occasionally called a *Folder*, can contain a number of *files* and *folders*. You may be familiar with these concepts with the GUI.
* A *Filesystem*, is the system that is used to organise both directories and files. There are many different kinds of file systems but primary interaction and model is a **Tree** structure.

Both Windows and Linux utilise a **Tree** structure, everything starts at the root directory which is either `/` or commonly for Windows `C:\`.

*File paths* outline where, relative to the current position or relative to the root of the filesystem is, a file is location. There are two kinds of paths, *relative* and *absolute*.

* *Absolute* path is based on the root of the filesystem or drive.

* *Relative* path is based on a position that could be anywhere on the system.

For some examples:

* `C:\Windows` - This is an absolute path and points to the `Windows` directory in the C drive.

* `/home/user/Documents` - An absolute path, based on the `/` root of the filesystem.

* `../Documents/notes` - Relative path where `..` indicates the parent directory (folder that contains `Documents`).

* `Videos\FilmsFromDecember\log.mp4` - Relative path, whichever directory that the user is currently in, they expect `Videos` to exist within it and `FilmsFromDecember` to be nested inside it.

Note: Windows uses `\` for separating directories while Linux and Mac uses `/`.  

### Pathing and Naming

To continue with pathing and naming, you can start seeing a pattern in how directories are structured. However, file names may be a little elusive, especially when we see `.mp4` and `.docx` associated with them.

#### File Extension

File Extensions have been around for a very long time, however files don't necessarily **need** to have an extension, they can exist without them. However they are very **helpful** for the operating system so it knows what application it should launch it with.

As a quick test:

* What application launches when you open a `.docx`?

* What application launches when you open a `.png`?

* Can you change the default application you want to launch it with?


## Knowledge Tasks

Make sure you take note of the following concepts and have a quick summar of what they are.

1. Find an example of a shell, specifically find information that will inform you what the differences are between Bash, Zsh and Powershell are.

2. Given the scope of the document, consider why deploying on Linux Servers is very common. Consider what domains (like Software Development, Computer Graphics, Web Development, Informatics) linux is used in.

3. Given the brief introduction of a filesystem, provide some concrete examples of a file. What are some file types you commonly open and how do you organise your files?

