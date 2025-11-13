
We're going to learn the essential building blocks of programming from the perspective of being a total beginner. The concepts covered will become the very tools that you'll utilize throughout your data science career.

### Please write code!

Learning to code is like learning to play music. You can read all about how to play the guitar, but unless you actually have your hands on the instrument to practice unfamiliar movements and patterns, you're not really learning to play the guitar. To get the real value out of this course, you must have your hands on keys, writing Python, running into errors, and solving problems with your own brain.

Sample code will be sprinkled throughout the program. You are strongly encouraged to write it out yourself and run it, even if you think you understand it. The very act of writing it out helps you learn. Once you've done that, experiment with it: change the order of the lines, modify the text, or put in different numbers. When you think you know how some code works, try to find ways to test your hypothesis.

Programming is a creative pursuit, and when you get the hang of it, should start feeling expressive. Whatever you do, as you go through this course, please write as much code as you can.

### A language is just a tool

Although we will be using the Python programming language, this is not a Python course. Rather it is a data bootcamp that happens to use Python because it's a popular tool used by data professionals. The intuition, wisdom, knowledge, and patterns of thinking that you develop here can be carried to many different languages and paradigms. Even though many languages could be appropriate to this end, we chose Python.

### Why Python?

That's a good question. There are many "data" languages out there, and you might have the impulse to learn the "best" one... But it's not really so simple. Programming languages are like sports, or music genres: a handful are wildly popular, many more have a small but passionate following, and the lack of an objective metric for "bestness" doesn't stop people from arguing about them.

We aren't going to try to make the case that Python is the best language, just as we'd never try to argue that golf is the best sport or that jazz is the best kind of music. But it is relevant in the job market and will allow you to pursue a wide variety of opportunities once you graduate from this bootcamp. Furthermore, here are a few things we like about it:

#### 1) Python is a friendly language for beginners (and data scientists)

Programming languages are designed to be easy to understand. It's hard to believe that when you see a line of code in Javascript, which is yet another alleged beginner friendly language, it looks like this:

```javasript
res.map(figArr => figArr.reduce((acc, next) => next ? next + acc : acc , 0)); 
```

But it's true. Every programming language ever invented was designed to be "easy" in some way. But for people who are not computer scientists, esoteric syntax with lots of brackets and parentheses (which are different!) can be a big barrier to entry.

Python is unusually human-readable. Even other "beginner-friendly" languages (like Javascript) expect you to wrap your brain around unusual patterns and complicated syntax, like in this snippet of Javascript:

```javascript
for (let i=0; i<contacts.length; i++) {
  send_email_to(contact[i]);
}
```

The same thing can be communicated in Python with a much more readable syntax:

```python
for contact in contacts:
    send_email_to(contact)
```

Combined with descriptive error messages (which is a good thing!), great documentation, and a supportive online community, this all makes Python highly accessible for beginners.

#### 2) Python is a friendly language for experts, too

The fact that Python is great for beginners does not mean that it's a "beginner language," to be left behind for something more powerful once you get the hang of it. You very well may move on to other languages (and it's a good idea to try new ones), but if you like Python, it is powerful and expressive enough to be useful for your entire career. Many of the virtues that make a language friendly for beginners also benefit seasons professionals too.

#### 3) Python is extremely versatile

Python has a terrific ecosystem of libraries, frameworks, and tools that lower the barrier of entry to do really powerful things. Here are just a few examples:

- Understand, analyze, and express enormous sets of data with libraries like Pandas
- Build a machine learning model with Sklearn
- Create an AI superintelligence that can seamlessly blend pop culture references into iconic works of art with Google's machine learning framework, TensorFlow
- Build a sophisticated web app with Django, or something simpler with Flask
- Build a game with Pygame
- Program your own Internet of Things devices with a Raspberry Pi

Of course, most people won't become proficient at all of these things... But by choosing Python, you are making it easy to dabble in all of these things, and eventually, to mix them together in interesting ways.

#### 4) Python is popular

Partly for the reasons already described, Python is astoundingly popular. Depending on who you ask, it may be the most popular of all programming languages. It has broad appeal, and great versatility, and there may or may not be hundreds of job openings in your area for folks proficient with it.

"Popular" doesn't always mean "good," or "the right choice for me", but there are some benefits to working with something popular. More people learning your language means that there are more resources to help you learn, more of other peoples' code for you to use, more beginners asking questions and getting answers for your perusal on forums like StackOverflow, and more people to answer questions for you when you get stuck. If you take it far enough to go pro, it also means more job opportunities :)

### What will I learn?

In the coming activities, we are going to learn the fundamental mechanics of the Python programming language, and in doing so, learn how data professionals break down problems and solve them with code. Programming is the act of codifying thought, which is why we call it "coding." Half of the task is understanding the way that code is written, kind of like how learning to read (and perhaps write) sheet music is part of learning to play the piano. The other part of the task is learning how to think in a way that is sufficiently specific to be captured in code. Here is a quick summary of the things we will be covering:

- Data and logic: the two sides of every piece of software
- Variables: the fundamental way in which data is stored and accessed programmatically
- Strings: working with and manipulating text
- Numbers: these are what they sound like :)
- Lists, Tuples, and Dictionaries: a look at how complex data structures can be created and used
- Loops: a powerful tool that repeats a certain process until a specified condition is reached
- Conditionals: different computations or actions performed depending on certain conditions
- Logic and Flow Control: the code that controls decision making
- Functions: a certain procedure or routine