# :bookmark_tabs: Linux Basic Command Line Cheatsheet 

## :information_source: Getting Command Information 
  Knowing how to get information about a command is so important and very useful for learning how a command works.
Most command have a ```--help``` option which print a description and short message about how to run the command.
#### Format :
```bash
$ command_name --help
```
For example if we want to know how to get information about ```$ cd``` we can use :
```bash
$ cd --help
```


  Another way to get information about a command is by using the `$ man` command. Man or Manual page is like a `--help` command. But it give more information than `--help` gives. The `$ man` show :
1. Name of the command
1. Synopis about how to use the command
1. Description about the command
1. The author of the manual pages
1. Link for reporting bugs
1. Copyright of the page
1. Extra information
	
#### Format :
```bash
$ man command_name
```
For example if we want to know how to get information about `ls` we can use 
```bash
$ man ls
```

## Navigating the File System

#### Current Working Directory 
  If we working in terminal and we forget about where we are in the directory, we can use `pwd` command. This command will tell you where you are in the terminal. 
#### Format :
```bash
$ pwd
```

If you open your terminal for the first time (and you didn't change the default directory before) and you run `$ pwd` it will show `/home/host_name`. For example if i run in my computer it will show 
```bash
$ pwd
/home/skyfall
```







