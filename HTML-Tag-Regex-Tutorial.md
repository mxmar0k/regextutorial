# Understanding the HTML Tag Regex

HTML, is without a doubt the backbone of web pages; it is made up of various elements, which are often represented by tags. Web developers sometimes need to parse, sometimes extract, or validate HTML content. This is the main reason where regular expressions come in handy. This tutorial aims to dissect a specific regex that matches an HTML tag, helping you understand its components and how it works.

## Summary

The regex that we're exploring in this tutorial is used to match HTML tags. It's particularly crafted to identify both self-closing tags (<img src="image.jpg" />) and paired tags (<div>content</div>). 

Here's the regex pattern that we will be looking in this tutorial:

/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Example](#Example)

## Regex Components

### Anchors

The "^" and "$" are anchor characters: /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/

^ marks the position at the start of a line.
$ marks the position at the end of a line.
But when they are together, they ensure that the pattern matches an entire line: from start to finish.

### Quantifiers

+: This one matches the preceding element one or more times.
*: and this one matches the preceding element zero or more times.

### Grouping Constructs

There are several groups in our regex, we're going to paste it again for quick reference /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/:

([a-z]+): This one matches one or more lowercase letters. In this case, it captures the tag name.
([^<]+)*: This matches any sequence of characters except "<", and it's used to capture tag attributes.
(?:>(.*)<\/\1>|\s+\/>): Finally, this is a non-capturing group, denoted by (?:...). Within it, we have two patterns separated by the OR operator (|):

The first pattern matches content between paired tags, and the second pattern matches self-closing tags.

### Bracket Expressions

Like we said in grouping constructs, [a-z] matches any lowercase letter from 'a' to 'z'; on the other hand, [^<]: matches any character that is not a <.

### Character Classes

Character classes allow for matching one out of several characters. They are denoted by square brackets []. In our regex:

[a-z]: Represents a character class that matches any lowercase letter from a to z.
[^<]: This is a negated character class. The ^ symbol at the start of the class negates the character set, meaning it matches any character that is not a <.

### The OR Operator

The "|" character represents the OR operator, like we anticipated earlier. It allows the regex to match one of several patterns. In our regex, it differentiates between paired tags and self-closing tags.

### Flags

The given regex does not have any flags: /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/. 

But what are they?

Flags are usually specified after the closing / in a regex and they modify the search behavior. 

Common flags include "i" for case-insensitive matching, "g" for global matching, and "m" for multi-line matching.


### Character Escapes

Character escapes are sequences that are used to represent special characters in regex. In our regex, we have a few character escapes:

\<: Escapes the < character, allowing it to be matched literally.
\/: Escapes the / character, allowing it to be matched literally.

### Example

Now that we have all this information, we will use a metaphor to explain the regex. But how?

Imagine the regex is a toy assembly line, and each component of the regex is a station on that line where a toy like Rex on toy story (our HTML string) is being assembled.

The Toy Assembly Line: Building an HTML Tag Toy
Regex: /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/

Start of the Line (^):
This is where our toy begins its journey. Every toy must start here.

The < Character:
Think of this as the base of our toy. Every toy (HTML tag) has this base.

The ([a-z]+) Group:
This is where we choose the color of our toy. Each color is represented by a letter from 'a' to 'z'. If our toy is a 'div' toy, then it's colored 'div'.

The ([^<]+)* Group:
This is the decoration station. Here, our toy can get stickers, buttons, or other decorations, BUT these decorations can't have the shape of the base (<), because that's reserved for the toy's base.

The (?:>(.*)<\/\1>|\s+\/>) Group:
This is the final assembly station with two machines:

The first machine is for toys that have content inside, like a music box. The toy is closed with a lid that matches its color (like </div> for a 'div' toy).
The second machine is for toys that don't open and are sealed shut, like a whistle.
End of the Line ($):
This is where our assembled toy comes out, ready to be played with. Every toy must pass through here.

Toy Examples:

1.- Toy: <div>Music Box Tune</div>

Starts at the beginning.
Gets a 'div' color.
Skips decorations.
Goes through the first machine and gets a musical tune inside. It's sealed with a 'div' colored lid.
Comes out ready to play!


2.- Toy: <whistle />

Starts at the beginning.
Gets a 'whistle' color.
Skips decorations.
Goes through the second machine and is sealed shut.
Comes out ready to be blown!


And that's how our toy assembly line (regex) builds HTML tag toys! 🧸🎨🎵

I hope this was clear for youuuu!

But if you have any doubts, please feel free to contact me.

## Author

Follow me on https://github.com/mxmar0k

Deployed GitHub-Gist:

Repository: https://github.com/mxmar0k/regextutorial


