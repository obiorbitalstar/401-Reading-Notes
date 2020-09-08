# Python Regular Expression 
Regular Expressions, often shortened as regex, are a sequence of characters used to check whether a pattern exists in a given text (string) or not

in Python, regular expressions are supported by the re module, meaning if you want to strat using them you have to import this module 

```
import re 

```
the re library in python provides serveral functions that make it worth mastering 

## Basic Patterns: Ordinary Characters
ordinary characters are the simplest regular expression,They match themselves exactly and do not have a special meaning in their regular expression syntax
Examples are 'A', 'a', 'X', '5'.

``` 
pattern = r"Cookie"
sequence = "Cookie"
if re.match(pattern, sequence):
    print("Match!")
else: print("Not a match!")

```
output: 
```
Match!

```

## Wild Card Characters: Special Characters
Special characters are characters that do not match themselves as seen but have a special meaning when used in a regular expression. For simple understanding, they can be thought of as reserved metacharacters that denote something else and not what they look like.

* . - A period. Matches any single character except the newline character.

```
re.search(r'Co.k.e', 'Cookie').group()

```
output:
```
'Cookie'
```
* ^ - A caret. Matches the start of the string.
> This is helpful if you want to make sure a document/sentence starts with certain characters.

```
re.search(r'^Eat', "Eat cake!").group()

```
output 
```
'Eat'
```
* $ - Matches the end of string.
```
re.search(r'cake$', "Cake! Let's eat cake").group()

```
output:
```
'cake'
```

* + - Checks if the preceding character appears one or more times starting from that position.

```
re.search(r'Co+kie', 'Cooookie').group()
```
output:
```
'Cooookie'
```
* '*' - Checks if the preceding character appears zero or more times starting from that position.
```
re.search(r'Ca*o*kie', 'Cookie').group()
```
output:
```
Cookie
```
* ? - Checks if the preceding character appears exactly zero or one time starting from that position.
```
re.search(r'Colou?r', 'Color').group()

```
output:
```
'Color'
```




