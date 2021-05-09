# Linux系统概述

TODO:

grep command in Unix/Linux - GeeksforGeeks
https://www.geeksforgeeks.org/grep-command-in-unixlinux/
The grep filter searches a file for a particular pattern of characters, and displays all lines that contain that pattern. The pattern that is searched in the file is referred to as the regular expression (grep stands for globally search for regular expression and print out). 

grep(1) - Linux manual page
https://man7.org/linux/man-pages/man1/grep.1.html
       grep, egrep, fgrep - print lines that match patterns


sed, a stream editor
https://www.gnu.org/software/sed/manual/sed.html
sed is a stream editor. A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline). While in some ways similar to an editor which permits scripted edits (such as ed), sed works by making only one pass over the input(s), and is consequently more efficient. But it is sed’s ability to filter text in a pipeline which particularly distinguishes it from other types of editors.

Sed Command in Linux/Unix with examples - GeeksforGeeks
https://www.geeksforgeeks.org/sed-command-in-linux-unix-with-examples/
SED command in UNIX is stands for stream editor and it can perform lot’s of function on file like, searching, find and replace, insertion or deletion. Though most common use of SED command in UNIX is for substitution or for find and replace. By using SED you can edit files even without opening it, which is much quicker way to find and replace something in file, than first opening that file in VI Editor and then changing it.

SED is a powerful text stream editor. Can do insertion, deletion, search and replace(substitution).
SED command in unix supports regular expression which allows it perform complex pattern matching.


Viewing text files on Linux - cat, head, tail, more and less · 2buntu
https://2buntu.com/articles/1491/viewing-text-files-on-linux-cat-head-tail-more-and-less/

Short version
head <filename>- View the top few lines of a file
-<lines> - Displays the first <lines> number of lines of a file
tail <filename> - View the bottom few lines of a file
-<lines> - Displays the last <lines> number of lines of a file
-f : continually watch for any additions at the end of the file
-f --pid=PID - continually display any additions until process with PID terminates
-f -s <sec> - continually display any additions at intervals of <sec> seconds
cat <filename> - View the whole file
-n : line-numbered output
-b : line-numbered output with no line numbers for blank lines
-s : multiple blank lines compressed into a single blank line
more <filename> - View the whole file, one screenful at a time.
spacebar : View next screen
b : View previous screen
d : View next half-screen
Enter : View next line
= : Current line number in file
v : Start vi editor on current line
/string : Search for string in file
n : Go to next occurrence of string
' : Go to first occurrence of string
less <filename>- Same as more, but with many more features. Displays the portion of the file without waiting for the entire file to be read by it. Accepts most of the more commands.
Pg Dn : View next screen
Pg Up : View previous screen
Up arrow : View previus line
Down arrow : View next line

Manage Files Effectively using head, tail and cat Commands in Linux
https://www.tecmint.com/view-contents-of-file-in-linux/

14 tail and head commands in Linux/Unix - Linux.com
https://www.linux.com/training-tutorials/14-tail-and-head-commands-linuxunix/

tail(1) - Linux manual page
https://man7.org/linux/man-pages/man1/tail.1.html
       tail - output the last part of files


head(1) - Linux manual page
https://man7.org/linux/man-pages/man1/head.1.html

       head - output the first part of files


The head and tail commands in LINUX | Baeldung on Linux
https://www.baeldung.com/linux/head-tail-commands

Coreutils - GNU core utilities
https://www.gnu.org/software/coreutils/
Coreutils - GNU core utilities
The GNU Core Utilities are the basic file, shell and text manipulation utilities of the GNU operating system. These are the core utilities which are expected to exist on every operating system.



2 Common options
https://www.gnu.org/software/coreutils/manual/coreutils.html#toc-Common-options-1

‘--help’
Print a usage message listing all available options, then exit successfully.

‘--version’
Print the version number, then exit successfully.

‘--’
Delimit the option list. Later arguments, if any, are treated as operands even if they begin with ‘-’. For example, ‘sort -- -r’ reads from the file named -r.



‘-S suffix’
‘--suffix=suffix’
Append suffix to each backup file made with -b. If this option is not specified, the value of the SIMPLE_BACKUP_SUFFIX environment variable is used. And if SIMPLE_BACKUP_SUFFIX is not set, the default is ‘~’, just as in Emacs.


GNU Coreutils
https://www.gnu.org/software/coreutils/manual/coreutils.html#toc-Introduction-1


27.2 Symbolic Modes
https://www.gnu.org/software/coreutils/manual/coreutils.html#Symbolic-Modes

Symbolic modes represent changes to files’ mode bits as operations on single-character symbols. They allow you to modify either all or selected parts of files’ mode bits, optionally based on their previous values, and perhaps on the current umask as well (see Umask and Protection).

The format of symbolic modes is:

[ugoa…][-+=]perms…[,…]
where perms is either zero or more letters from the set ‘rwxXst’, or a single letter from the set ‘ugo’.

27.2.1 Setting Permissions

users operation permissions

u
the user who owns the file;

g
other users who are in the file’s group;

o
all other users;

a
all users; the same as ‘ugo’.

The operation part tells how to change the affected users’ access to the file, and is one of the following symbols:

+
to add the permissions to whatever permissions the users already have for the file;

-
to remove the permissions from whatever permissions the users already have for the file;

=
to make the permissions the only permissions that the users have for the file.

The permissions part tells what kind of access to the file should be changed; it is normally zero or more of the following letters. As with the users part, the order does not matter when more than one letter is given. Omitting the permissions part is useful only with the ‘=’ operation, where it gives the specified users no access at all to the file.

r
the permission the users have to read the file;

w
the permission the users have to write to the file;

x
the permission the users have to execute the file, or search it if it is a directory.

For example, to give everyone permission to read and write a regular file, but not to execute it, use:

a=rw
To remove write permission for all users other than the file’s owner, use:

go-w
The above command does not affect the access that the owner of the file has to it, nor does it affect whether other users can read or execute the file.

To give everyone except a file’s owner no permission to do anything with that file, use the mode below. Other users could still remove the file, if they have write permission on the directory it is in.

go=
Another way to specify the same thing is:

og-rwx


The head and tail commands in LINUX | Baeldung on Linux
https://www.baeldung.com/linux/head-tail-commands

Coreutils - GNU core utilities
https://www.gnu.org/software/coreutils/
GNU coreutils - Core GNU utilities - GNU Project - Free Software Foundation
https://www.gnu.org/software/coreutils/manual/
->
所有的GNU的core util命令：
https://www.gnu.org/software/coreutils/manual/coreutils.html#toc-Introduction-1

```bash
3 Output of entire files
3.1 cat: Concatenate and write files
3.2 tac: Concatenate and write files in reverse
3.3 nl: Number lines and write files
3.4 od: Write files in octal or other formats
3.5 base32: Transform data into printable data
3.6 base64: Transform data into printable data
3.7 basenc: Transform data into printable data
4 Formatting file contents
4.1 fmt: Reformat paragraph text
4.2 pr: Paginate or columnate files for printing
4.3 fold: Wrap input lines to fit in specified width
5 Output of parts of files
5.1 head: Output the first part of files
5.2 tail: Output the last part of files
5.3 split: Split a file into pieces.
5.4 csplit: Split a file into context-determined pieces
6 Summarizing files
6.1 wc: Print newline, word, and byte counts
6.2 sum: Print checksum and block counts
6.3 cksum: Print CRC checksum and byte counts
6.4 b2sum: Print or check BLAKE2 digests
6.5 md5sum: Print or check MD5 digests
6.6 sha1sum: Print or check SHA-1 digests
6.7 sha2 utilities: Print or check SHA-2 digests
7 Operating on sorted files
7.1 sort: Sort text files
7.2 shuf: Shuffling text
7.3 uniq: Uniquify files
7.4 comm: Compare two sorted files line by line
7.5 ptx: Produce permuted indexes
7.5.1 General options
7.5.2 Charset selection
7.5.3 Word selection and input processing
7.5.4 Output formatting
7.5.5 The GNU extensions to ptx
7.6 tsort: Topological sort
7.6.1 tsort: Background
8 Operating on fields
8.1 cut: Print selected parts of lines
8.2 paste: Merge lines of files
8.3 join: Join lines on a common field
8.3.1 General options
8.3.2 Pre-sorting
8.3.3 Working with fields
8.3.4 Controlling join’s field matching
8.3.5 Header lines
8.3.6 Union, Intersection and Difference of files
9 Operating on characters
9.1 tr: Translate, squeeze, and/or delete characters
9.1.1 Specifying sets of characters
9.1.2 Translating
9.1.3 Squeezing repeats and deleting
9.2 expand: Convert tabs to spaces
9.3 unexpand: Convert spaces to tabs
10 Directory listing
10.1 ls: List directory contents
10.1.1 Which files are listed
10.1.2 What information is listed
10.1.3 Sorting the output
10.1.4 General output formatting
10.1.5 Formatting file timestamps
10.1.6 Formatting the file names
10.2 dir: Briefly list directory contents
10.3 vdir: Verbosely list directory contents
10.4 dircolors: Color setup for ls
11 Basic operations
11.1 cp: Copy files and directories
11.2 dd: Convert and copy a file
11.3 install: Copy files and set attributes
11.4 mv: Move (rename) files
11.5 rm: Remove files or directories
11.6 shred: Remove files more securely
12 Special file types
12.1 link: Make a hard link via the link syscall
12.2 ln: Make links between files
12.3 mkdir: Make directories
12.4 mkfifo: Make FIFOs (named pipes)
12.5 mknod: Make block or character special files
12.6 readlink: Print value of a symlink or canonical file name
12.7 rmdir: Remove empty directories
12.8 unlink: Remove files via the unlink syscall
13 Changing file attributes
13.1 chown: Change file owner and group
13.2 chgrp: Change group ownership
13.3 chmod: Change access permissions
13.4 touch: Change file timestamps
14 Disk usage
14.1 df: Report file system disk space usage
14.2 du: Estimate file space usage
14.3 stat: Report file or file system status
14.4 sync: Synchronize cached writes to persistent storage
14.5 truncate: Shrink or extend the size of a file
15 Printing text
15.1 echo: Print a line of text
15.2 printf: Format and print data
15.3 yes: Print a string until interrupted
16 Conditions
16.1 false: Do nothing, unsuccessfully
16.2 true: Do nothing, successfully
16.3 test: Check file types and compare values
16.3.1 File type tests
16.3.2 Access permission tests
16.3.3 File characteristic tests
16.3.4 String tests
16.3.5 Numeric tests
16.3.6 Connectives for test
16.4 expr: Evaluate expressions
16.4.1 String expressions
16.4.2 Numeric expressions
16.4.3 Relations for expr
16.4.4 Examples of using expr
17 Redirection
17.1 tee: Redirect output to multiple files or processes
18 File name manipulation
18.1 basename: Strip directory and suffix from a file name
18.2 dirname: Strip last file name component
18.3 pathchk: Check file name validity and portability
18.4 mktemp: Create temporary file or directory
18.5 realpath: Print the resolved file name.
18.5.1 Realpath usage examples
19 Working context
19.1 pwd: Print working directory
19.2 stty: Print or change terminal characteristics
19.2.1 Control settings
19.2.2 Input settings
19.2.3 Output settings
19.2.4 Local settings
19.2.5 Combination settings
19.2.6 Special characters
19.2.7 Special settings
19.3 printenv: Print all or some environment variables
19.4 tty: Print file name of terminal on standard input
20 User information
20.1 id: Print user identity
20.2 logname: Print current login name
20.3 whoami: Print effective user ID
20.4 groups: Print group names a user is in
20.5 users: Print login names of users currently logged in
20.6 who: Print who is currently logged in
21 System context
21.1 date: Print or set system date and time
21.1.1 Time conversion specifiers
21.1.2 Date conversion specifiers
21.1.3 Literal conversion specifiers
21.1.4 Padding and other flags
21.1.5 Setting the time
21.1.6 Options for date
21.1.7 Examples of date
21.2 arch: Print machine hardware name
21.3 nproc: Print the number of available processors
21.4 uname: Print system information
21.5 hostname: Print or set system name
21.6 hostid: Print numeric host identifier
21.7 uptime: Print system uptime and load
22 SELinux context
22.1 chcon: Change SELinux context of file
22.2 runcon: Run a command in specified SELinux context
23 Modified command invocation
23.1 chroot: Run a command with a different root directory
23.2 env: Run a command in a modified environment
23.2.1 General options
23.2.2 -S/--split-string usage in scripts
Testing and troubleshooting
23.2.3 -S/--split-string syntax
Splitting arguments by whitespace
Escape sequences
Comments
Environment variable expansion
23.3 nice: Run a command with modified niceness
23.4 nohup: Run a command immune to hangups
23.5 stdbuf: Run a command with modified I/O stream buffering
23.6 timeout: Run a command with a time limit
24 Process control
24.1 kill: Send a signal to processes
25 Delaying
25.1 sleep: Delay for a specified time
26 Numeric operations
26.1 factor: Print prime factors
26.2 numfmt: Reformat numbers
26.2.1 General options
26.2.2 Possible units:
26.2.3 Examples of using numfmt
26.3 seq: Print numeric sequences
```

TODO：整理出 常用的命令，
不常用的，就暂时不整理了。





cron - Wikipedia
https://en.wikipedia.org/wiki/Cron

Cron - 维基百科，自由的百科全书
https://zh.wikipedia.org/wiki/Cron

Linux Shell Commands
https://docs.cs.cf.ac.uk/notes/linux-shell-commands/



rsync - Wikipedia
https://en.wikipedia.org/wiki/Rsync

Use
Similar to cp, rcp and scp, rsync requires the specification of a source and of a destination, of which at least one must be local.[19]

Generic syntax:

rsync [OPTION] … SRC … [USER@]HOST:DEST
rsync [OPTION] … [USER@]HOST:SRC [DEST]

rsync(1) - Linux man page
https://linux.die.net/man/1/rsync
rsync -- a fast, versatile, remote (and local) file-copying tool

Rsync (Remote Sync): 20 Helpful Examples in Linux
https://phoenixnap.com/kb/rsync-command-linux-examples
