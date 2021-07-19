# Matching a Hex Value: Regex Tutorial

This file is intended to explain the details of how a specific regular expression works. This particular regular expression is used to match a HEX value. The description below will detail each component of the regular expression and how it works. 

## Summary

We will be evaluating the following regular expressions used to match HEX values:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

Description below will provide details  of the anchors, quantifiers, OR Operator, grouping and capturing and bracket expressions used in this regular expression.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)


## Regex Components

### Anchors

Anchor: ^ 

`/^#`

Description: 

Anchors by themselves don't match any regular expression. Rather they assert something about the string (e.g. beginning, end) based on expressions/matching pattern next to the anchor. 

Example: `^This` indicates that the string must begin with `This`

The ^ is an anchor that indicates that the beginning of the string must match the character #. # is used to distinguish a hexadecimal number from a decimal number. However, as we will see in the next anchor, # is optional.

Anchor: $ 

`$/`

Description: Matches the end of the string. Similar to the ^ anchor, $ is used to check if a string fully matches a pattern. However, $ asserts the pattern to the end of the string, not the beginning.

Example: `end$` indicates that the string must end with `end`.

In our case end of string must match with the 3 or 6 character pattern identified before the $ anchor. The 3 or 6 character pattern is described in more detail under Quantifiers. 

### Quantifiers

Quantifier: ?

 `/^#?`

Description: 
? implies a boolean value, 0 or 1. Typically, this makes the preceding symbol/character optional. 

Example: This could be used to distinguish between British and American spelling in a string e.g. colour vs color -- the regex would colou?r

In our regex, the quantifier ? indicates that the character # preceding the quantifier ? is optional. It's optional for # to appear at the beginning of the expression. 

Quantifier: {}

`[a-f0-9]{6}`
and `[a-f0-9]{3}`

Description: 

Quantifier indicates how many time the preceding pattern matches. Normally, the quantifiers are greedy, causing the regex to match as many occurrences of a particular pattern as possible. However, if ? was appended, the quantifier would become lazy-- causing the regex to match as few occurrences as possible. In our case, the quantifier is greedy. 

Example: `2{5}` indicates that 2 must be repeated 5 times. Matching string must be 22222.

In our regex, {6} indicates that there are 6 instances of the string in the preceding bracket expression. That implies that this quantifier will allow exactly 6 characters in the string containing characters between a-f and/or integer between 0-9.
{3} indicates that there are 3 instances of the string in the preceding bracket expression. That implies that this quantifier will allow exactly 3 characters in the string containing characters between a-f and/or integer between 0-9.

### OR Operator

OR Operator: |

`[a-f0-9]{6}|[a-f0-9]{3}`

Description: The | indicator (i.e. OR indicator) is a boolean that matches either the expression before or after.

Example: 3|5 indicates that either 3 or 5 or both integers are allowed in the string. 353 or 333 or 555 are all acceptable matching patterns. 

In our case, that implies match with 3 character string containing lower case a-f and/or integer 0-9 OR a string with 6 characters containing lowercase a-f and/or integer between 0-9. A matching string has to have 3 or 6 character with the specified pattern. Anything other than 3 or 6 characters will not match. 

### Character Classes

 `a-f0-9` <br>
Description: <br> Character classes only matches one out of several characters defined in the character set. A hyphen can be used inside a character class to define a range of characters More than one range can be used -- as is the case in our code snipet. 

Example: <br>
`[0-9]` <br>This character class matches a single digit between 0 and 9

In our case, the character class consists of lower case a-f and/or integer 0-9 


### Grouping and Capturing

Grouping and Capturing: ()

`([a-f0-9]{6}|[a-f0-9]{3})`

Description: <br>The () groups the regular expression between them. The grouping treats multiple characters as a single unit. 
This can proof useful when extracting information using any programming language. This group of data will be exposed in the form of an array. Values can be accessed using an index on the result of the match. 

Example: (dog){3} matched dogdogdog. The unit of characters 'dog' would need to repeat 3 times indicated in the quantifier. 

In our case, the grouped expression is a bracket expression whose details are provided in the section below. Ultimately the end string anchor $ is applied to this grouping. 

### Bracket Expressions

Bracket Expression: []

`[a-f0-9]`

Description: <br>Bracket expression is a regex that will match  a specific pattern of characters (alphabetic, numeric, special characters, symbols etc..) defined within the brackets. Typically a hyphen is used to describe a set or range of characters e.g. `[a-z]`. It's possible to use the ^ metacharacter to negate what is in between the brackets. 

Example: <br>`[a-d 1-3]` <br>indicates that the string must include atleast 1 character that is between a and d or 1-3

In our reg ex, the bracket [] expression indicates matching a string that has any lower case character between a-f or any integer between 0-9

### Greedy and Lazy Match
`[a-f0-9]{6}`
and `[a-f0-9]{3}`

Quantifier: {}

Description: <br>Greedy means match the longest possible string. Lazy means match the shortest possible string. 

Example:  `w.+l` matches `well` in `well` but the lazy `w.+?l` matches `wel`

As explained in the quantifier section, normal quantifiers are greedy, causing the regex to match as many occurrences of a particular pattern as possible. However, if ? was appended, the quantifier would become lazy-- causing the regex to match as few occurrences as possible. In our case, the quantifier is greedy.

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
