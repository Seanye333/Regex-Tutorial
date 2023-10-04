# Regex Tutorial for Email & URL

Welcome to my Regex (Regular Expression) Tutorial! This tutorial will explore multiple regex patterns to validate E-mail and URL. Regex is a powerful tool that is utilized for pattern matching within strings. Understanding regex is critical and essential for any programming language. From anchors to Character Escape sections, they will cover almost everything you need to know to master the art of pattern matching. There are two examples to assit you from understanding the concepts. 

## Summary

In this guide, essential compoments of regex will be covered. Each section provides detailed explanations and examples for various regex components. 
Two regex patterns will be describing:
* Matching an Email: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
    * This regex pattern validates email addresses, ensuring they have a proper format with a username, domain, and top-level domain (TLD). 
    
* Matching a URL: `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`
    * This regex pattern is designed to match URLs, both with and without the http or https protocol, capturing different parts of the URL like the protocol, domain, and path. 

We will break down this pattern and explain each component in detail.
## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
The Anchors assert a position at the start and/or end of the line

  * Start of the line: `^`
  * End of the line: `$`
  
In Email Example: 
   * The `^` anchor asserts the start of the line, ensuring that the pattern matches from the beginning of the email address. 
   * The `$` anchor asserts the end of the line, ensuring that the pattern matches until the end of the email address.

In URL Example: 
   * The `^` anchor asserts the start of a line, ensuring that the pattern starts matching from the beginning of the input. 
   * The `$` anchor asserts the end of a line, ensuring that the pattern matches until the end of the input.
  
### Quantifiers
The quantifiers identify how many instances of a group, character, or character class must be displayed in the input to be found by mathcing. 
  * Previous group, character, or character class must occur at least one or more times. `+`
  * Preceding group, character, or character class must be matched zero or more times: `*`
  * Preceding group, character, or character class can occur zero or one time: `?`

In Email Example: 
   * `+` ensures there is at least one character in the username(X.@) and domain(@X).
   * `+` after `([a-z0-9_\.-]+)` ensures that there is at least one or more characters before the @ symbol, allowing various combinations of letters, numbers, underscores, dots, and hyphens.

In URL Example: 
   * `?` is used after the protocol to match it zero or one time
   * `*` is used after the path to match it zero or more times.
   * `?` after the protocol `(https?://)?` matches the protocol zero or one time, allowing both http and https protocols. `*` after `([\/\w \.-]*)` matches the path zero or more times, accommodating various path lengths.

### Grouping Constructs
The Grouping Constructs capture the matched text, allowing you to extract or manipulate specific portions of the input. 
   * Apply quantifiers to part of your regex:`(...)`
   
In Email Example: 
   * `(...)` is used to group for the username, domain, and TLD.
   * `([a-z0-9_\.-]+)`: Captures the username part of the email address, allowing letters, numbers, underscores, dots, and hyphens.
   * `([\da-z\.-]+)`: Captures the domain name part, allowing digits, letters, dots, and hyphens.
   * `([a-z\.]{2,6})`: Captures the top-level domain (TLD) like com, org, net, ensuring it consists of 2 to 6 letters.

In URL Example: 
   * `(...)` is used to group for the protocol, domain, and path.
   * `(https?:\/\/)?` captures the protocol (optional).
   * `([\da-z\.-]+)` captures the domain name.
   * `([a-z\.]{2,6})` captures the top-level domain  like com, org, net.
   * `([\/\w \.-]*)*` captures the path (optional) and allows for multiple path segments.

### Bracket Expressions
Bracket expressions are used to match a single character out of a set of characters. Ex: [aeiou] matches any vowel, specify ranges like [0-9] to match any digit. 

In Email Example:  
   * `[...]` are used to define valid characters for the username and domain.
   * `[a-z]` allows lowercase letters in various parts of the email address.
   * `[0-9]`r any digit.
   
In URL Example: 
   * `[...]` are used to define valid characters for the domain and path
   * `[a-z]` matches any vowel. Ranges can also be specified, 

### Character Classes
Character classes such as `\d` (digits) and `\w` (word characters), `\D` (non-digits),  and `\W` (non-word characters) match specific character types.

In Email Example: 
   * `\d` is used to allow digits in the email address `[\da-z\.-]`.
   
In URL Example: 
   * `\d` is used to allow digits in the domain `[\da-z\.-]`.

### The OR Operator
The OR operator `|` allows you to match either the pattern on its left or the pattern on its right. For example, apple|orange matches either "apple" or "orange".

In Email Example: 
   * Not used 
   
In URL Example: 
   *  Used in the protocol to match both `http` and `https`.

### Flags
Flags modify how the regex is interpreted. Common flags include `i` (case-insensitive) and `g`(global, match all occurrences).

In Email Example: 
   * Not used 
   
In URL Example: 
   * Not used

### Character Escapes
Character escapes like `\/` and `@` match the character literally that match specific characters that would otherwise be treated as regex metacharacters. For example, `\/` matches a literal forward slash.

In Email Example: 
   * `@` is used to match the at symbol in the email address, ensuring it is treated as a regular character and not a regex metacharacter.

In URL Example: 
   * `\/` is used to match the forward slash in the path, ensuring it is treated as a regular character and not a regex metacharacter.

## Author

Thanks for reading the tutorial. Following is my github homepage: https://github.com/Seanye333
https://gist.github.com/Seanye333/8cf9508b5024bde455ce50d1d8860d50
## Credit 
Sepcially thanks to Jackson's page and geeksforgeeks to help develop this tutorial!  
 * https://gist.github.com/jacksonfdam/3000275
 * https://www.geeksforgeeks.org/components-of-a-url/
