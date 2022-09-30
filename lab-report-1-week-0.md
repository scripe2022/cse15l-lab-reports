# Lab 1: Remote Access and the Filesystem

## 1. Installing VScode
This step is very simple, go to the official website to download the corresponding version of the operating system. VS Code is a powerful IDE, and almost any function can be customized. A little trick is to click on the bottom left corner of vs code to display the terminal, which works great on Windows systems!
[https://code.visualstudio.com/](https://code.visualstudio.com/)
![](https://scripe2022.github.io/cse15l-lab-reports/src/yuhang_lab1_0.png)

## 2. Remotely Connecting
To connect remotely, we must first have a remote server. The course provides us with a server: ieng6.ucsd.edu, query the username here: [https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php)
The username format of CSE15L students in fall 2022 is: cs15lfa22xx, the last two are different for each student.
Before logging in to the ieng6 server for the first time, you need to change the password first. You may encounter a lot of trouble here, make a request to ITS and they will help you.
### ssh
The word ssh can be ambiguous because it represents both a protocol and a client program.
ssh mentioned in the course is a general term for the protocol and client program, the client program ssh has many optional parameters, such as -l to specify the login user, etc., but the easiest way to use it is:
`ssh USER@ADDRESS`
In the example of the ieng6 server, the login command is:
`ssh cs15lfa22jp@ieng6.ucsd.edu`
Then enter the password:
![](https://scripe2022.github.io/cse15l-lab-reports/src/yuhang_lab1_1.png)
To return to localhost, type exit or press Ctrl-d

## 3. Trying Some Commands
There are many useful commands under linux, the following are the most commonly used:
`ls` - list directory contents
`cd` - change the working directory
`mv` - move (rename) files
`cp` - copy files and directories
`rm` - remove files or directories
`mkdir` - make directories
Usage of these commands:
![](https://scripe2022.github.io/cse15l-lab-reports/src/yuhang_lab1_2.png)
Under Linux, `/` represents the root directory, and `~` represents the Home directory (ie, the user directory), `./` refers to the current directory, `../` refers to the previous directory.

## 4. Moving Files with scp
scp is a command to transfer files between servers. Similar to the cp command, scp can also use most of the optional parameters of the cp command, such as -r to transfer the directory.
For example, if you want to transfer WhereAmI.java in the local ~/Desktop/ directory to the ~/ directory of the server, the command is:
`scp ~/Desktop/WhereAmI.java cs15lfa22jp@ieng6.ucsd.edu:~/`
![](https://scripe2022.github.io/cse15l-lab-reports/src/yuhang_lab1_3.png)
Like cp, scp also overwrites files!
![](https://scripe2022.github.io/cse15l-lab-reports/src/yuhang_lab1_4.png)

## 5. Setting an SSH Key
ssh can do passwordless login via key.
Asymmetric encryption uses an algorithm to generate a pair of keys, including a public key and a private key. Encryption with one key can be decrypted with the other key. When in use, the party generating the key keeps the private key and makes the public key public, and any ciphertext encrypted using the public key can be decrypted by its own private key.
A key pair can be generated via the `ssh-keygen` command:
![](https://scripe2022.github.io/cse15l-lab-reports/src/yuhang_lab1_5.png)

If no path is specified, the generated key pair will be saved in the ~/.ssh/ directory.
The usage of ssh-add is described in the lab1 guide, but this seems to be the command of the openssh client, which I use in the lab. I would like to introduce a more general approach:
`~/.ssh/authrized_keys` stores the public keys of all authorized key pairs, just add the local public key to the server's authrized_keys. If the server does not have this file or the ~/.ssh/ directory, you need to create them.
![](https://scripe2022.github.io/cse15l-lab-reports/src/yuhang_lab1_6.png)

## 6. Optimizing Remote Running
If you want to manage multiple servers, for example, you want to view the log of each server, or execute a script on each server, then remote running is very useful:  
![](https://scripe2022.github.io/cse15l-lab-reports/src/yuhang_lab1_7.png)

Although the ssh connection is still required, there is no need to wait for a successful login before entering the command.