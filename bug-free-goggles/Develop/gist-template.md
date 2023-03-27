# Regex Tutorial - by Victor Yang

Regular Expression (Regex) are methods and rules for helping developers search for and/or match text. These Regex methods can be used in a variety of ways to perform operations that can match text, validate formats such as email addresses or phone numbers, ensure a user's password matches minimum security criteria and more.

## Summary

This tutorial will cover a number of basic and advanced Regular Expressions. Let's look at the regular expression in the box below:

<mark>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</mark>

This combination of characters might just look like a series of random characters, but this is actually a regular expression sequence of Anchors, Quantifiers, Grouping Constructs, Bracket Expressions, Character Classes, Flags, and other operators that verifies whether or not a given string is a valid email address. The following tutorial will describe how each of the components in this expression works.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Character Escapes](#Character_Escapes)
- [Putting it Together](#Putting_it_Together)

## Regex Components

To start, the contents within our expression must have a '/' at the start AND end of the string. For example, if we were to searching for the specific string of 'ort,' our expression should look like:

 <mark> /fal/ </mark>

This is a match regex query which will specifically search for any case-sensitive instances of the characters 'fal'. Let's apply the previous expression to the following string:

<mark> The *fal*cons are *fal*ling out of the sky! </mark>

Notice that in the string above, we saw two instances of 'fal'. Applying the regex /fal/ to the previous string would give you the previous result.

### Anchors

-   <mark>^</mark> Beginning - Matches the beginning of the string, or the beginning of a line if the multiline flag m is also enabled. This only matches the position, NOT characters.

-   <mark>$</mark> End - Matches the end of the string, or the end of a line if the multiline flag m is also enabled. This only matches the position, NOT characters.

-   <mark>\b</mark> Word Boundary - Matches any position that is at the end of a word. This matches the position of the given character, not the character itself.

-   <mark>\B</mark> Not Work Boundary - Matches any position that is not at the end of a word. This matches the position of the given character, not the character itself.

### Quantifiers

Quantifiers are used to find instances of a specific character, group, or character classes.

-   <mark>+</mark> - Must follow a character, but will match one or more of the same consecutive character.
Example: /a+/ will search for instances of the letter 'a' AND any instance where there are multiple consecutive a's.

-   <mark>?</mark> - The character preceeding this quantifer is optional. The character returns a match between zero to one.

-   <mark>*</mark> - Is similar to the ? that the character preceding this is optional, but this quantifer returns matches in quantities from zero or more.

-   <mark>{}</mark> - Matches the quantity of the character preceding this quantifer.

<mark>IE: /i\w{3,}/ will search for words that begin with the letter 'a' that are longer than 3 characters. Let's apply this expression to the string below:

I have *information* to report. We have found the secret v*illage* of the h*idden* leaf clan!.</mark>

### OR Operator

-   <mark>|</mark> - The OR Operator acts just like a boolean statement. Matches the expression before or after the operator.

### Character Classes

-   <mark>.</mark> - Character Set - This matches any single character however, it does not match return or newline characters.
Example expression /.at/ will result in = That shipment you sent was a much needed update to our equipment.

-   <mark>[]</mark> - Character Set - Match any characters inside of the brackets.

-   <mark>[^]</mark> - Negated Set - Match any characters not inside of the brackets.

<mark>Example expression /[^p]an/ will search for any character that is NOT 'p' followed by characters 'an'. This gives us = Chelsea likes burgers more than pizza.</mark>

-   <mark>[a-e]</mark> - Range - Matches any characters that contains a character code between the two specified characters included between the brackets.

<mark>In this case, this would search for all letters from 'a' to 'e'.</mark>

### Flags

-   <mark>g</mark> - Global - Match anywhere in the string, allowing subsequent searches to start from the end of the previous match.

-   <mark>i</mark> - Ignore Case - Makes the expression case-insensitive.

-   <mark>m</mark> - Multiline - When enabled, beginning and end anchors (^ and $) will match the start and end of a line, instead of the start and end of the whole string.

-   <mark>s</mark> - dotall - Matches any character, including newline.

### Grouping and Capturing

Grouping Constructs help

-   <mark>()</mark> - Capture Group - This grouping construct collects the characters inside and matches the group in that exact order.

-   <mark>(?:)</mark> Non-Capturing Group - This construct groups multiple characters together without creating a capture group.

### Bracket Expressions

-   <mark>(?=)</mark> - Positive Lookahead - Matches groups of text to the main expression without including the main expression in the result.

-   <mark>(?!)</mark> - Negative Lookahead - Specifies a group that cannot match after the main expression. Any matches will be discarded.

-   <mark>(?!)</mark> - Positive Lookbehind - Matches a group before the main expression wtithout including it in the result.

-   <mark>(?!)</mark> - Negative Lookbehind - Specifies a group that cannot match before the main expression. Any matches will be discarded.

### Character Escapes
-   <mark>\+</mark> - Reserved Characters - The following characters has special meaning and should be preceded by a \ to represent a literal character.
Example: the expression \. will search for the character '.'

-   <mark>\t</mark> - Tab - Matches a TAB character. (character code of 9)

-   <mark>\v</mark> - Vertical Tab - Matches a VERTICAL TAB character (character code of 11)

-   <mark>\0 </mark>- null - Matches any NULL characters. (character code of 0)

### Putting it Together
Now that we have a better understanding of regex and how it functions, let's revisit the email validation regex that we saw that the beginning of this excercise:

   <mark>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</mark>

Our expression begins with the meta escape ^ which indicates the start of our input.

Next, we have the capture group <mark>([a-z0-9_.-]+)</mark> which searches for a string containing a range from letters a through z, numbers zero through nine, special characters '_', '-', and '.' in a non-specific order. The quantifier + at the end of the capture group allows this to occur any number of times until the next rule:

This carries on to our next group when a specific character '@' is matched. (for email addresses)

Our next expression <mark>([\da-z.-]+)</mark> is also a capture group searching for numbers zero through nine, letters ranging from a through z, and then special characters '-', and '.' in a non-specific order. Much like the first expression, this one also contains the + quantifier.

This moves to the last group when the \. character escape finds a '.' character in the string.

Lastly, the <mark>([a-z.]{2,6})</mark> expression is another capture group searching for matches with a range for letters a through z plus including special character '.' with a quantifier matching the charcters between two to six times, as many times as possible.

For more regex practice, https://regex101.com/ is a great resource to test expressions. This site also gives the user an explanation of what the expression does, which is a great tool for learning some deeper combinations.

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)

### Author: Victor Yang
Thank you for taking the time to read through this tutorial about Regex! Please reach out to me at vyang9887@gmail.com with any questions.

You can find more of my work on my GitHub page at https://github.com/vyang9887/.
