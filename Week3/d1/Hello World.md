
The first thing you are going to learn is how to print `hello world!`. It is the classic first step for most programming courses.

### Welcome to the IDE

Even though we can run all Python stuff inside the console, it is easier to use some kind of development environment. In this module, it will be `JupyterLab`.

In the terminal (it can be the same window we have used for Python), start JupyterLab.

```bash
jupyter lab
```

It will open automatically at `localhost:8888/lab` and it will look like this:

![](https://i.imgur.com/F9s1HFM.png)

Instruction

Open a new text file in your working directory, name it `main.py`, and copy-paste the following text there:

I used to be a farmer, and I made a fine living  
I had a little stretch of land along the CP line  
But times were hard and though I tried, the money wasn't there  
And the bankers came and took my land and told me "fair is fair".

I looked for every kind of job, and the answer was always no  
"Hire you right now?" they'd always laugh, "We just let twenty go!"  
The government, they promised me a measly little sum  
But I've got too much pride to end up on the streets.

Then I thought, who gives a damn if all the jobs are gone?  
I'm gonna be a PIRATE on the river of Saskatchewan!

This is how it should look:

![](https://i.imgur.com/XTQIvP8.png)

At first glance, this IDE looks kind of weird. We might find ourselves wondering:

- **Why are there strange numbers on the left?**
- **Why are some of the words in different colours?**
- **What an ugly font**

Well, that last one isn't really a question :)

#### There are numbers on the left and that is strange.

Yep – those are line numbers. Python, like most programming languages, thinks about code in terms of lines, in much the same way we might think about the English language in terms of sentences. In the scripts that we are going to write, the code will be read left to right, line by line, by us and the computer.

Having line numbers is often useful and convenient as a way to refer by line to where a piece of code lives. For example, later on, when we get errors (and there will be errors), Python will be kind enough to tell us on which line the error occurred. That's a lifesaver – we can direct our attention straight to where the problem is.

#### Why are some of the words in different colours?

Indeed! Apart from being fun to look at, the different colours in a text editor have semantic significance too – the colour of each word tells us something about it. See if you can spot some patterns in what the text editor has chosen to highlight.

Before reading on, go back to the text editor and ponder it for a bit. Try to guess what makes some words or phrases look different from others. Test your theories by changing the text and noticing what happens.

Ready to read on? Okay. Let's continue.

In the example above, some of the words are green, and the colour depends on the IDE and can differ: `and for sum if all` - these are called **keywords**. They have special meanings which we won't get into just yet but when we see them, they tell us something very specific about the code. The text editor turns them green to signal this special meaning to us.

Some of the other text, like `"Hire you now?"` is in red. This signifies that the code is being interpreted as a `String`. When we wrap text in `"double quotes"` or `'single quotes'`, we are saying to Python: Don't interpret this as code, interpret it as plain text.

#### What an ugly font.

Okay, well that's just an opinion. This text editor, like most text editors designed for coding, uses a monospaced font - a font where each character is exactly the same width. Programmers like to use this kind of font because it lets us line text up vertically, and makes the code easier to scan.

Instruction

To see the difference, try typing `"i"` ten times on one line, and `"M"` ten times on the line below it, then try the same thing in your email client, word processor, or favourite instant messenger. Big difference, right?

Instruction

Before moving on, let's try a few more things:

- What happens if we write a number?
- What happens if we wrap the number in quotes?
- What if we wrap a keyword in quotes?
- What do the colour changes say about how the meaning (a.k.a. the semantics) of the code changes?

### Python in the Terminal

We have talked about the text editor a bit, so now let's direct our attention to _the terminal_. The terminal is also known as the console (a.k.a. the `REPL` which we'll explore as you read on).

The first thing we will do is launch Python from _the terminal_. We can do it with the command `python`

```python
python
```

![](https://i.imgur.com/Cs55cOt.png)

Python will start in _the terminal_ and will look similar to what you can see in the picture above. You can easily find the information about which Python version you have in _the terminal_. Now you can write any Python commands and the output will be shown directly below.

Instruction

Try typing `"Hi terminal, how is your day going?"` and pressing Enter.

![](https://i.imgur.com/bz5s3eI.png)

Oh, so we got an error. That's okay though because, as with all errors, there's a lesson hidden inside it. In this case, we've almost gathered enough information to identify this _terminal_ as a **REPL** – a **Read, Eval, Print, Loop**.

Before we discuss that, what happens if we type `2+2` into the terminal, and press enter?

- Read - When we type something into the prompt and press Enter, it is read by Python. "Okay, message received," says Python, thus concluding the Read step.
- Eval - Next, Python goes through the process of figuring out what the message said. That's called Evaluation. If instead of trying to exchange pleasantries, we type `2+2` and press enter, then Python would read a 2, then a +, then a 2, which it would then evaluate as 4.
- Print - Now that Python has **read** and **evaluated** what we've written, it's time to give us feedback. In the case of `2+2`, Python will print a 4. In the case of asking how Python's day is going, it prints an error.
- Loop - Now that Python has done that, it's ready to repeat the process, back from the start, ad infinitum. We can input another command, hit Enter, and read-eval-print will happen again.

We do the same sort of thing when someone sends us a text message:

- First, we **read** the message.
- Then, we **think about** (i.e. evaluate) what the message means, and what response might be appropriate.
- Then, we **send back a reply**.
- Then, we **wait** for another message. Our behaviour in a text conversation is basically a REPL.

So when we typed `"Hi terminal, how is your day going?"` and pressed enter, Python read what we wrote, started to evaluate it, and then got confused because that's English, not Python. It printed a helpful error to let us know that it didn't understand what we meant.

Now, let's try to print text properly in Python:

```python
print("Hello World!")
```

When you want to go back to _the terminal_ (i.e. quit Python), you can do it with the command `quit`:

```python
quit()
```

The last missing piece is to write real Python code in the text editor and have _the terminal_ interpret it. Remove the text from the main.py file, type this into your file and save it:

```python
print("Hello World!")
```

Now we can execute this file directly from _the terminal_:

```bash
python main.py
```

Note

Make sure you are in the correct directory in the terminal. The directory can be changed using the command `cd`.

This is how you can use _the terminal_ to execute Python scripts.

### Jupyter Notebook

The IDE we are going to work with most is a Jupyter notebook.

Instruction

From the home page of the JupyterLab instance, open a new Jupyter notebook and run the `"Hello World` example inside the notebook.