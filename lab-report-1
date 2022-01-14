# Lab 1: Remote Access and the Filesystem
## Step 1: Installing VSCode <br />
I already had VSCode downloaded becasue I took CSE11 last quarter, which required VSCode.
![Image](im1.png) 
&nbsp;


## Step 2: Remotely Connecting <br />
I first downloaded OpenSSH (a program which can connect computers).  I then used the "ssh username@servername" command to connect my client with the server (a computer in the CSE basement).
![Image](im2.png)
&nbsp;

## Step 3: Trying Some Commands <br />
I ran the commands "cd", "ls", "pwd", "mkdir", and "cp" in both the server and client.  I also tried modifications of these commands such as "ls -a" (lists all directories including hidden ones) and "cd ~" (exits one directory).  When attempting to run the command "cp /home/linux/ieng6/cs15lwi22/public/hello.txt ~/" in my client, I received in error that stated that it couldn;t rea the file because permission was denied.
![Image](im31.png)
![Image](im32.png)
&nbsp;

## Step 4: Moving Files with scp <br />
I used the scp command to move a file called WhereAmI.java (which prints out the name of the operating system and user in which the file is located) from my client to my server. I then logged into my server and used ls to ensure WhereAmI.java was succesfully moved to the server.  I then ran the file on the server and made sure it printed out the name of the server's operating system, not the client's.
![Image](im4.png) 
&nbsp;

## Step 5: Setting an SSH Key <br />
I first used a program called ssh-keygen which creates two files, with one being a public key and th other being a private key. I then copied my public key to the server. After this, I was able to use the ssh command to get into the server without having to enter my passowrd.  This saved me about 9 seconds when running WhereAmI.java 
![Image](im5.png) 
&nbsp;


## Step 6: Optimizing Remote Running <br />
In order to decrease the time remote running takes, I ran multiple commands on the same line by seperating each command with smeicolon. I also put commands in quaotes after a ssh command in order to immediately exit the remote server after the command in the quotes is run
![Image](im6.png) 
