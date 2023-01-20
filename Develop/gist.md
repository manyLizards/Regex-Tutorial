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

By default, the quantifiers aboce are "greedy", meaning they try to match as much of the string as possible. However, when you add an ```?``` at the end, like so
```*?```
```+?```
```??```
```{n}?```
```{n,}?```
```{n,m}?```
it makes the quantifier "non-greedy", meaning that it will stop as soon as it finds one match.

### OR Operator

You can clarify that the string you're looking for contains one or the other of two characters with the OR operator. For example
I or J would look like ```(I|J)```
0 or O would look like ```(0|O)```
and so on.

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)