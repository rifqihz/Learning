# :bookmark_tabs: Linux Basic Command Line Cheatsheet 

## :information_source: Getting Command Information 
  Knowing how to get information about a command is so important and very useful for learning how a command works.
Most command have a ```--help``` option which print a description and short message about how to run the command.
#### Format :
```bash
~$ command_name --help
```
For example if we want to know how to get information about ```$ cd``` we can use :
```bash
~$ cd --help
```


  Another way to get information about a command is by using the `$ man` command. Man or Manual page is like a `--help` command. But it give more information than `--help` gives. The information that given were :
1. Name of the command
1. Synopis about how to use the command
1. Description about the command
1. The author of the manual pages
1. Link for reporting bugs
1. Copyright of the page
1. Extra information
	
#### Format :
```bash
~$ man command_name
```
For example if we want to know get information about `ls` we can use 
```bash
~$ man ls
```
Beside that there are a command that can help you if you forget about a command but you remember a few keyword that related to the command. That command is `$ apropos`. 
#### Format :
```bash
~$ apropos key
```
For example if we want forget about command `$ whatis` and we only remember 'what',then we can use this command :
```bash
~$ apropos what
```
It'll show you the related command(s) with key 'what' and a short description of each command(s).\

And if you just want to know about the description about a command, you can use `$ whatis`. It will shows only the description of a command.
#### Format :
```bash
~$ whatis command_name
```
For example if we want to know about `ls`, then you can use this command :
```bash
~$ whatis ls
```

## Navigating the File System

### - Current Working Directory 
---
  If we working in terminal and we forget about where we are in the directory, we can use `pwd` command. This command will tell you where you are in the terminal. 
#### Format :
```bash
~$ pwd
```

If you open your terminal for the first time (and you didn't change the default directory before) and you run `$ pwd` it will show `/home/host_name`. For example if i run in my computer it will show 
```bash
~$ pwd
/home/skyfall
```

### - List Of Directory
---
  If you want to know list of file or directory in a directory you can use `$ ls`. 
#### Format :
```bash 
~$ ls
```
Tips you can add useful option in ls command,such as :
1. `$ ls -a`\
It is an option to show everything in the directory including a hidden file
1. `$ ls -l`\
It is an option to show long listing format of information about general file or folder including :
- Permission
- Owner
- Group
- Size
- Date and etc

### - Change the working directory
---
If you need to go from a directory to other directory and you will need command `$ cd`. cd is a command for changing the working directory. 
#### Format :
```bash
~$ cd
```
For example if i was in `/home` directory and i want to go to `/Downloads` directory. Between `/home` directory there are a directory called 'skyfall' . So i need to go to skyfall directory and then i go to downloads directory. Here's the implementation :
```bash
/home$ cd skyfall
~$ cd Downloads
~/Downloads$ 
```
or i can use
```bash
/home$ cd skyfall/Downloads
~/Donwloads$
```
the result will be same. It's up to you, but i suggest you if you don't know about where is your the location of your destination directory,you do it one-by-one like in the first example.

Otherwise,if you want to get back to higher directory you can use `$ cd ..`.\

## File and Directory Command
### - Create Directory
Command for make directori(es) is `$ mkdir`
#### Format :
```bash
$ mkdir dir_name
```
#### Example :
make 3 directories(ex : dir1,dir2,dir3) in single command :
```bash
$ mkdir dir1 dir2 dir3
```
### - Remove (file,directory,etc)
1. Command for remove file(s) is `$ rm`
#### Format :
```bash
$ rm file_name
```
#### Example :
Remove 2 files(ex : file1 and file2) in single command :
```bash
$ rm file1 file2
```

2. Command for remove directori(es) is `$ rmdir`. Only works for empty directory.
#### Format :
```bash
$ rmdir dir_name
```
#### Example :
Remove 2 empty directories (ex : dir1 and dir2) in single command :
```bash
$ rmdir dir1 dir2
```

3. Command for remove non-empty and empty directori(es) is `$ rm -r`.
#### Format :
```bash
$ rm -r dir_name
```
#### Example :
Remove 2 non-empty/empty directories (ex : dir1 and dir2) in single command :
```bash
$ rm -r dir1 dir2
```

4. Command for **force remove** file(s) without confirmation is `$ rm -f`
#### Format :
```bash
$ rm -f file_name
```
#### Example :
Force remove 2 files (ex : file1 and file2) without any confirmation in single command :
```bash 
$ rm -f file1 file2
```

5. Command for **force remove** directori(es) without confirmation is ` $ rm -rf`
#### Format :
```bash
$ rm -rf dir_name
```
#### Example :
Force remove 2 directories (ex : dir1 and dir2) without any confirmation in single command :
```bash
$ rm -rf dir1 dir2
```

### - Copy (file & directory)
1. Command for copy file(s) is `$ cp`.
#### Format :
```bash
$ cp file_name destination
```
#### Example :
Copying 3 file (ex : file1,file2,file3) from `/Documents` directory to `/home`.
```bash
~/Document$ cp {file1,file2,file3} ~
```
If you want to copy many file with the same prefix but different ending (ex : file1-file 10). You can do :
```bash
~/Document$ cp file{1..10} ~
```
2. Command for copy directori(es) is `$ cp -r`
#### Format :
```bash
$ cp -r dir_name destination
```
#### Example :
Copying 2 directories (ex : dir1,dir2) from `/home` directory to `/Documents`.
```bash
~$ cp dir{1,2} ~/Documents
```
### - Move and Rename 
Move and renaming file(s) or directori(es) can be done with `$ mv`
#### Format :
- Rename:
```bash
$ mv oldfile newfile
```
- moving :
```bash
$ mv file dir_name
```
#### Example :
- Rename a file (file1 to file2) :
```bash
$ mv file1 file2
```
- Rename a directory (dir1 to dir2) :
```bash
$ mv dir1 dir2
```
- move a file to directory (file 1 from ~ to /Documents) :
```bash
$ mv file1 ~/Documents
```

### - Create file or update the access or modification time
#### Format :
```bash
$ touch file_name
```
#### Example :
- Make 10 file (file1 - file10) with same prefix different ending :
```bash
$ touch file{1..10}
```
- update, we can update file/folder using this format :
```bash
$ touch existing_
```









