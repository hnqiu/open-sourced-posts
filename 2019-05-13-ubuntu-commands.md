---
title:  "An Archive of My Frequent Ubuntu Commands"
date: 2019-05-13
last_modified_at: 2019-05-13
categories:
  - cheatsheets
---

>:exclamation: Please note this cheatsheet is from personal experience and other online resources. It should not be considered as an official guide.

## Basic Commands
```sh
# look around
cd 
ls -atlh 
ls -d */ # list directories only
echo *
less -N [file] # display file with line numbers 
ls | less

which
whereis
man
intro

grep # often used with other commands
printenv # or `env`
env | grep "Keyword"
ps -a | grep "Keyword"  #process status

nautilus [path] # open file manager of a directory from terminal
nautilus -q # quit nautilus
```

```sh
# manipulate files
cp -i [file] [dest_dir] # interactive: prompt before overwrite
cp -r [dir] [dest_dir] # copy a directory
rm -r ./* # remove all within current directory
mv [file] [dest_dir]
mkdir -p [parent/dir]
# rmdir

touch [newFile]
ln -s [file] [symbolic] #symbolic link
```

```sh
# apt
sudo apt-get update # update the package lists
sudo apt-get upgrade # fetch new versions of packages on the list
sudo apt-get install <package>
```

```sh
# permissions
chmod -rw+x [file]
chmod 755 [file]
# u: user | g: group | o: others
chmod -R o-w [folder]

sudo chown -R <user>:<group> [folder]
sudo chown <user>:<group> [file]
```

## More Advanced Commands
```sh
# tee
tee [option] [file] ... # redirect output to files and/or to standard outputs
# example
ps -ax | tee -a process.txt | grep "foo" # a: append
```

```sh
# editing files in terminal 
echo "some text" >> [file] # append what's inside quotes to file

# double quote (") and single quote (') have different level of expansions
# single quote will NOT interprete anything
# double quotes will, unless with backslash (\) to escape
echo '$PATH'
echo "$PATH"
echo "\$PATH"
# results will be
$PATH
/usr/bin:#etc
$PATH
```

```sh
# find and execute

# find a file that contains "Keyword" in the home directory (including subdirs)
find ~/ -type f -name "*Keyword*"

# find a file/dir in the current directory (maxdepth==1 means only the current dir)
# and pass the results to the command following "-exec" , then end with "{} +"
find . -type f -name "*Keyword*" -maxdepth 1 -exec ls -lh {} +
find . -type d -exec chmod 775 {} +

find . -perm 775 # find all under current dir that have 775 permission
```

## Use Terminal to Open Files
```sh
gedit [file_name] & disown # Open gedit without unresponsive terminal

# or
gedit [file_name]
# then use Ctrl+Z to stop it, and use
bg # background
# finally use
disown

jobs # show current running programs
```

## Seldom Used Commands
```sh
# compress and extract
tar -czvf [archive.tar.gz] [dir_to_compress] # c: compress; f: file, must be the last flag
tar -xzvf [archive.tar.gz] [dir_to_extract] # x: extract; z: gzip
tar -xvf [archive.tar.xz] [dir_to_extract] # x: extract
unzip [file.zip] -d [dest_folder]
zip -r [file] [folder]
# gzip & gunzip
```

```sh
# others
sudo shutdown now
sudo reboot

sudo su
exit
```
