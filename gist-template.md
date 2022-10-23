# REGEX: MATCHING AN EMAIL

A regular expression is a sequence of characters that defines a search pattern, for text, that can be used within all programming languages. A regular expression is often reffered to as a "regex" in programming.  

The concept of regex comes from the mathematical concept of "regular sets", loosely defined as any set that represents the value of the regular Expression including the intersection, complement, difference, reversal, closure, and concatenation of two regular sets.


## Summary

A regex can be used in validation of email input. It cannot match all possibilities, but can be used to identify proper formatting for the vast majority of email addresses. Proper formatting can be defined as a username followed by an "@" symbol, followed by a domain name, followed by ".", followed by a top-level domain name. 

    (username)@(domain).(top-level_domain)

The following snippet is the regex defining a search pattern for the above email address format:

    /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/


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

In programming, there are two ways to construct a regex: literal notation and using a RegExp constructor. A regex is manually constructed using literals wrapped in forward-slash characters. A regex may contain anchors, bracket expressions, quantifiers, "OR" operators, character escapes, character classes, flags, and other advanced categories. In the case of the RegExp constructor, the regex contained with in the method's ellipses would be wrapped in quotation marks, as opposed to forward slashes. in this gist we will be deconstructing the use of literal notation. 

### Anchors

An anchor indicates the start or end of the input string. This regex contains two different types of anchors:

    ^  $

The ^ anchor filters for a username containing the characters that follow it. In this case the expression seeks to include a range of all letters (a-z), all number digits (0-9), underscores and special characters (periods and hyphens), in a pattern matched one or more times. This anchor also indicates the beginning of the input.

The $ anchor filters for a domain and top-level domain name containing the characters that precede it. In this case the expression seeks limit character input using a quantifier, include a range of all letters (a-z), special characters (periods). This expression preceded by a single full stop. The full-stop, or "." follows the expression that filters for any digit (0-9), letters (a-z), special characters (periods and hyphens), in a pattern matched one or more times. This anchor also indicates the end of the input.


### Quantifiers

A quantifier limits how many characters can be included in the input string, or a sub-set (section) of that string. This regex conatins two different quantifiers:

    + {2,6}

The "+" quantifier requires the preceding pattern be matched one or more times. Meaning valid input can a single "a" or multiple "aaa". Simply this means the string is equal to one or more characters or digits.

The "{2,6}" quantifier requires the preceding pattern to repeat no less than twice, and no more than six times. Simply, this means the string is between two and six characters/digits.


### OR Operator

"OR" operators are used outside of bracket notation, inside a grouping construct. 

    |

Within a pattern the "OR" operator can be used to filter alternative characters/digits, For example "1|a", would filter for a "1" or an "a". 

This regex does not include an "OR" operator. 


### Character Classes

A character class is defined as a set of characters. Using a hyphen inside a character class specifies a range. This regex contains several character classes.

    a-z 0-9 . _ -

"a-z" specifies all individual alpha-characters, "0-9" specifies all individual digits, "." specifies a period, "_" specifies an underscore, and "-" specifies a hyphen.

### Flags

A flag can be placed at the end of regex, outside of the final forward slash. It indicates additional functionality or options. Common examples would include the use of "g" for global search, "i" for a case -sensitive search, or "m" for a multi-line search.

    g i m

This regex does not include a flag. 

### Grouping and Capturing

To set the input string into sub-sets (subexpression), the grouping construct "()" can be used. 

    ()

Ellipses separate the regex into subexpressions, this allows the application of different filters to subsets of the input:

    ([a-z0-9_\.-]+) ([\da-z\.-]+) ([a-z\.]{2,6})


### Bracket Expressions

Bracket expression specifies a range of characters/digits that can be included in the input for each pattern.

    []

The regex uses brackets to include multi-character collating elements such as:

    [a-z0-9_\.-] [\da-z\.-] [a-z\.]

The input must match the set of list expressions contained in each set of brackets.


### Greedy and Lazy Match

This regex includes quantifiers, which are inherently "greedy matches". The expreesion seeks to match as many occurrences of the pattern as possible.

    [a-z0-9_\.-]+

For example the above subexpression seeks to match the bracket expression at least once, with no upper limit. Meaning you it could match "a" to "aaaa...". In this example the subexpression would seek to match the longest possible string in the pattern search. A lazy match can also be specified:

    ?

The "lazy match" seeks to match the shortest string possible i.e. "a"


### Boundaries

The word boundary can be used to form words to be searched, as opposed to individual characters/digits. A boundary immediately precedes the first character of a word, and immediately follows the last character.

    \b

This regex does not include any boundaries. 

### Back-references

A back reference specifies the search repeat the preceding group capture.

    \1

This regex does not include any back-references. An example would be:

    ([a-z0-9_\.-]+)\1 = ([a-z0-9_\.-]+)([a-z0-9_\.-]+)


### Look-ahead and Look-behind

Look-ahead specifies a search pattern for what immediately follows the current position in the string.

    (?=what)

Look-behind specifies a search pattern for what immediately precedes the current position in the string

    (?<=what)

There is no look-ahead or look-behind in this regex.


## Author

# Patrick Ratcliff
# GitHub Username: PatrickARatcliff
# GitHub Repo URL: https://github.com/PatrickARatcliff/m17c-regex


