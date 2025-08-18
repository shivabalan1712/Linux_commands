# 🖥️ Basic Linux Commands Questions  
**Day 1 - 23-08-2024**  
This document provides a list of 30 beginner-level Linux command questions along with easy-to-understand explanations. Use these for placement training and interview preparation.

---

## **Table of Contents**
1. [What is the Linux command to list files and directories?](#1-what-is-the-linux-command-to-list-files-and-directories)
2. [How do you change directories in Linux?](#2-how-do-you-change-directories-in-linux)
3. [What is the command to display the current working directory?](#3-what-is-the-command-to-display-the-current-working-directory)
4. [How do you create a new file in Linux?](#4-how-do-you-create-a-new-file-in-linux)
5. [How can you view the contents of a file in Linux?](#5-how-can-you-view-the-contents-of-a-file-in-linux)
6. [What is the command to copy files in Linux?](#6-what-is-the-command-to-copy-files-in-linux)
7. [How do you move or rename files in Linux?](#7-how-do-you-move-or-rename-files-in-linux)
8. [What is the Linux command to delete a file?](#8-what-is-the-linux-command-to-delete-a-file)
9. [How do you create a new directory in Linux?](#9-how-do-you-create-a-new-directory-in-linux)
10. [How can you delete a directory in Linux?](#10-how-can-you-delete-a-directory-in-linux)
11. [What is the command to display the last few lines of a file?](#11-what-is-the-command-to-display-the-last-few-lines-of-a-file)
12. [How do you display the first few lines of a file in Linux?](#12-how-do-you-display-the-first-few-lines-of-a-file-in-linux)
13. [What is the command to search for a pattern in a file?](#13-what-is-the-command-to-search-for-a-pattern-in-a-file)
14. [How can you find the current system date and time in Linux?](#14-how-can-you-find-the-current-system-date-and-time-in-linux)
15. [What is the command to display the manual page for a command?](#15-what-is-the-command-to-display-the-manual-page-for-a-command)
16. [How do you check the disk usage of directories and files in Linux?](#16-how-do-you-check-the-disk-usage-of-directories-and-files-in-linux)
17. [What is the command to display running processes?](#17-what-is-the-command-to-display-running-processes)
18. [How can you check the available disk space in Linux?](#18-how-can-you-check-the-available-disk-space-in-linux)
19. [What is the command to find your system's IP address in Linux?](#19-what-is-the-command-to-find-your-systems-ip-address-in-linux)
20. [How do you compress files using gzip in Linux?](#20-how-do-you-compress-files-using-gzip-in-linux)
21. [What is the command to extract a tar.gz archive?](#21-what-is-the-command-to-extract-a-targz-archive)
22. [How do you change file permissions in Linux?](#22-how-do-you-change-file-permissions-in-linux)
23. [What is the command to display the content of a file with line numbers?](#23-what-is-the-command-to-display-the-content-of-a-file-with-line-numbers)
24. [How can you search for a file in a directory and its subdirectories?](#24-how-can-you-search-for-a-file-in-a-directory-and-its-subdirectories)
25. [What is the command to check the memory usage in Linux?](#25-what-is-the-command-to-check-the-memory-usage-in-linux)
26. [How do you display network configuration information in Linux?](#26-how-do-you-display-network-configuration-information-in-linux)
27. [What is the command to kill a process by its process ID?](#27-what-is-the-command-to-kill-a-process-by-its-process-id)
28. [How do you view the history of commands you've executed in Linux?](#28-how-do-you-view-the-history-of-commands-youve-executed-in-linux)
29. [What is the command to switch users in Linux?](#29-what-is-the-command-to-switch-users-in-linux)
30. [How can you schedule a task to run at a specific time in Linux?](#30-how-can-you-schedule-a-task-to-run-at-a-specific-time-in-linux)

---

## **Questions and Answers**

### 1. What is the Linux command to list files and directories?
The command `ls` is used to list files and directories in the current directory.
#### syntax: ls
```bash
$ ls
Desktop  Documents  Downloads  Pictures
```

### 2. How do you change directories in Linux?
Use the `cd` command followed by the path to the directory you want to switch to.
#### syntax: cd [directory_path]

```bash
$ cd Documents/
```

### 3. What is the command to display the current working directory?
The `pwd` command prints the full path of the current working directory.
#### syntax: pwd
```bash
$ pwd
/home/user/Documents
```

### 4. How do you create a new file in Linux?
The `touch` command is used to create a new, empty file.
#### syntax: touch [filename]

```bash
$ touch example.txt
```

### 5. How can you view the contents of a file in Linux?
The `cat` command displays the contents of a file on the terminal.
#### syntax: cat [filename]

```bash
$ cat example.txt
Hello, World!
```

### 6. What is the command to copy files in Linux?
The `cp` command is used to copy files from one location to another.
#### syntax: cp [source_file] [destination]

```bash
$ cp example.txt /home/user/Documents/
```

### 7. How do you move or rename files in Linux?
The `mv` command can be used both to move a file to a different location and to rename a file.
#### syntax :mv [old_name] [new_name]

```bash
$ mv example.txt example_new.txt
```

### 8. What is the Linux command to delete a file?
The `rm` command removes or deletes a file.
#### syntax: rm [filename]

```bash
$ rm example.txt
```

### 9. How do you create a new directory in Linux?
The `mkdir` command is used to create a new directory.
#### syntax: mkdir [directory_name]

```bash
$ mkdir new_folder
```

### 10. How can you delete a directory in Linux?
Use the `rmdir` command to remove an empty directory or `rm -r` to delete a directory and its contents.
#### syntax: rmdir [directory_name]
####         rm -r [directory_name]

```bash
$ rmdir old_folder
$ rm -r old_folder_with_files
```

### 11. What is the command to display the last few lines of a file?
The `tail` command shows the last few lines of a file.
#### syntax: tail [filename]

```bash
$ tail example.txt
This is the last line.
```

### 12. How do you display the first few lines of a file in Linux?
The `head` command shows the first few lines of a file.
#### syntax: head [filename]

```bash
$ head example.txt
This is the first line.
```

### 13. What is the command to search for a pattern in a file?
The `grep` command searches for a specific pattern of text within a file.
#### syntax: grep [pattern] [filename]

```bash
$ grep "Hello" example.txt
Hello, World!
```

### 14. How can you find the current system date and time in Linux?
The `date` command displays the current date and time.
#### syntax: date

```bash
$ date
Fri Aug 23 14:55:02 IST 2024
```

### 15. What is the command to display the manual page for a command?
The `man` command shows the manual page for any command, explaining its usage.
#### syntax: man [command]

```bash
$ man ls
```

### 16. How do you check the disk usage of directories and files in Linux?
The `du` command provides information about the disk usage of files and directories.
#### syntax: du [options] [directory_name]

```bash
$ du -h /home/user
20M	/home/user/Documents
```

### 17. What is the command to display running processes?
The `ps` command shows the currently running processes.
#### syntax: ps

```bash
$ ps
PID TTY          TIME CMD
1234 pts/0    00:00:00 bash
5678 pts/0    00:00:00 ps
```

### 18. How can you check the available disk space in Linux?
The `df` command displays the available disk space on all mounted filesystems.
#### syntax: df [options]

```bash
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   20G   80G  20% /
```

### 19. What is the command to find your system's IP address in Linux?
The `ifconfig` or `ip a` commands can be used to view your system's IP address.
#### syntax: ip addr show

```bash
$ ip addr show
inet 192.168.1.2/24 brd 192.168.1.255 scope global eth0
```

### 20. How do you compress files using gzip in Linux?
The `gzip` command compresses files, reducing their size.
#### syntax: gzip [filename]

```bash
$ gzip example.txt
```

### 21. What is the command to extract a tar.gz archive?
The `tar -xzvf` command extracts files from a `.tar.gz` archive.
#### syntax: tar -xzvf [archive_name.tar.gz]

```bash
$ tar -xzvf archive.tar.gz
```

### 22. How do you change file permissions in Linux?
The `chmod` command is used to change the permissions of a file or directory.
#### syntax: chmod [permissions] [filename]

```bash
$ chmod 755 example.txt
```

### 23. What is the command to display the content of a file with line numbers?
The `nl` command displays a file's content with line numbers.
#### syntax: nl [filename]

```bash
$ nl example.txt
     1	Hello, World!
     2	This is a test file.
```

### 24. How can you search for a file in a directory and its subdirectories?
The `find` command searches for files in a directory and its subdirectories based on criteria.
#### syntax: find [directory] -name [filename]

```bash
$ find /home/user -name example.txt
/home/user/Documents/example.txt
```

### 25. What is the command to check the memory usage in Linux?
The `free` command displays the system's memory usage.
#### syntax: free -h

```bash
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          7.7Gi       2.3Gi       4.1Gi       105Mi       1.3Gi       5.1Gi
Swap:         2.0Gi          0B       2.0Gi
```

### 26. How do you display network configuration information in Linux?
The `ifconfig` or `ip addr` command shows network configuration details.
#### syntax: ifconfig

```bash
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:2B:3C:4D:5E  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
```

### 27. What is the command to kill a process by its process ID?
The `kill` command terminates a process using its process ID (PID).
#### syntax: kill [PID]

```bash
$ kill 1234
```

### 28. How do you view the history of commands you've executed in Linux?
The `history` command displays a list of previously executed commands.
#### syntax: history

```bash
$ history
1  ls
2  cd Documents/
3  pwd
```

### 29. What is the command to switch users in Linux?
The `su` command allows you to switch to another user account.
#### syntax: su [username]

```bash
$ su root
```

### 30. How can you schedule a task to run at a specific time in Linux?
The `cron` or `at` commands are used to schedule tasks to run at specified times.
#### syntax: crontab -e

```bash
$ crontab -e
# Add a job to run at 5 AM every day
0 5 * * * /path/to/script.sh
```

