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



### OR Operator

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