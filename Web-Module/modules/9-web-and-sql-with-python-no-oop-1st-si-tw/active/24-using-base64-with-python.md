# Using Base64 with Python

## What is Base64?

To understand Base64, you need to slightly understand how characters are actually stored.

In the lowest level, you can only store 1s and 0s, right? So we have to translate the character to numbers, that can be later stored as a binary number. To do this, people invented character tables, so we can translate a specific character to a number.

Currently there are hundreds of character tables as standards, so sometimes we need to pick what is best for us.

Let me shortly introduce you to the 2 most common ones:

### ASCII table

ASCII is from the 60s, so we can call it the most ancient character code in the word of IT. It looks like this:

![asciifull.gif](media/Web%20with%20Python%20module%20resources/asciifull.gif)

You can see, it consist of some control characters, english letters and some operator characters. Not much...

Despite its limitations, it's very good for storage, because 1 ASCII character (1 thing from the 128 options) is stored in 7 bit. (which uses 1 byte)

### Unicode

As a modern extension, and widely used standard, Unicode was created as a universal character table.

UTF-8 is the encoding that implements the Unicode standard, but sometimes they refer to the same thing.

ASCII was incorporated into the Unicode (1991) character set as the first 128 symbols, so the 7-bit ASCII characters have the same numeric codes in both sets. This allows [UTF-8](https://en.wikipedia.org/wiki/UTF-8 "UTF-8") to be backward compatible.

This standard allows us to store huge variety of characters, but in the cost of using 4 bytes, instead of the 1 byte that the ASCII standard uses. Meaning » 4 times the storage.

## So why Base64?

A string variable is just a special array, containing only characters. Modern languages, like Python totally hides this fact from us to make it more convenient to use.

When you want to store a string, you actually store it's characters. 

\--..... .. to be finished
