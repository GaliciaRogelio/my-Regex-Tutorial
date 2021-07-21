# Matching a Hex Value: Regex Tutorial

In this tutorial I will explain what a regular expression is and how it works. A regular expression is a way to search through a string of text. This particular regular expression or `regex` is used to match a Hex value or a hexadecimal format for identifying colors.

## Summary

This is the regular expression used to match Hex values:

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

We will describe below the details of what anchors, quantifiers, or operator, grouping and capturing and bracket expressions that are used in this regular expression to match hex values.

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

Anchor: `^` 

`/^#`

Description:  

Anchors are part of the family of regex tokens that do not match any specific character but rather assert something about the string or the matching process. Anchors declare that a current position in the string matches a determined location (e.g. beginning of the string, or end of a line)

Example: 
```
`^http` indicates that the string must begin with `http`
```

The `^` is the anchor that indicates that the character `#` must be matched at the beginning of the string. the character # is what distinguishes a hexadecimal number from a deimal number. But, according to the regular expression this symbol is optional and will not be required. In the following quantifier section I will explain why.

Anchor: `$` 

`$/`

Description:

The `$` is the anchor that indicates the end of the string. Just like the `^` anchor, the `$` anchor is used to check that a sting matches the pattern but in this case, this anchor declares the pattern at the end of the string. 

Example: 
```
`com$` indicates that the string must end with `com`.
```

In the case of this regular expression it indicates that the string must match the 3 or 6 character pattern that is identified before the `$` anchor. I will describe with more details the pattern in the quantifier section.

### Quantifiers

Quantifier: `?`

 `/^#?`

Description: 

The quantifier `?` makes the proceding item optional; it means zero or one {0,1}. 

Example: 

```
/colou?r/ will match both color and colour
```

In our regular expression, the quantifier `?` indicates that the character `#` at the beginning of the quantifier `?` is optional.

Quantifier: `{n}`

`[a-f0-9]{6}` and `[a-f0-9]{3}`

Description: 

The quantifier `{n}` indicates the times the pattern should match. usually the quantifiers are greedy ( it can match the longest possible string ) but if a `?` is appended, it becomes lazy ( it matches the shortest possible string ).

Example: 
```
`f{5}` indicates that f must be repeated 5 times. Matching string must be fffff.
```

In our regular expression `{6}` indicates that the quantifier will allow exactly 6 characters; `{3}` on the other hand indicates that it will only allow 3 characters In the string containing a series of characters between `a-f` and/or integers? between `0-9`.

### OR Operator

OR Operator: `|`

`[a-f0-9]{6}|[a-f0-9]{3}`

Description: 

The Or operator or `|` (alternation operator) tells the regular expression to match everything on the left of the `|` or everything on the right.

Example: 
```
`dog|cat` indicates that either dog or cat or both options are allowed in the string. dog or cat or catdog are all acceptable matching patterns. 
```

In our regular expression it indicates that a string that contains lower case characters `a-f` and/or integer between `0-9` will have to either have 3 characters OR 6 characters. Anything else will not match the pattern.

### Character Classes

Character Classes: `[a-f0-9]`

 `a-f0-9` 

Description:

 Character classes or character set is used to specify a range of characters. It will only match one out of several characters defined inside the brackets unless otherwise specified with a quantifier.

Example: 

```
`[0-9]`

This character class matches a single digit between 0 and 9
```

In our regular expression the character class consists of lower case a-f and/or integer 0-9.


### Grouping and Capturing

Grouping and Capturing: `()`

`([a-f0-9]{6}|[a-f0-9]{3})`

Description: 

The `()` are a way to treat multiple characters as a single unit. They are created to encapsulate a group of characters inside a set of parentheses. This allows you to apply a quantifier to the entire group or to restrict alternation to part of the regular expression.

Example:
```
 (crush){2} matches crushcrush which is the unit of characters specified by the quantifier, 2.
 ```

In this regular expression, the character classes and quantifiers inside the parentheses will be ended by the `$` symbol which is an anchor to end the string.

### Bracket Expressions

Bracket Expression: `[]`

`[a-f0-9]`

Description:

A bracket expression is a regular expression that will match a specific pattern of alphabetic, numeric or symbol characters inside a set of brackets. Usually a hyphen is used to describe a set of characters from a specific range like `[a-f]`.

Example:
```
`[c-z2-9]` 

indicates that the string must include atleast 1 character that is between c and z or 2-9
```

In our regular expression, the bracket `[]` expression indicates matching a string that has any lower case character between a-f or any integer between 0-9

### Greedy and Lazy Match

`[a-f0-9]{6}` and `[a-f0-9]{3}`

Quantifier: `{}`

Description: 

Greedy means match the longest possible string. Lazy means match the shortest possible string. 

Example: 
```
 The greedy`h.+l` matches `hell` in hello, but the lazy `h.+?l` matches `hel`
 ```

As explained in the quantifier section, normal quantifiers are greedy, causing the regex to match as many occurrences of a particular pattern as possible. However, if ? was appended, the quantifier would become lazy-- causing the regex to match as few occurrences as possible. In our case, the quantifier is greedy.

## Author

* [Rogelio Galicia](https://github.com/GaliciaRogelio)

I am a junior Web Developer aspiring to become a software engineer. I have always been interested in computer science but never really got into it until now. One of my goals is to learn artificial intelligence so that I can contribute to self driving cars and anything that we see in science fiction.

I hope you find this tutorial helpful and please share in the comments anything that I might have missed!.
