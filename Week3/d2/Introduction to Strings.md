**Strings** are an incredibly useful data type for programmers and end-users. Here is an example of _a string_ with one character:

`"M"`

And here is an example of _a string_ with 5 characters:

`"Moose"`

_Strings_ aren't just words and sentences, they are any combination of characters, with no apparent relationship between them (from the computer's perspective) other than the order that they come in. As far as Python is concerned, these _strings_ both make equal amounts of sense:

- "You can't always get what you want, but if you try sometimes, well you just might find you get what you need."
- "JHIASUIWUhjhkajhgiuha#72898&%(_237_@&🦄🦄🦄🦄🔥"

Python thinks: "A bunch of characters with quotes around them, must be a _string_." The quotes are the important part here. They have a special meaning in Python, similar to how they have a special meaning in English.

When we throw quotes around a bit of code in Python, it signals to the Python interpreter (and other humans) that the programmer is no longer giving programming instructions, they are defining some literal text.

> #### Python Primer
> 
> Follow [this video](https://learningimages.lighthouselabs.ca/Data+BC/Statistical+Modelling+in+Python/1.+Python+Fundamentals/Python+Primer_+String+Data+Type.mp4) for some more details on how to work with the string data type.

Instruction

Try it yourself: type something in your notebook. With or without quotes.

We have tried the following examples:

1. `Hello, world!` without quotes is not _a string_. It results in an error because Python is trying to read it as programming instructions.
2. `"Hello World"` with quotes is _a string_, and so it works fine. Python doesn't try to interpret it as anything other than _a string_ of text.
3. `2+2` without quotes is not _a string_ – Python sees a number 2, followed by the + operator, then another number 2. That's a programming instruction: "Add these two numbers together." It does so, and gives us 4.
4. `"2+2"` with quotes is _a string_ – Python just sees the regular symbols "2+2," with no expectation that those symbols are supposed to interact with each other in any way.

### Double or Single Quotes?

`"Double quotes"` and `'single quotes'` are both fine to wrap _a string_ in. But beware! We have to be careful about when we use single quotes and when we use doubles. What if our _strings_ also contain those characters? When we make this type of error, we get a hint from our text editor.

We will run the following examples:

```python
print('Let's get down to business!')
print("Let's get down to business!")

print('I said, "we should go" and we left.')
print("I said, "we should go" and we left.")
```

The syntax highlights change unexpectedly in the middle of _the string_. That's a classic sign that something is wrong. In the first example, Python thinks that `"Let"` is _a string_, and `"s get down to business!"` is a programming instruction. It is not. This will fail with `SyntaxError`.

What does the error say? `"SyntaxError: invalid syntax"`. Big hint. A syntax error means that there's something wrong with the way that we formed our Python code. In English, there is an obvious syntax error in the phrase `"Where are y?ou going."` A question mark can't go in the middle of a word. The phrase is malformed. That's in contrast to, say, an error like `"Where is you going?"` which is grammatically incorrect but syntactically correct.

In Python, a syntax error means `"You're breaking the rules of what valid code looks like."` In this case, it doesn't know what to do with an `"s"` after _a string_, so it puts a little arrow there to let us know where it tripped. Could Python infer that there was another quote forthcoming and that that one was meant only as an apostrophe? Perhaps. But Python, like any self-respecting programming language, **abhors ambiguity**: If you start _a string_ with a single quote, then the next time a single quote appears, it had better be to end _the string_.

We can fix this by replacing the single quotes with double quotes, as in line 2. Now, the single quote (used as an apostrophe) is interpreted as any other character. There is no more ambiguity. The single quote (apostrophe) cannot possibly indicate that _the string_ has ended.

The same thing is going on in lines 4 and 5. Single quotes are no problem, but double quotes confuse the interpreter, making it think that we've ended _the string_ early.

#### What if we have _strings_ with both, single and double quotes?

Let's take a look at the following example:

```python
print("She asked, "Can't we just leave?" If only it was that simple.")
print('She asked, "Can't we just leave?" If only it was that simple.')
```

In the example above, we try double quotes first. That doesn't work because the dialogue `"Can't we just leave?"` is wrapped in double quotes, and any person well versed in English will tell you that this is the correct way to present dialogue.

We try single quotes. That solves the dialogue problem, but now the (also correct) apostrophe in `"Can't"` interferes. We've exhausted our supply of quotes.

Luckily, we aren't the first people to notice this problem. As we'll find is often the case, those intrepid programmers before us have given us a solution: In this case, it is called the escape character. Enter the mighty **backslash** `\`.

```python
print("She asked, \"Can't we just leave?\" If only it was that simple.")
print('She asked, "Can\'t we just leave?" If only it was that simple.')
```

In _a string_, the backslash denotes `"the character immediately after me should be interpreted differently than usual"`. For quotes, that means: Don't interpret this quote as the end of _the string_.

Many other escape characters can be found [in this Python resource](https://python-reference.readthedocs.io/en/latest/docs/str/escapes.html).