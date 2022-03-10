## Welcome to Lab 5

### [Home](https://ank010.github.io/cse15l-lab-reports/index.html)

### Finding the tests that caused different outputs

During Lab 9, I created 2 files, results.txt in Mymarkdown-parse and results2.txt in markdown-parse directory which was Professor Joe's updated verion of MarkdownParse. The command to create these files was:

```
bash script.sh > results.txt
```
run on both versions of MarkdownParse. 

Then, using the command diff, I created an output that showed all the tests that outputted different "links" between my version and the professor's version. Below is the command used:

```
diff Mymarkdown-parse/results.txt markdown-parse/results2.txt
```
From this, I chose two tests: 
[test-files/493.md](https://ank010.github.io/cse15l-lab-reports/test-files493.html)
and
[test-files.499.md](https://ank010.github.io/cse15l-lab-reports/test-files499.html)


### Test File 493

My implementation outputted: ```[<b, <b>c]```
Professor's implementation: ``` [<b, <b, <b>c]```

Based on the preview of test file 493, both outputs are wrong, there are no links in the file. It seems that each one of the supposed links in this file have < in between the (). In markdown, to create headers or pargraphs in html, <> are used to indicate the start or end of an object. Seeing this within the parenthesis, when generating the html version of the file, the compiler might be trying to create a header or paragraph instead of a link like we want. Looking at my code, we check for a ! before the open bracket to make sure the link we get isn't for an image but an actual link. Similarly, once we find the open and close parenthesis, in my code, before adding everything in between those two indices to the ArrayList, we can check if the substring between the parenthesis contains a < or >. There is no line to be fixed, but rather a line to be added at the location mentioned earlier.

### Test File 499

My implementation outputted: ```[ ]```
Professor's implementation: ```[foo\]```

Based on the preview of test file 499, the correct output should be: ```[foo):]```. While the professor's implementation correctly identified that there is a link, whereas mine didn't find one, the link that was found was still incorrect. Similar to a problem mentioned in the previous lab report, for Mymarkdown parse it would be better to change how we match the brackets to correctly identify which brackets match up with which. I am not completly sure why my implementation is not outputting the same thing as the Professor's as it should identify ```(foo\)``` as the parenthesis and the link, however it fails to do that. In any case, the bug is A) not matching the close parenthesis to the open from outside in - starting from the close paren closest to the end of the line and work in from the first paren matching them and then B) not recognizing the backslash in the link. Website links do not have backslashes, so any link with a backslash is either invalid or is for a file system. In either case, below are the two chunks of code that need to be changed:
```
 int nextCloseBracket = markdown.indexOf("]", nextOpenBracket);
 int openParen = markdown.indexOf("(", nextCloseBracket);
 int closeParen = markdown.indexOf(")", openParen);
 ```
 and 
 ```
  if(openParen - nextCloseBracket == 1){
                    String substring = markdown.substring(openParen+1, closeParen);
                    if(!substring.trim().contains(" ")){
                        if(nextOpenBracket != 0 && markdown.charAt(nextOpenBracket-1) != '!'){
                             toReturn.add(markdown.substring(openParen + 1, closeParen));
```
Adding additional checks and fixing up the code in these two blocks should help fix the problem. 

## End of Lab 5!