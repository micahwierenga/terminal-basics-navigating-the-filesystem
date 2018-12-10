<!--
booj
-->

<!--1:30 5 minutes -->

<!-- Hook: *Go to https://hackertyper.net/.  Raise your hand if you have this idea of a computer hacker--typing in super-fast, hunched over their green and black monitor, as images flash super-fast in front of them?

Even if you don't, most of the world does. Today, we're going to try and earn those chops, but spoiler alert: it's a lot slower, and less glamorous than the movies make it seem.  

Hopefully by the end of this class, I can get you to love, or at least like, the errors that will guide you to becoming that leet haxor that the world already thinks you are. -->

# Terminal Basics + Navigating the Filesystem

![](unix_system.jpg)

## Why is this important?
*This workshop is relevant to developers because:*

- You will be using your terminal almost every day as a developer.
- It will help you understand your Operating System better.

## What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*

- **Summarize** a basic filesystem structure, including absolute and relative paths
- **Use** the most common commands to navigate and modify files / directories via the Terminal window (`cd`, `pwd`, `mkdir`, `rm -r`, `mv`, `cp`, `touch`)
- **Describe** a basic UNIX permissions system
- **Differentiate** between navigating the file system using the CLI vs. the GUI

## Where should we be now?
<!-- call out the skills that are prerequisites -->
*Before this workshop, developers should already be able to:*

- **Open** the terminal
- **Basic understanding** of file structure

---

<!-- 1:35 5 minutes -->

##  Intro
<details>
  <summary>What is a GUI (pronounced gooey)?</summary>
  <p>There was a time when computers didn't come with a Graphical User Interface (GUI). Instead, everyone interacted with the computer using text commands in what we call a Command Line Interface (CLI).</p>
</details>
<br>
<figure>
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/94/FreeDOS_Beta_9_pre-release5_%28command_line_interface%29_on_Bochs_sshot20040912.png" alt="Terminal">
  <br>
  <figcaption>Image from Wikimedia</figcaption>
</figure>
<br>
<!-- Today, the command line still exists, even though you may have never seen it as a casual computer user. 

In this course, we are going to spend a lot of time in the command line, and we will use it every day to manage our files and tell our computer how to run our programs. 

It will greatly speed up our development process and help us take ownership of our computer at a deeper level. 

There is so much that your computer will do for you if you know how to speak its language! -->
<br>

<details>
  <summary>What is a shell?</summary>
  <p>A shell is a type of command-line program, which contains a very simple, text-based user interface enabling us to access all of an operating system's services. It is a program that accepts *text as input* and *translates that text* into the *appropriate functions* that you want your computer to run.</p>
  <p>*Taken from Just for fun: [Type like a hacker](http://hackertyper.com/)*</p>
</details>

---

<!-- 1:40 5 minutes -->

<!-- Half-mast I do -->

## Forget Finder, get fast at using your laptop

### Opening & Closing Terminal 

First, we need to launch the command prompt. We do this by using spotlight:

- ⌘ (Command) + Space
- "Terminal"
- Enter

Notice that you can actually hit enter as soon as the field autocompletes. Get used to taking shortcuts – don't type the whole word out if you don't have to and avoid using your mouse if you can open or use an app with just keyboard shortcuts. It may seem harder now, but when you get used to it, it will save you literally hours of cumulative time.

### Getting Comfortable

- For many programs, you can open multiple tabs by pressing **⌘-T**.
  - Try it in your terminal!
- You can close the current tab or window with **⌘-W**. This goes for most applications on a Mac.
  - Try _that_ in your terminal!
- If you have a process running, you can quit it by pressing **Ctrl-C**. Let's try that now.

  - At the command line, type `ping 127.0.0.1`. This basically sends a message to your own computer asking if it's awake.
  - Notice that it will keep pinging, even if you type something.
  - To stop the currently-running script, press **Ctrl-C**.

- To quit the command line altogether, you can press **⌘-Q**.

<!-- Open up and do all, half-mast when done, help neighbors if stuck -->

---

<!-- 1:45 10 minutes -->

## Basic Navigation, and Creating Files and Directories

<!-- Before this, run through all of the commands that do these things with dev input-->

| Command   | Explanation                             |
|-----------|-----------------------------------------|
| `mkdir`   | Creates a new directory                 |
| `touch`   | Creates a new file                      |
| `cd`      | Changes directory                       |
| `ls`      | Lists all non-hidden files in directory |

From your home directory, make a 
* a file named my ``my_birthday_<you birthday in yy_mm_dd format>.txt``, example ``my_birthday_79_05_11.txt``.
* a directory named ``temporary_work``
* a file named ``i_love_javascript.js`` in the ``temporary_work`` directory
* make a directory named ``booj-coding`` and another directory in ``booj-coding`` named ``lessons``
* list out the contents of the ``temporary_work`` folder 

We'll do this exercise together.

### Paths 

Every file or folder in a file system can be read, written, and deleted by referencing its position inside the filesystem. When we talk about the position of a file or a folder in a file system, we refer to its "path". There are a couple of different kinds of paths we can use to refer to a file:

- **absolute paths**
- **relative paths**

*Directory* is an important term that's used interchangeably with *folder*. Though they are not exactly the same thing, when we say "navigate to your project directory" think of this as "navigate to your project folder".  Here's a little more information:

_Strictly speaking, there is a difference between a directory which is a file system concept, and the graphical user interface metaphor that is used to represent it (a folder).... If one is referring to a container of documents, the term folder is more appropriate. The term directory refers to the way a structured list of document files and folders is stored on the computer. It is comparable to a telephone directory that contains lists of names, numbers and addresses and does not contain the actual documents themselves._

*Taken from [Close-To-Open Cache Consistency in the Linux NFS Client](http://www.citi.umich.edu/projects/nfs-perf/results/cel/dnlc.html)*

*Absolute Paths*

An absolute path is defined as the specific location of a file or folder from the root directory, typically shown as `/`. The root directory is the starting point from which all other folders are defined and is not normally the same as your **Home** directory, which is normally found at `/Users/[Your Username]`.

```bash
/usr/local/bin/git
/etc/example.ext
/var/data/database.db

```
Notice, all these paths started from `/` directory which is a root directory for every Linux/Unix machines.

Some examples of absolute path:

*What is a relative path?*
A relative path is a reference to a file or folder **relative** to the current position, or the present working directory (pwd). If we are in the folder `/a/b/` and we want to open the file that has the absolute path `/a/b/c/file.txt`, we can just type:

```bash
open c/file.txt
```

or

```bash
open ./c/file.txt
```

At any time, we can also use the absolute path, by adding a slash to the beginning of the path. The absolute path is the same for a file or a folder regardless of the current working directory, but relative paths are different, depending on what directory we are in. Directory structures are laid out like `directory/subdirectory/subsubdirectory`.

<!-- Ask for dev input (what is relative vs absolute) but with real examples on my computer. A useful metaphor is giving directions to a location by either starting from the same place every time or starting from your current location -->

Below are some examples of using relative and absolute path for the same action:

- My present location is `/booj-coding/lessons` and now I want to change directory to `/booj-coding`.

  - Using relative path: `cd ..`
  - Using absolute path: `cd /booj-coding`

- My present location is `/booj-coding/lessons` and I want to change the location to `/booj-coding/labs`

  - Using relative path: `cd ../labs`
  - Using absolute path: `cd /booj-coding/labs`

By the way, your terminal is located in:

```bash
/Applications/Utilities/Terminal.app
```

### Navigating through the command prompt

The tilde `~` character is an alias to your home directory. Use it to quickly return home.

```bash
cd ~/
```

We're "looking into" the User directory at this point; use **Tab** and the **arrow keys** in the command line to increase your speed while navigating the command line.

Pressing **Up** scrolls through previously entered commands.

<!-- 1:55 - 10 mins -->

## Copying and Moving Files

Copying files and folders? `cp file new-file1` creates a copy of the “file” and calls it “new-file” in your current directory. If you're looking to copy directories you'll have to pass in a `-r`, which stands for "recursive," to copy the directory and everything inside of it:

```bash
cp -r my-project my-project-copy
```

Create a copy of the entire "my-project” directory and call it “my-project-copy". You could always chain a file path onto the second argument and create the copy elsewhere:

```bash
cp -r my-project my-project-copy/copy-within-a-copy
```

How about removing files and folders? Well, we talked about that earlier, but let's practice: `cd` to your root directory and do the following:

```bash
touch junk-file.txt
mkdir junk-directory
touch junk-directory/inner-junk-file.txt
ls
```

Now, you should see a `junk-file.txt` and a `junk-directory` in your root directory. But let's get rid of them:

```bash
rm junk-file.txt
rm -r junk-directory
```

The first command removes the file `junk-file.txt`; the second removes the directory `junk-directory` and everything inside of it (`inner-junk-file.txt`) because we passed the `-r`, which stands for "recursive". You could also accomplish this with `-rf`. The `f` stands for force but use this with caution and make sure you are in the right place. You can imagine how bad the results could be if you did that to your home folder!

### Modifying multiple files at the same time

Now, if you're making a whole bunch of files/folders, `mkdir`, `rm`, and `touch` can be used to create and remove more than one file/directory at the same time.

Try it out. First, `ls` to see what you have in there and then:

- `mkdir directory01 directory02 directory03`
- `touch file01 file02 file03`
- `rm file01 file03`

Thinking about this command with relative and absolute paths:

- If my present location is `/a/b/`, and I am want to remove `/a/b/folder/file.txt` file

  - Using relative path: `rm folder/file.txt`
  - Using absolute path: `rm /a/b/folder/file.txt`

- If my present location is `/booj-coding/labs`, and I want to remove a `a.txt` file located in this directory

  - Using relative path: `rm a.txt`
  - Using absolute path: `rm /booj-coding/labs/a.txt`

Finally, we can rename and move files and folders with this syntax:

```bash
mv file-name file-name2
```

The first argument is the file or folder being moved or renamed, and the second argument is the directory destination you can use to also rename the file/folder if you want. For example, from your root directory:

```bash
mkdir this-folder that-folder
touch this-file.txt that-file.txt
mv this-file.txt this-folder
mv that-file.txt that-folder/that-fileeeeeee.txt
```

Notice now, `this-folder` has a `this-file.txt` within it and `that-folder` has a `that-fileeee.txt`.

A few other helpful commands you can try on your own:

| Command   | Explanation                                                           |
|-----------|-----------------------------------------------------------------------|
| `ls -a`   | Lists all items in current directory including hidden files           |
| `ls -l`   | Gives a long list of items in current directory including permissions |
| `history` | lists entire commands history                                         |
| `df -h`   | displays free disk space                                              |

<!-- 2:05 - 10 minutes -->

## UNIX permissions and Chmod

An OS is meant to serve many users, A user may correspond to a real-world person, but also a program that acts as a specific user. In my laptop OS, let's say I am "Gerry" and with gerry goes a set of permissions and restrictions on all files and folders. But I can also act for some specific program as the user "www" which corresponds to the privileges necessary to operate the local web server. Every User on the OS has a User ID - the name "Gerry" or "www" is just an alias for a User ID.

Users can be organized in groups. A user may be in one or several groups. A group will have the same set of permissions for every user assigned to this group.

Every file has an owner user and an owner group. So, for any file in the system, user 'gerry' may have one of the following ownership relations:

* gerry owns the file, i.e. the file's owner is 'gerry'.
* gerry is a member of the group that owns the file, i.e. the file's owner group is 'booj-coding'.
* gerry is neither the owner, nor belonging to the group that owns the file.

Every file on the system has associated with it a set of permissions. Permissions tell UNIX what can be done with that file and by whom. There are three things you can do with a given file:

* read it.
* write it.
* execute it.

Permissions for a file will specify which of the three actions above can be performed for groups and users in an OS.

For every file, there are 3 types of permissions: permissions for the owner, for the owning group, and for everyone else. Remember that there are three possible actions a user can take on a file: read (r), write (w), execute (x). So, for each of the three permissions we need three actions.

If you change the present working directory to the root (`cd /`) and then show the folder content with the details by typing `ls -l` on the command prompt, you will get something like this:

```bash
 0 drwxrwxr-x+ 93 root  admin  3162 Aug 15 19:37 Applications
 0 drwxr-xr-x+ 66 root  wheel  2244 Jan 18  2015 Library
 0 drwxr-xr-x@  2 root  wheel    68 Sep  9  2014 Network
 0 drwxr-xr-x+  4 root  wheel   136 Jan 18  2015 System
 8 lrwxr-xr-x   1 root  wheel    49 Apr 14  2014 User Information -> /Library/Documentation/User Information.localized
 0 drwxr-xr-x   6 root  admin   204 Jan 18  2015 Users
 0 drwxrwxrwt@  5 root  admin   170 Aug 15 16:35 Volumes
 0 drwxr-xr-x@ 39 root  wheel  1326 Apr 28 21:05 bin
 0 drwxrwxr-t@  2 root  admin    68 Sep  9  2014 cores
 0 drwxr-xr-x   3 root  wheel   102 Sep  8  2014 data
10 dr-xr-xr-x   3 root  wheel  4805 Aug 14 11:45 dev
 8 lrwxr-xr-x@  1 root  wheel    11 Jan 18  2015 etc -> private/etc
 2 dr-xr-xr-x   2 root  wheel     1 Aug 15 19:42 home
 2 dr-xr-xr-x   2 root  wheel     1 Aug 15 19:42 net
 0 drwxr-xr-x@  6 root  wheel   204 Jan 18  2015 private
 0 drwxr-xr-x@ 59 root  wheel  2006 Apr 28 21:05 sbin
 8 lrwxr-xr-x@  1 root  wheel    11 Jan 18  2015 tmp -> private/tmp
 0 drwxr-xr-x@ 12 root  wheel   408 Jan 18  2015 usr
 8 lrwxr-xr-x@  1 root  wheel    11 Jan 18  2015 var -> private/var

```

The second column corresponds to the permissions details for each file/folder. For the first line:

```bash
drwxrwxr-x+
```
We're not going to talk about the `d` letter at the start or the `+`/`@` at the end of each line for the moment. Just pay attention to the nine letters between.

The important part in this set of characters is:

```bash
rwxrwxr-x
```

This can be read:
```bash
rwx rwx r-x
```
This breaks down like this:

- first group of three letters corresponds to the owner permission
- the second group of three letters corresponds to the owner group permission
- the last group of three letters corresponds to others' permission

#### `chmod`

To modify a file's permissions, you need to use the `chmod` command.

Only the owner of a file may use chmod to alter a file's permissions.

`chmod` has the following syntax:

```bash
chmod [options] mode file(s)
```

The 'mode' part specifies the new permissions for the file(s) that follow as arguments. A mode specifies which user's permissions should be changed, and afterwards which access types should be changed. Let's say for example:

```bash
chmod a-x file.txt
```

This means that the execute bit should be cleared (-) for all users: owner, group and the rest of the world. The permissions start with a letter specifying what users should be affected by the change, and this might be any of the following:


* u the owner user
* g the owner group
* o others (neither u, nor g)
* a all users

You might have encountered things like `chmod 755 a_file.txt`.

You can change the entire permission pattern of a file in one go using one number like the one in this example. Every mode has a corresponding code number, and as we shall see, there is a very simple way to figure out what number corresponds to any mode.

Every single digit in the triplet corresponds to the level of authorization for a group (user, group and others). Every digit is the addition of the rights for this group, and every level of permission corresponds to a number:

* 4 for r.
* 2 for w.
* 1 for x.

So if a file has rwxr-xr-x permissions we do the following calculation:

* Triplet for u: rwx => 4 + 2 + 1 = *7*
* Triplet for g: r-x => 4 + 0 + 1 = *5*
* Triplet for o: r-x => 4 + 0 + 1 = *5*
Which makes : 755

So, 755 in UNIX permissions means 'I don't mind if other people read or run this file, but only I should be able to modify it' while 777 means 'everyone has full access to this file'

[Comment]: # (An example of why we need chmod is that if we write a small script we'll need to make it executable to actually run it.)

Reference: https://kb.iu.edu/d/abdb

<!-- 2:15 15 minutes -->

## Customize The terminal - Demo

#### When using bash_profile

When a terminal session starts, there are some configurations read at the start of the session. The configuration is written in a file that has a specific name. As we run `bash`, the file name for this type of shell is called `.bash_profile` and is located in the user folder, so every user for the same machine can have different configurations.

If you open the file `.bash_profile` using the command `subl ~/.bash_profile`, you'll see your own config file for bash.

You can add code to this file and it will be parsed and/or executed every time you open a new window/tab.  You can add custom commands, aliases, redefine your path etc.

One of the most important params in this file is the `$PATH` definition, let's see what this is about.

### $PATH

You’ll hear about _shell path_ (or $PATH) when working with the command line. The _shell path_ in OS X (or Linux) refers to a list of folders in the file system that contains files or executables that will be used by certain applications and programs.

The $PATH is useful because you will not need to type the absolute path of a command if the folder where this command is contained is already in the path.

When a command is typed in the terminal, a search will be performed by the OS to see if the command exists in the folders referenced by the path.

For example, the path that allows you to run the command `git` in the terminal like this:

```bash
$ git
```

Instead of having to run:

```bash
$ /usr/local/bin/git
```

The $PATH contains several absolute paths, and they are all separated by colons **:**

You can show your $PATH by typing

```bash
$ echo $PATH
```

The result should be something like:

```bash
/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin
```

The path above is actually a list of 5 different paths:

* /usr/bin
* /bin
* /usr/sbin
* /sbin
* /usr/local/bin


### Customizing the path

You can add folders in the $PATH by adding in the `.bash_profile` config file. If you open you terminal config file, you’ll see a line looking like:

```bash
export PATH="/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:~/bin:$PATH"
```

(the folders may be different in your PATH)

Let’s describe this line:

* `export PATH=""` : This tells the terminal to send the variable named PATH to the terminal sessions so that the variable is always accessible.
* `/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:~/bin` This is the list of folders that are defined in the path.
* `:$PATH` : the PATH variable can be defined in several files and by different programs, so at the end of re-defining the path, adding `:$PATH` means that all the PATH definitions made in other config files will be added to the new definition.

In this path definition, we could add a new path to a folder, for example, if we transform this path:

```bash
export PATH="/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:~/bin:$PATH"
```

...to this path:

```bash
export PATH="/a/b/c:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:~/bin:$PATH"
```

Now every new terminal session will include the commands (executable files) in the folder `/a/b/c`


The orders of the folders in the path matters. For example, in the path above, if there is one executable file called `wdi` in the folder `/a/b/c` and another one with the same name in the folder `/usr/local/bin`, then the one executed when the command `wdi` is invoked and will be the command in the folder `/a/b/c` because of the precedence in the path.

Get comfortable with your `~/.bash_profile`

[Comment]: # (export works for anything. We can use it to keep track of other variables we might need like whether something is a dev or production environment.) 

<!-- 2:30 10 minutes -->

<!-- This might be a good time to do a Command-Line Lab if there is time.  Something like 

- Make a new folder
- Change your location to that directory
- Create two blank files
- Put "hello" into one file, "goodbye" into the other
- Create a new directory called "salutations"
- Put the file with "hello" into the "salutations" folder
- Delete the file with "goodbye"
- Copy everything from the "salutations" folder into a new "greetings" folder -->

## Closing Thoughts

We will use the command line several hours every day, because it makes all file and folder manipulations easier. A lot of programs that we will use during the course also only have CLI interaction and can only be used with commands. Always remember that every action you'll do in a GUI can be done in the CLI, but the reverse is not always true.

## Resources
- Click [here](https://github.com/den-wdi-2/terminal-basics-navigating-the-filesystem/blob/master/meta_skills.md) to go to the meta-skills page. 
- Take a look at some simple keyboard shortcuts to practice: [CLI Shortcuts](https://gist.github.com/alexpchin/01caa027b825d5f98871)


## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
