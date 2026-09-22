# Filesystem Navigation

##Objective

The objective of this lab was to practice navigating and managing the Linux filesystem using command-line tools.

##The lab focused on:

-Creating directory structures
-Creating files
-Finding files by name and extension
-Finding files based on modification time
-Viewing directory structures
-Using locate to search for files
-Understanding the difference between find and locate

##Environment
Operating System: CentOS 9
Virtualization: VMware Workstation
Shell: Bash

###Task 1 — Create a Four-Level Directory Structure

I created a four-level project directory structure using a single mkdir -p command.

Example:

mkdir -p  filesystem-navigation/project/src/module/auth project/docs project/tests
Why mkdir -p?

The -p option allows Linux to create parent directories automatically when they do not already exist.

This is useful when creating several levels of directories at once.

###Verification
tree ~/filesystem-navigation/project

##Task 2 — Create Mixed-Extension Files

I created multiple empty files with different extensions.

Example:

touch file1.txt file2.log file3.conf file4.txt file5.log

The touch command can create an empty file if the file does not already exist.

###Verification
ls -l

##Task 3 — Find All .log Files

I used find to locate all files ending in .log.

find ~/filesystem-navigation -type f -name "*.log"

###Explanation
find — searches the filesystem
 — starting location
-type f — search only regular files
find ~/filesystem-navigation -name "*.log" — match files ending in .log

The quotation marks prevent the shell from expanding the wildcard before find receives it.

Task 4 — Find Recently Modified Files

I used find to locate files modified within the required time period.

Example:

find ~/filesystem-navigation -type f -mmin -60

###Explanation

-mmin -60 means:

Find files whose modification time is less than 60 minutes ago.

This is useful for identifying recently changed files during troubleshooting.

##Task 5 — Generate a Directory Map

I used tree to display the directory hierarchy.

tree ~/filesystem-navigation > structure.txt

The > operator redirected the output of tree into a file.

###Verification
cat structure.txt

This produced a text representation of the directory structure.

##Task 6 — Use locate

I updated the locate database:

sudo updatedb

Then searched for files:

locate "*.log"


#Project structure

filesystem-navigation
    ├── Project
    │   ├── docs
    │   │   ├── config.conf
    │   │   ├── docs.log
    │   │   ├── readme.txt
    │   │   └── script.sh
    │   ├── src
    │   │   ├── app.log
    │   │   ├── app.txt
    │   │   ├── auth
    │   │   │   ├── auth.conf
    │   │   │   ├── auth.log
    │   │   │   ├── auth.sh
    │   │   │   ├── auth.txt
    │   │   │   └── modules
    │   │   │       ├── mod.conf
    │   │   │       ├── mod.log
    │   │   │       ├── mod.sh
    │   │   │       └── mod.txt
    │   │   ├── config.conf
    │   │   └── script.sh
    │   └── tests
    │       ├── test.conf
    │       ├── test.log
    │       ├── test.sh
    │       └── test.txt
    ├── README.md
    ├── reference.txt
    └── structure.txt


##find vs locate
  ` find                                          	locate`
Searches the filesystem directly	Searches a pre-built database
Can search using many conditions	Primarily searches filenames/paths
Results reflect the current filesystem	Database can become outdated
Useful for precise searches      	Usually very fast

##Important lesson

locate may not immediately find a newly created file because its database needs to be updated.

##Skills Practiced
-Linux filesystem navigation
-Directory creation
-File creation
-find
-locate
-updatedb
-tree
-Output redirection
-Wildcards
-File modification-time searches

##Key Commands
-mkdir -p
-touch
-find
-tree
-updatedb
-locate
-cat

##What I Learned

This lab strengthened my ability to navigate and search the Linux filesystem from the command line. I also learned when to use find versus locate and how output redirection can be used to save command results to a file.

