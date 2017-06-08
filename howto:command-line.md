# Command Line
> "Any fool can use a computer. Many do." - Ted Nelson
## Introduction
  * **echo**
      * A built in command that writes its arguments to the standard output.
  * **mkdir**
      * Used to make a new directory.
      * Usage: `mkdir <directory_name>`
  * **cd**
      * Used to change the directory in which the user is currently working.
      * Usage: `cd <directory>`
      * Usage: `cd ..` (Moves back up one directory)
  * **touch**
      * Used to create new files.
      * Usage: `touch <file_name>` 
 * **ls**
      * Lists the files in the current working directory.
 * **mv**
      * Used to rename and move files or directories.
      * Usage: `mv <source> <target>` (Moves the source file to the target)
      * Ex: `mv cat.txt dog.txt` (Renames `cat.txt` to `dog.txt`) 
  * **nano**
      * A simple text editor for the commmand line. 
      * May require sudo access to edit administrative files.
      * Usage: `nano <target_file>`
  * **cat** 
      * Displays the file to the standard output.
      * Usage: `cat <target_file>` 
  * **rm**
      * Used to delete files and directories
      * Usage: `rm <target_file>` (Deletes the target file)
      * Directories need a special flag attatched onto the command for recursive deletion due to the way directories behave. `rm -r <target_directory>`
  * **man**
      * Used to format and display the man pages, a user manual that describes how to use a certain command.
      * Usage: `man <command_name>`
## Advanced
  * **sudo**
      * Used to elevate a command.
      * Some commands are restricted by default to protect your computer, so you need to elevate the command to be able to use it.
      * `sudo <command> ...`
  * **chmod** 
      * Used to change the access permissions to objects in the file system.
      * Usage: `chmod <permissions> <target>`
  * **chown**
      * Used to change the owner of a group of objects in the file system.
      * Usage: `chown <new_owner> <object1> >object2> ...`
  * **ifconfig** 
      * Used for network interface configuration.
  * **find** 
      * Searches for files in a directory hierarchy.
  * **passwd** 
      * Changes the user's password. May require sudo access.
      * Usage: `passwd <user>`
  * **grep**
      * Searches the input file for lines containing a match to the given pattern.
      * Usage: `grep <pattern> <target_file>`

[![asciicast](https://asciinema.org/a/3zjlti1gepjl02opkg5t3gt92.png)](https://asciinema.org/a/3zjlti1gepjl02opkg5t3gt92)
