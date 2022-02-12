# Lab 3: Copy whole directories with scp -r
Used `scp -r . cs15lwi22aii@ieng6.ucsd.edu:~/markdown-parse` to copy MarkdownParse into my ieng6 account.
I then logged into my ieng6 account using he `ssh` command and entered the markdown-parse directory using `cd`.
I then used `javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java` to compile and 
`java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTestto` run the file.
