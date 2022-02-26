Test code 1

@Test
    public void testSnippet2() throws IOException {
        String regFile = Files.readString(Path.of("./snippet-2.md"));
        String[] regLines = regFile.split("\n");
        assertEquals(List.of("a.com", "a.com(())", 
            "example.com"), MarkdownParse.getLinks(regLines));
    }
