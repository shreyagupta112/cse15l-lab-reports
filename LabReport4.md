# Lab Report 4

[My markdown-parse repo ](https://github.com/shreyagupta112/markdown-parse)

[Reviewed markdown-parse repo ](https://github.com/Alexander-Kourjanski/markdown-parse)


## Snippet 1

### Should produce:
```
[`google.com, google.com, ucsd.edu]
```
### My Code:
```
    @Test
    public void testSnippet1() throws IOException {
        String regFile = Files.readString(Path.of("./snippet-1.md"));
        String[] regLines = regFile.split("\n");
        assertEquals(List.of("`google.com", "google.com", "ucsd.edu"), MarkdownParse.getLinks(regLines));
    }
```
### Reviewer Code:
```
    @Test
    public void testSnippet1() throws IOException {
        ArrayList<String> testfile2 = new ArrayList<>();
        testfile2.add("`google.com");
        testfile2.add("google.com");
        testfile2.add("ucsd.edu");
        String testfilemd = MarkdownParse.converter("./snippet-1.md");
        assertEquals(testfile2, MarkdownParse.getLinks(testfilemd));
    }
```
### My Output:
```
1) testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[`google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com, ucsd.edu]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:36)
```
### Reviewed Output:
```
1) testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[`google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:87)
```
### Question #1:

A minor change would fix this.  I would need to add a few lines that ensures a space between the inner parenthesis and outer bracket exists 
and checks for brackets. I don;t have an issue with my program getting confsued by the backticks so that's not an issue.

## Snippet 2

### Should produce:
```
[a.com, a.com(()), example.com]
```
### My Code:
```
    @Test
    public void testSnippet2() throws IOException {
        String regFile = Files.readString(Path.of("./snippet-2.md"));
        String[] regLines = regFile.split("\n");
        assertEquals(List.of("a.com", "a.com(())", "example.com"), MarkdownParse.getLinks(regLines));
    }
```
### Reviewer Code:
```
    @Test
    public void testSnippet2() throws IOException {
        ArrayList<String> testfile2 = new ArrayList<>();
        testfile2.add("a.com");
        testfile2.add("a.com(())");
        testfile2.add("example.com");
        String testfilemd = MarkdownParse.converter("./snippet-2.md");
        assertEquals(testfile2, MarkdownParse.getLinks(testfilemd));
    }
```
### My Output:
```
2) testSnippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[a.com, a.com((, example.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet2(MarkdownParseTest.java:43)
```
### Reviewed Output:
```
2) testSnippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[a.com, a.com((]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet2(MarkdownParseTest.java:97)
```
### Question #2:

A small code change should be able to fix this.This issue with my code is that it gets confused by all teh parenthesis in snippet 2.  I could fix this by getting my code to ignores all parenthesis until it get to the end of the string by using a subscript method, putting the line as a string, and making the subscript get 1 less than the substring length.

## Snippet 3

### Should produce:
```
[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]
```
### My Code:
```
    @Test
    public void testSnippet3() throws IOException {
        String regFile = Files.readString(Path.of("./snippet-3.md"));
        String[] regLines = regFile.split("\n");
        assertEquals(List.of("https://www.twitter.com", "https://ucsd-cse15l-w22.github.io/", "https://cse.ucsd.edu/"), MarkdownParse.getLinks(regLines));
    }
```
### Reviewer Code:
```
    @Test
    public void testSnippet3() throws IOException {
        ArrayList<String> testfile2 = new ArrayList<>();
        testfile2.add("https://www.twitter.com");
        testfile2.add("https://ucsd-cse15l-w22.github.io/");
        testfile2.add("https://cse.ucsd.edu/");
        String testfilemd = MarkdownParse.converter("./snippet-3.md");
        assertEquals(testfile2, MarkdownParse.getLinks(testfilemd));
    }
```
### My Output:
```
3) testSnippet3(MarkdownParseTest)
java.lang.AssertionError: expected:<[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]> but was:<[, , ]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet3(MarkdownParseTest.java:52)
```
### Reviewed Output:
```
3) testSnippet3(MarkdownParseTest)
java.lang.AssertionError: expected:<[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]> but was:<[
    https://www.twitter.com
,
    https://ucsd-cse15l-w22.github.io/
, github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet3(MarkdownParseTest.java:107)
```
### Question #3:

This can't be changed by a small change in the code.  This is becasue the MarkdownParse works by going thorugh the file line by line with each line being its own link section.  This means in order to fix this bug I would have to substantially change how the code works which would be a major change.