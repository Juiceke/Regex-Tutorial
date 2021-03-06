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

```{2,5}``` Again, just like the previous one, but it looks for between 2 and 5 E's.

```My d(ude)*``` Everything between the () is considered the previous character, so it is now looking for "My d" or "My dude". You could add as many "ude"'s as you wanted to this and it would still find it.

```My d(ude){2,5}``` The previous two combined into one!  

Let's look at the example RegEx again.

```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```

The ```{2,6}``` part of this RegEx is looking for somewhere between two and six characters in the area where you would usually put ".com"
### OR Operator
The OR Operator is used to look for more than one thing or another. 

```x(y|z)``` Will look for whatever is in place of x, followed by y or z! In this case, it would find ```xy```, ```xz```, and ```xyz```.

```x[yz]``` Will look for whatever is in place of x, followed by y and z. In this case, it would find ```xyz``` only.

Lets take a look the example RegEx again:  
```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/```  
In the regex, I do not see anything that matches this.

I'm not too confident about this one, so feel free to correct me about OR Operator's if you know better!
### Character Classes
Character classes will look for certain kinds of characters in the text.

```\d``` would match any single character that is a number. Ex: ```1```, ```2```, ```3```.

```\w``` would match any single character that is a letter. Ex: ```a```, ```b```, ```c```.

```\s``` would match any whitespace character in the text. Ex: spaces and tabs in a document.

```.``` would match every character. Ex: Everything!

There are some more things you can do with these. Here are those other things.  

Making the character after the / capitalized makes it do the opposite. /D looks for everything not a number and all that.

Putting something before the / will make the regex look for something more specific. For Example: ```f\d``` would look for f followed by a number.

Let's see if anything in the example regex matches this.  

```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$```

```[\da-z\.-]``` uses the \d character class, and ```([\/\w \.-]*)``` uses the \w character class.

There's more things you can do with it, but this is everything you need currently.
### Flags
Flags will be something you put at the end of your Regex to change how it is read. The example Regex doesn't use this, so I will not be going into detail on it in this tutorial.

### Grouping and Capturing
Capture groups are groups of characters we make using ```()```. 

```x(yz)``` makes a capturing group for the value bc after an a, so the RegEx looks for ```xyz```

```x(?:yz)*``` uses a ```?:``` to cancel the capturing group, which will cause it to still look for ```xyz```, but will also look for just ```x```.

```x(?<dude>yz)``` uses ```<>``` to name the capture group, so now the ```yz``` group is named dude.

Let's see if anything in the example regex matches this.  

```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$```

```(https?:\/\/)``` cancels the capture group so it will accept that start, but doesn't need it to be a URL.
### Bracket Expressions
Bracket expressions can be used to do some previous things quickly!

```[xyz]``` is the same as using an or operator to say ```x|y|z```.

```[x-z]``` is the same as the previous example because it is looking for x,z, and everything between the two! It will not find capitalized letters unless you also put those in!

```[0-9]%``` looks for a number with a percent sign in front of it!

```[^x-zX-Z]``` looks for a string that doesn't have whatever is in front of it within the brackets!

Let's see if anything in the example regex matches this.  

```/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$```

```([\da-z\.-]+)\.([a-z\.]{2,6})``` 

We can see two examples of a bracket expression in this RegEx! there are two ```[a-z]``` bracket expressions within the regex that look for lowercase a through z in both of those areas! 
### Greedy and Lazy Match
Greedy operators will expand a match as far as it can, so if I wanted to look for a div in something, it would match everything within the div. Some greedy operators would be ```* + {}```. 

Lazy operators will look for said item, and only said item, so if I were to look for a div, it would only find the ```<div>``` parts of the text. A lazy operator would be ```?```

Greedy Operator that finds everything between two <> signs: ```<.+>```

Lazy Operator that finds only the <> signs: ```<.*?>```

### Boundaries
Boundaries will only look for things within boundaries that you set.

```\bdude\b``` will only look for the word dude with nothing around it.

```\Bdude\B``` will only look for dude if some letter characters are around it!
### Back-references

### Look-ahead and Look-behind
Look-ahead and Look-behind will look for something as long as a character you decided is behind or in front of it.

```x(?=y)``` will find an x as long as a y is in front of it, but it will not match the y with it.

```(?<=y)x``` will find an x as long as a y is behind it, but it will not match the y with it.

There is also an opposite way to do this.

```x(?!y)``` will find an x that has anything but a y in front of it.
  
```(?<!y)x``` will find an x that has anything but a y behind it.

## Author

I am Juiceke and I am currently studying code, so please let me know if there was anything I can change in this. It will improve the tutorial along with my understanding of RegEx! :)

My profile: https://github.com/Juiceke
