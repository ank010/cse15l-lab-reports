## Welcome to Lab 2

### [Home](https://ank010.github.io/cse15l-lab-reports/index.html)

### Copy whole directories with scp -r

The command scp -r copies the whole root directory rather than just a single file as scp does. 

Here we will be copying the whole of markdown-parse onto ieng6:

![screenshot](scpR1.jpg)

There will be a long output of all the hidden files and public files it copies over to the remote server. 

Now when we ```ssh``` into ieng6 and use the ``` ls``` command:

![screenshot](copyMP.jpg)

We see that we have the folder now on our remote server we can run the files in that folder on ieng6. 

![screenshot](runtest1.jpg)

As seen above. Make sure to ```cd``` into the markdown-parse folder before running tests. 

These are the compile and run commands for future reference:
```
javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java

java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest
```

Now, we can make this process faster by combining the lines to copy the files over to ieng6 and ssh into the remote server in one step then running the files in one line once we are in:

![screenshot](comboRunTest1.jpg)

Then after we have been logged in:

![screenshot](comboRunTest2.jpg)

We can ```cd``` into markdown-parse and use the two command lines from above to compile and run the files (I used a makefile created in week 6 lab that has the two command lines to make the command line look cleaner)

Through combining the command lines, we can copy to a remote server, enter the server, and run the files all in just a few keystrokes. 

### This is the end of lab report #3!

