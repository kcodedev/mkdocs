# File and Directory Management

## ls
List directory contents.

- `ls` : List files and directories
- `ls -l` : Long listing format with permissions, size, etc.
- `ls -a` : Show hidden files (starting with .)
- `ls -h` : Human-readable file sizes

## cd
Change directory.

- `cd /path/to/directory` : Change to specific directory
- `cd ..` : Go up one directory
- `cd ~` : Go to home directory

## mkdir
Make directory.

- `mkdir newdir` : Create a new directory
- `mkdir -p path/to/newdir` : Create nested directories

## rm
Remove files or directories.

- `rm file.txt` : Remove a file
- `rm -r directory` : Remove a directory and its contents
- `rm -f file.txt` : Force remove without confirmation

## cp
Copy files or directories.

- `cp source.txt destination.txt` : Copy file
- `cp -r sourcedir destdir` : Copy directory recursively

## mv
Move or rename files or directories.

- `mv oldname.txt newname.txt` : Rename file
- `mv file.txt /path/to/dest/` : Move file to directory

## touch
Create empty file or update timestamp.

- `touch newfile.txt` : Create empty file

## find
Search for files.

- `find /path -name "*.txt"` : Find files by name