# :notebook_with_decorative_cover: Linux Basic Command Line Cheatsheet 

## :information_source: Getting Command Information 
  Knowing how to get information about a command is so important and very useful if we are working in the terminal.
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
For example if we want to know how to get information about `ls` we can use :
```bash
~$ man ls
```
Beside that there are a command that can help you if you forget about a command but you remember a few keyword that related to the command. The command is `$ apropos`. 
#### Format :
```bash
~$ apropos key
```
For example if we forget about command `$ whatis` and we only remember 'what', then we can use this command :
```bash
~$ apropos what
```
It'll show you the related command(s) with key 'what' and a short description of each command(s).\

And if you just want to know about the description about a command, you can use `$ whatis`. It will shows the description of a command only.
#### Format :
```bash
~$ whatis command_name
```
For example if we want to know about `ls`, then we can use this command :
```bash
~$ whatis ls
```

## :bookmark_tabs: Navigating the File System

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
If you need to go from a directory to other directory, you can use `$ cd` command. It's a command to change the working directory. 
#### Format :
```bash
~$ cd
```
For example if i was in `/home` directory and i want to go to `/Downloads` directory. Next of `/home` directory, there are a directory called 'skyfall' . So i need to go to skyfall directory and then i go to downloads directory. Here's the implementation :
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
the result will be the same. It's up to you, but i suggest you if you don't know about where is your the location of your destination directory,you do it one-by-one like in the first example.

Otherwise,if you want to go to higher directory you can use `$ cd ..` command.

## :file_folder: File and Directory Command
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
- update the modification time, we can update file/folder using this format :
```bash
$ touch existing_
```

### - View the content of the file
If you want to read the content of the file you can use `$ cat ` command.
#### Format :
``` bash
$ cat file_name
```
There are a few other options that would be useful. That is `$ cat > file_name` and `$ cat >> file_name`. This two option is used for add content of the file. The different is if you use '>' you will delete the content and rewrite it with your input. If you use '>>' your input will be added in the last of the content.

### - Browse through a file
There are two option for browse through a file. There are `$ more` and `$ less`. `$ more` is a file perusal filter for CRT viewing.`$ less` is the opposite of `$ more`.
#### Format :
More :
```bash
$ more file_name
```
Less :
```bash
$ less file_name
```

### - Display first 10 line of the file
#### Format :
```bash
$ head file_name
```

### - Display the last 10 line of the file
#### Format :
```bash
$ tail file_name
```
### - Detect file type
We can use `$ file` for detect file type using file header.
#### Format :
```bash
$ file file_name
```

### - Print all string(s)
If we want to print all string (printable) we can use ` $ strings`
#### Format :
```bash
$ strings file_name
```

## :mag: Search
### - Search a pattern in a file
We can use `$ grep` if we want to search a pattern in a file.
#### Format :
```bash
$ grep pattern file_name
```
It will show the content of the file that have the same pattern like your input pattern.

### - Search a pattern recursively in a directory
We can use `$ grep -r` if we want to search a pattern in a directory. It will search pattern in all file(s) inside the directory.
#### Format :
```bash
$ grep -r pattern dir_name
```

### - Find files and directory by name
If we don't know or forget about where is a file or a directory we can use `$ locate ` command.
#### Format :
```bash
$ locate file_or_dir_name
```

## :closed_lock_with_key: File Permission

![Linux Permission](https://1.bp.blogspot.com/-KCp0GyTq5og/WcALlG2-0NI/AAAAAAAAAM8/af0o4Z_BNvsV1Ar8MWA8_CeqS_bwKLRGACLcBGAs/s640/perms1.png)

There are 3 type of file permission (rwx) :
Permission | Description | Num
---------- | ----------- | ---
Read | Read the content | 4
Write | Change the content (add,edit,delete) | 2
Execute | Run the file/script | 1

So, if we want to change file permission we can use the sum of permission number :
Permission | Symbol | Number
---------- | ------ | ------
Read, Write, Execute | rwx | 7
Read, Write | rw- | 6
Read, Execute | r-x | 5
Read only | r-- | 4
Write, Execute | -rx | 3
Write only | -w- | 2
Execute Only | --x | 1
Nothing | --- | 0

We can change the permission using `$ chmod`
#### Format :
- Change file permission by number
```bash
$ chmod xxx file_name
```
'xxx' should be change with the sum of the number of file permission. first x is for user, second x is for group and third x is for everyone.
- Change file permission by letter (the change will be added for user,group and everyone)
```bash
$ chmod +z file_name
```
'z' should be changed with 'r' or 'w' or 'x' or both or all of them.


## :link: Source 
1. Image source : 
- http://trickster-id.blogspot.com/2017/09/File-permission-pada-linux.html
2. Content source : 
- https://www.linuxtrainingacademy.com/linux-commands-cheat-sheet/#4_8211_USER_INFORMATION_AND_MANAGEMENT
- https://github.com/joulephicar/holy-text/blob/master/linux.md











