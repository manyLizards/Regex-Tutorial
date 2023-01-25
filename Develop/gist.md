# Regex Code: Finding and Matching a URL

Regex code is a way of finding like the find and replace button in most editing softwares. However, Regex is more complex and allows you to look for any criteria that the usual find and replace button would not do. I am going to go into detail of a few Regex components and how they can be useful.

## Summary

I will be covering the regex code for matching a URL. 
Here is an example: 
```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Anchors do not match just any character. They match a position before or after characters.
```^``` matches the beginning of the text, while
```$``` matches the end of the text.
So if you type 
```/^abc/```
Any text that starts with the letter a, the letters ab, or the letters abc will return true. Whereas
```/abc$/```
Any text that ends with the letter c, the letters bc, or the letters abc will return true.

Let's see what that looks like in the code we were given for finding a URL.
```/^(https?:\/\/)/``` means the code should start with http, and
```/*\/?$/``` means the code should end with any of these characters.


### Quantifiers

```*``` Will match the preceding item 0 or more times.
```+``` Matches the preceding item 1 or more times. Equivalent to ```{1,}```
```?``` Matches the preceding item 0 or 1 time. For example, ```/e?le?/``` matches the "el" in "angel" and the "le" in angle.
```{n}``` Where "n" is a positive integer, matches exactly "n" occurrences of the preceding item. For example, ```/a{2}/``` doesn't match the "a" in "candy", but it matches all of the "a"s in "caandy", and the first two "a"s in "caaaaandy".
```{n,}``` Where "n" is a positive integer, matches at least "n" occurences of the preceding item. For example, ```/a{2,}/``` doesn't match the "a" in "candy", but matches all of the "a"s in "caandy" and in "caaaaaandy".
```{n,m}``` Where "n" is 0 or a positive integer, "m" is a positive integer, and m > n, matches at least "n" and at the most "m" occurrences of the preceding item "x". For example, ```/a{1,3}/``` matches nothing in "cndy", the "a" in "candy" the two "a"s in "caandy" and the first three "a"s in "caaaaaaandy".

In our regex to find a URL, we are shown the ```*``` quantifier to signify that we want to find a URL 0 or more times.
We see the ```+``` quantifier as well, displayed as ```([\da-z\.-]+)```, requesting the set of characters 1 or more times, searching for the subdomain.
The ```?``` quantifier can be found a few times throughout the Regex searching for a URL. ```(https?:\/\/)?``` and ```/?``` contain all 3 instances. The first is signifying that the match can find ```http://```, or ```https://```.
We also see ```{n,m}``` in the expression to find a URL in the string ```\.([a-z\.]{2,6})```, which matches the domain. It starts with a period followed by 2 to 6 lowercase letters or periods.


### OR Operator

You can clarify that the string you're looking for contains one or the other of two characters with the OR operator. For example
I or J would look like ```/(I|J)/```
0 or O would look like ```/(0|O)/```
and so on.

### Character Classes

Also called "character set", it allows you to tell the regex engine to match only one out of several characters. Simply place the characters you want to match between square brackets. If you want to match an a or an e, use ```[ae]```. You could use this in ```gr[ae]y``` to match either gray or grey. The order of the characters inside the brackets does not matter. You can also use a hyphen inside a character class to specify a range of characters. ```[0-9]``` matches any single digit between 0 and 9.

We see this a few times in our regular expression to find a URL. First in ```([\da-z\.-]+)```, it matches one or more characters that can be digits, lowercase letters, a period, or a dash. The second instance is ```\.([a-z\.]{2,6})``` which groups lowercase letters.

### Flags

Flags come at the end of regular expressions, like so:
```/pattern/gmi``` with the flags being g, m , and i.
```i``` makes the search case-insensitive, with no difference between A and a
```g``` looks for all matches. Without it, only the first match is returned.
```m``` multiline code
```s``` enables "dotall" mode, which allows a "." to match newline character.
```u``` enables full unicode support. The flag enables correct processing of surrogate pairs.
```y``` enables "sticky" mode: searching at the exact position in the text.

We do not see any flags in the regular expression to find a URL.

### Grouping and Capturing

Groups use the () symbols. They are useful for creating blocks of patterns, so you can apply repititions or other modifiers to them as a whole. In the pattern ```([a-x]{3}[0-9])+```, the ```+``` metacharacter is applied to the whole group. Also, another main use of groups is for processing parts of a match like extracting data or replacing it.
With ```pattern1(pattern2)pattern3```, you'll capture the results of pattern2 for later use but not the parts matched by pattern1 or pattern3. This is useful when you want to extract only a portion of the search.

We group a few things together in our regular expression. 
First, ```(https?:\/\/)?``` groups the http(s) result
Second, ```([\da-z\.-]+)``` groups the subdomain
Third, ```\.([a-z\.]{2,6})``` groups the domain
And lastly, ```([\/\w \.-]*)*``` groups the path.

### Bracket Expressions

Brackets indicate a set of characters to match. Any individual character between the brackets will match, and you can also use a hyphen to define a set.
Curly braces are used to specify an exact amount of things to match. They are used after an expression: ```\na{2}\``` will only match 'na' exactly twice.
Parentheses represent remembered matches. Once a match is remembered, you can use ```$n``` to refer to it, starting with ```$1``` up to ```$9```, or with ```$&``` to refer to the entire match.


### Greedy and Lazy Match

By default, the quantifiers above are "greedy", meaning they try to match as much of the string as possible. However, when you add an ```?``` at the end, like so
```*?```
```+?```
```??```
```{n}?```
```{n,}?```
```{n,m}?```
it makes the quantifier "non-greedy", meaning that it will stop as soon as it finds one match.

### Boundaries

The metacharacter ```/b``` is an anchor like the caret and dollar sign. It matches at a position that is called a "word boundary". You can place it before the first character in the string, if the first character is a word character, after the last character in the string, if the last character is a word character, or between two characters in the string, where one is a word character and the other is not a word character. There are no boundary characters in the regular expression to find a URL.

### Back-references

Shown as ```\1```, an example of a back-reference would be ```([a-c])x\1x\1``` which matches ```axaxa```, ```bxbxb```, and ```cxcxc```. There are no back-references in the regular expression to find a URL.

### Look-ahead and Look-behind

There are two types of Look-ahead, positive and negative. 
Negative lookahead is if you want to match something not followed by something else. If you want to find q that is not followed by u, the regex would look like ```q(?!u)```. The construct is a pair of parenthesis with the open parenthesis followed by a question mark and an exclamation point.
Positive lookahead is the same. ```q(?=u)``` matches a q that is followed by a u without making the u part of the match. 

Lookbehind has the same effect, but works backwards. 
For negative lookbehind, ```(?<!a)b``` matches a "b" that is not preceded by an "a", using negative lookbehind. It doesn't match ```cab``` but matches the ```b``` (and only the ```b```) in ```bed``` or ```debt```.
Positive look-behind looks like ```(?<=text)```: a pair of parentheses, with the open parenthesis followed by a question mark, "less than" symbol, and an equals sign. Negative lookbehind is written as ```(?<!text)```, using an exclamation point instead of an equals sign.

The regex to find a URL does not utilize the lookahead or lookbehind methods.

## Author

manyLizards, or Jordan Barringer, is a software engineer studying at the University of Texas' online boot camp.