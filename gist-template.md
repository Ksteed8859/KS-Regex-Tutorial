# KS Regular Expression Tutorial

Regular expressions, also known as regex, are a series of letters, numbers, or special characters that define a search pattern. By adding different characters to your regex, you can tell Javascript what sort of characters to look for in a string. This is useful because as it is Javascript, while containing a way to check whether a string contains a certain letter or phrase, they are limited to direct matches. Using regular expressions simply tell your coding language what to look for in a string using one expression, as opposed to coding out "if" statements for each case.

Confused? That's okay! Keep reading to see how to breakdown a regular expression and get a more in-depth explanation of all the pieces that make a regex so handy.

## Summary

For this tutorial, we're going to be breaking down this regular expression used for matching emails. Using this regex, you can tell your code to look at a user email, see if it has characters such as letters, numbers, or special characters, and accept or reject the email depending on what it finds. The regex is listed below, but don't worry if it doesn't make sense. We'll be breaking it down to it's basic parts throughout this tutorial.

Matching an Email – /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

There are two types of anchors in a regex, signified by ^ and $.

The ^ means that the string must start with whatever follows it in the expression. In our case, that means that the email must start with characters that match ([a-z0-9_\.-]+). We'll learn what all that means later on, but for now all you have to know is that the ^ anchor means that whatever follows it must be included in the beginning of the string. If it isn't, the email will be rejected as invalid.

The $ means the exact opposite, whatever precedes it must be included at the end of the string. So in our case, the email must end with characters that match ([\da-z\.-]+)\.([a-z\.]{2,6}).

### Quantifiers

Quantifiers are how we set limits on the string that we can match with. The most common one we see is a restriction on length. 

Quantifiers are called inherently "greedy" because without user intervention, they match as many occurrences as possible. They may include *, which matches the pattern zero or more times, +, which matches the pattern one or more times, ?, which matches the pattern zero or one time, and {}, which are how we set limits.

We can also make Quantifiers "lazy", meaning they'll match as few occurrences as possible. We do this by adding a ? symbol after it.

Taking a look at our regex, there's really only one quantifier in the form of curly brackets: {2,6}. This is one on the length restrictions I mentioned earlier. This expression says that the first number, 2, is our minimum and the last number, 6, is our maximum. Because it is included with a bracket expression at the very end of our regex, ([a-z\.]{2,6}), it's setting a limit on how long the end of the email can be. It can contain letters a-z and special characters " \ " and " . ", but it has restrictions of a minimum length of 2 and a maximum of 6. 

### Character Classes

Character classes within a regex defines what types of characters can be used to fulfil a match in our  string. We've already been over one type of character class, the bracket expression, but there are a few other types out there.

    . - Will match any character except the newline character.

    \d - Matches any Arabic numeral digit.

    \w - Matching any alphanumeric character from the Latin alphabet.

    \s - Matches a single whitespace character, such as a tab or line break.

These can be coded to perform an inverse match by capitalizing the letter after the backslash ( ie: \D).

Our regex doesn't contain any of these, but they are handy shortcuts to know. 

### Flags

Flags are placed at the end of a regular expression that define a limit or functionality for teh entire regex. Similar to quantifiers, but for the whole expression. There are 6 types of flags, but these are the three most common.

    g : Global Search. The regex is tested against all possible matches in a string.

    i : Case-insensitive search. Case is ignored when making a match.

    m : Multi-line search. Multiline input should be treated as multiple lines.

Our regex doesn't contain any of these, but they are still handy shortcuts to know.

### Grouping and Capturing

As your regular expressions get langer and more complicated, we need a way to check and make sure that all parts of the string are fulfilling their requirements. That's where grouping constructs comes in handy. Using grouping, we can contain our regex into smaller subsections, called subexpressions. This is done by wrapping sections of the regex in parenthesis. Our regex is grouped into three subexpressions: ([a-z0-9_\.-]+), ([\da-z\.-]+), and ([a-z\.]{2,6}). As you can see, if subexpression is operating under different bracket expressions and quantifiers. 

Grouping constructs have two categories: capturing and non-capturing. Capturing groups capture matched character sequences for possible re-use, while non-capturing groups don't. The difference between the two in a written regex is that a non-capturing group will contain the characters '?:' at the beginning of the expression inside the parenthesis. None of our subexpressions contain that, so they are all capturing grouping constructs.

### Bracket Expressions

Bracket Expressions are, as the name suggests, expressions that are inside a pair of brackets. Our regex contains several: [a-z0-9_\.-], [\da-z\.-], [a-z\.]. These expressions dictate which characters we want to include in our string.

So let's break down our first bracket expression, [a-z0-9_\.-], to see what exactly can be included in the first part of our email.

[a-z]: This is saying that any lowercase letter between a and z are valid. Notice how the expression only contains lowercase a-z, not capital A-Z. That means only lowercase values are accepted, capitals are rejected. If we wanted otherwise, we would have to change our expression to [a-zA-Z].

[0-9]: This is saying that the string can contain numbers between 0-9, which equates to saying that any combination of numbers is valid since a keyboard only contains numbers 0-9 anyways.

[_\.-]: These are the special characters our email is allowed to contain. A user could have an email with an underscore ( _ ), a backslash ( \ ), a period ( . ), or a dash ( - ) and still be considered valid. However, any other special characters, like a question mark ( ? ) would not be allowed.

### Greedy and Lazy Match

Like I described earlier, quantifiers can either be greedy or lazy. A greedy match means that you're quantifier is matching as many occurrences of a pattern as possible. On the other side of things, a lazy match means you're quantifier is matching as few occurrences as possible. Quantifiers are automatically greedy, they want to make as many matches as possible. A " ? " symbol needs to be added before you're Quantifier becomes lazy.

## Author

Hi! My name is Kate Steed and I'm a student in the University of Utah coding bootcamp where I'm learning full-stack development. Take a look at my github repo for more of my works!

https://github.com/Ksteed8859

