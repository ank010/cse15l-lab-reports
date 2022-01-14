## Welcome to Lab 1

### [Home](https://ank010.github.io/cse15l-lab-reports/index.html)

### Setting up Server Access
This lab is a step-by-step tutorial on how to log into a course-specific account on ieng6.

### Step 1: Installing VScode
In order to access the online server, ieng6, we need to go through a terminal. VScode, an IDE, will provide that terminal. If not already downloaded, got to [https://code.visualstudio.com/](https://code.visualstudio.com/) and follow their instructions in donwloading it onto your computer. 

Once it is downloaded, open it up and it should look something like this:
![screenshot](VSCshot.jpg)

### Step 2: Remotely Connecting
Now we will log in to the remote server through the terminal in VScode. First, you have to find the course-specific username through this link: [Course Specific ID](https://sdacs.ucsd.edu/~icc/index.php). Remember to reset the password for the account if you haven't done so already.

Next, open up the terminal in VScode (View --> Terminal) and enter in your course-specific ID as shown below, with the ssh:
![screenshot](TerminalLog.jpg)
You will get a message asking if you want to connect, enter 'y' to continue. After entering your password, you  will see something like this in your terminal:
![screenshot](LogginPic.jpg)
Once you get here, you have successfully logged in to the remote server!

## Using Some Commands
Now that we are in the server, we can try some commands that are commonly used when navigating around. 
Here is a list of commands:
- cd ~
- cd
- ls -lat
- ls -a
- ls <directory> where <directory> is /home/linux/ieng6/[username]
- cp /home/linux/ieng6/cs15lwi22/public/hello.txt ~/

This is what it looks like running some of them:
![screenshot](commands.jpg)

## Copying Files From Local to the Server
Now that we will work on moving files from local computer to the online server using the 'scp' command. 
First log out of the ieng6 by simply typing in exit to the command line
Now, create a file on your computer, give a default constructor + any print statements
Next, open the terminal (make sure the directory is correct) and enter the following:
![screenshot](scpPic1.jpg)


