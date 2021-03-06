# Lab 2
## Test 1 
[Link to failure inducing file](https://github.com/shreyagupta112/cse15l-lab-reports/blob/main/testfile1.md) <br>
Here's the commit for the MarkdownParse file after I fixed the bug:
![Image](test11.png)
![Image](test12.png)

Symptom: 
```
PS C:\Users\sunit\Documents\GitHub\cse15l-lab-reports> java MarkdownParse testfile1.md

Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:769)
        at java.base/java.lang.String.substring(String.java:2709)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParse.main(MarkdownParse.java:27)
```
Before we ran into the bug, we changed the program to run a `for (String line: markdown)` loop instead of a `while loop`.  This helps the user read the program better.  However, if there are more characters after the link, running the file will lead to the symptom of an infinite loop.  The bug in the code was that the program would keep reading the rest of the file after the last link, looking for morelinks which it would never find.  We solved this by inserting the `if (line.subscript(")", line.length)` line which stops the program from going through the text wihtout links in an infinite loop.
---
## Test 2 
[Link to failure inducing file](https://github.com/shreyagupta112/cse15l-lab-reports/blob/main/test-file2.md) <br>
Here's the commit for the MarkdownParse file after I fixed the bug:
![Image](test2.png)

Symptom:
```
PS C:\Users\sunit\Documents\GitHub\cse15l-lab-reports> java MarkdownParse test-file2.md

Exception in thread "main" java.lang.StringIndexOutOfBoundsException: begin 0, end -1, length 27
        at java.base/java.lang.String.checkBoundsBeginEnd(String.java:4601)
        at java.base/java.lang.String.substring(String.java:2704)
        at MarkdownParse.getLinks(MarkdownParse.java:18)
        at MarkdownParse.main(MarkdownParse.java:27)
```
The program can't tell if there is a link inside the text whihc is a bug we had to fix.  The symptom of this bug is that the program couldn't find a `(` or `)` in the text (becasue it isn't there) and would return a `-1 `.  This led to the program trying to get a substring with -1, which iwould lead to an erro becasue you can't do that.
---
## Test 3 
[Link to failure inducing file](https://github.com/shreyagupta112/cse15l-lab-reports/blob/main/testfile3.md) <br>
Here's the commit for the MarkdownParse file after I fixed the bug:
![Image](test3.png)

Symptom:
```
PS C:\Users\sunit\Documents\GitHub\cse15l-lab-reports> java MarkdownParse test-file3.md
39 
[page.com]
```

A bug in the program was that the program only processed lines wiht both paranethesis and brackets and skipped lines wiht links enclosed in either onyl brackets or only parenthesis.  The symptom fo this is that the program wouldn't print out links in the file that were not enlcosed in both brackets and paranthesis, which led to an incomplete output (in the case of this test file an output wihtout any of the links becasue none of the links in the file were enclosed in both parenthesis and brackets).

