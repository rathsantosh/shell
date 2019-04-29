1: What is a shell?

* Shell is an interface between the user and the kernel. A system can have many shell running simultaneously. So, whenever a user  enters a command through the keyboard, the shell communicates with the kernel to execute it and then display the output on the terminal (CLI) to the user.

2: What are the different types of commonly used shells on a typical Linux system?

* csh,ksh,bash,Bourne. The most commonly used and advanced shell used today is "Bash".

3: What is the equivalent of a file shortcut that we have a window on a Linux system?

* Shortcuts are created using "links" on Linux. There are two types of links that can be used namely "soft link" and "hard link".

4: What is the difference between soft and hard links?

* Soft links are link to the file name and can reside on different filesytem as well,however hard links are link to the inode of the file and have to be on the same filesytem as that of the file. Deleting the original file makes the soft link inactive (broken link) but does not affect the hard link (Hard link will still access a copy of the file)

5: How will you pass and access arguments to a script in Linux?

::

 Arguments can be passed as:
 scriptName "Arg1" "Arg2"…."Argn" and can be accessed inside the script as $1 , $2 .. $n

6: What is the significance of $#?

* $# shows the count of the arguments passed to the script.

7: What is the difference between $* and $@?

* $@ treats each quoted arguments as separate arguments but $* will consider the entire set of positional parameters as a single string.

8: Given a file, replace all occurrence of word "ABC" with "DEF" from 5th line till end in only those lines that contains word "MNO"

::

$sed –n '5,$p' file1|sed '/MNO/s/ABC/DEF/'

9: Given a file, write a command sequence to find the count of each word.

::

$tr –s  "(backslash)040" <file1|tr –s  "(backslash)011"|tr "(backslash)040 (backslash)011" "(backslash)012" | uniq –c

10: How will you find the 99th line of a file using only tail and head command?

::

$tail +99 file1|head -1

11: Print the 10th line without using tail and head command.

::

$sed –n '10p' file1

12: In my bash shell I want my prompt to be of format '$"Present working directory":"hostname"> and load a file containing a list of user-defined functions as soon as I log in, how will you automate this?

* In bash shell, we can create ".profile"  and .bashrc file which automatically gets invoked as soon as I log in and write the      following syntax into it.
 
::


 export PS1='$ `pwd`:`hostname`>' .File1

**Note:** Here File1 is the file containing the user-defined functions and "." invokes this file in current shell.

13:Explain about "s" permission bit in a file?

* "s" bit is called "set user id" (SUID) bit.

  "s" bit on a file causes the process to have the privileges of the owner of the file during the instance of the program.

  For example, executing "passwd" command to change current password causes the user to writes its new password to shadow file even though it has "root" as its owner.

14: I want to create a directory such that anyone in the group can create a file and access any person's file in it but none should be able to delete a file other than the one created by himself.

* We can create the directory giving read and execute access to everyone in the group and setting its sticky bit "t" on as follows
::


$mkdir tree
$chmod g+wx tree
$chmod +t tree

15: How can you find out how long the system has been running

* We can find this by using the command "uptime"
::

$uptime

16: How would you find out all information about a specific user like his default shell, real-life name, default directory, when and how long he has been using the system?
::
    
   $finger user1
   Login: user1			
   Name: user123
   Directory: /home/user1  	
   Shell: /bin/bash
   On since Mon Apr 29 09:17 (IST) on :0 from :0 (messages off)
   No mail.
   No Plan.

17: What is the difference between $$ and $!?
 
* $$ gives the process id of the currently executing process whereas $! Shows the process id of the process that recently went into the background.

18: What are zombie processes?

* These are the processes which have died but whose exit status is still not picked by the parent process. These processes even if not functional or running still have its process id entry in the process table.

19: I want to monitor a continuously updating log file, what command can be used to most efficiently achieve this?

* We can use tail –f filename. This will cause only the default last 10 lines to be displayed on std I/O which continuously shows the updating part of the file.

20: Write a script to print the first 10 elements of Fibonacci series.

:: 
  
  #!/bin/sh
  a=1
  b=1
  echo $a
  echo $b
  for I in 1 2 3 4 5 6 7 8
  do
  c=a
  b=$a
  b=$(($a+$c))
  echo $b
  done

21: What is the difference between grep and egrep?

* egrep is Extended grep that supports added grep features like "+" (1 or more occurrence of a previous character),"?"(0 or 1 occurrence of a previous character) and "|" (alternate matching)

22: How to set an array in Linux?

::


 In bash
 A=(element1 element2 element3 …. elementn)

23: Write a for loop script

::

 #!/bin/bash
 for i in 1 2 3 4 5
 do
 echo "Welcome $i times"
 done

24: How do we delete all blank lines in a file?

::

$sed  '^ [(backslash)011(backslash)040]*$/d' text1

**Note:** where (backslash)011 is an octal equivalent of space and
          (backslash)040 is an octal equivalent of the tab

25: How will I insert a line "ABCDEF" at every 100th line of a file?

* $sed '100i\ABCDEF' file1

26: What are the four fundamental components of every file system on Linux?

* Bootblock, super block, inode block and Datablock are found fundamental components of every file system on Linux.

27: What is a boot block?

* This block contains a small program called "Master Boot record"(MBR) which loads the kernel during system boot up.

28: What is a super block?

* Super block contains all the information about the file system like the size of file system, block size used by its number of free data blocks and list of free inodes and data blocks.

29: What is an inode block?
 
* This block contains the inode for every file of the file system along with all the file attributes except its name.

30: What is the use of a shebang line?

* Shebang line at the top of each script determines interpreter of bash which is to be used to execute the script.

31: Describe the root account.

* The root account is like a systems administrator account and allows you full control of the system. Here you can create and maintain  user accounts, assigning different permissions for each account. It is the default account every time you install Linux.


























