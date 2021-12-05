# A RegEx Tutorial - By Juiceke

RegEx, otherwise known as Regular Expresson, is a way to filter through text that can also be used to validate text inputs on websites! You can type certain things into a RegEx to have it look for the specific things you tell it to look for. This may sound simple, but there's a lot of different things that can be done with it! That's why I'm here to (hopefully) give you a better understanding of Regular Expressions by the end of this ReadMe!

## Summary

In this tutorial, I will be using a RegEx that looks for URLs. Go ahead and take a minute to look at it.  
  
```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```
  
Probably looks trickier than you thought it would if you're new to this! Don't worry, I'll explain what's going on with all these different symbols in the different sections below. If there's something specific you need, there are links to every section also below.

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
Anchors check to see if something is in a certain area. For example:  
```^``` is put before a string and looks for something at the beginning of a string, so ```^My dude``` would look for "My dude" at the beginning of a string.  
  
```$``` is put after a string to look for something at the ending of a string, so  ```Looking Good$``` would look for "Looking Good" at the ending of a string.

```^$``` would make sure the string matches exactly what has been put in a string, so ```^My dude! Looking Good!$``` would look for the exact phrase "My dude! Looking Good!"
  
Let's look back at the example RegEx!  
  
```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```  

Do you see the anchors at the beginning and end of the RegEx? Ignoring all the other things in there, it's basically just looking for https:// => any amount of lowercase letters => a period followed by any amount of lowercase letters.
### Quantifiers
Quantifiers look for a certain amount of something in a string.

```+``` Looks for whatever is before it. ```My dude+``` would look for anything matching "My dude" in a string. You could also add as many E's at the end as you wanted, and it would still find it

```*``` Looks for whatever is before it, minus whatever character is directly next to it. ```My dude*``` would look for anything matching "My dud", or "My dude" in a string. You can add as many E's as you want in this one too.

```?``` Is like ```*```, but wouldn't find it if you added any extra E's.  

```{2}``` This is the same thing, but you decide how much it needs. {0} would be the same as ```*```, since it doesn't need an E in the case of "my dude" in that case. {1} would need one E, like ```+```. {2} would need two, and so on so forth.  
  
```{2,}``` Just like the previous one, but it'll look for the number and anything greater than that number. ```My dude{2,}``` would end up finding "My dudeeeeeee" if that were in the string.  

```{2,5}``` Again, just like the previous one, but it looks for the amount of E's between 2 and 5.

```My d(ude)*``` Everything between the () is considered the previous character, so it is now looking for "My d" or "My dude". You could add as many "ude"'s as you wanted to this and it would still find it.

```My d(ude){2,5}``` The previous two combined into one!  

Let's look at the example RegEx again.

```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```

The ```{2,6}``` part of this RegEx is looking for somewhere between two and six characters in the area where you would usually put ".com"
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
