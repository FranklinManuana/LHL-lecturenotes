Having learned about strings, there's one more thing that we've got to learn before we are able to see the bigger picture: **the numbers**.

What's _a number_? That's kind of a deceptively difficult question for Python to answer (even we would have a hard time coming up with the definition), so let's start by asking an easier question: What isn't _a number_? Well, one thing that _a number_ isn't is a string. How do we know? Well, because we can't do string stuff with _a number_:

```python
print(len(2))
print("I would like " + 2 + " milkshakes, please.")
```

Also, some string behaviours work for _numbers_, but they work differently than we would expect:

```python
2+2
"2" + "2"
"2" + 2
```

Or, at least differently than we would expect if we pretended that we knew about string concatenation but not about addition. Actually, the fact that 2+2 results in 4 is quite natural because that's how _numbers_ work. We can perform things like arithmetic on them, and we don't tend to perform things like string concatenation on them.

So let's revisit the original question: What is _a number_?

And this time, let's call in the [**big guns**](https://en.wikipedia.org/wiki/Number) for the answer: _A number is a mathematical object, used to count, measure, and also label_.

Bafflingly simple, but if we dig deeper, can we think of anything else that you can use _a number_ for? Telling what year it is. That's just counting. Knowing what π is, that's just measuring. Having a credit card number, that's just a label. Just kidding, actually, a credit card number is more like a string of digits than _a number_ in its own right. If we read out a credit card number to someone, we don't start reading "Six quadrillion two hundred and eighty-three trillion..."

So in Python, we expect that we should be able to do things to _numbers_ that involve counting, measuring, and labelling. We'll see more about labelling when we get to Lists. For now, we'll be talking about counting and measuring.

### Integers and Floats

`"String"` is a data type in Python. `"Number"` is not... But clearly _numbers_ are a thing in Python. That's why the 2+2 thing worked earlier. It's true that _numbers_ are a thing. But there is no data type called "Number."

Have a closer look at that error that we got when we tried to add "2" and 2:

![](https://i.imgur.com/1IwBHfC.png)

Here's what we know from that error:

- It's a `TypeError,` which means that there's a problem with the data type(s) involved
- Python thinks that something that is supposed to be a string (`str`) is not a string
- The thing that is supposed to be a string is something called an `"int"`

It turns out that `"int"` is short for **integer**. In Python, _numbers_ are organized into two types: `Integers` and `Floats`. The reason for this is one of those kinds of [**esoteric computer science things**](https://www.dummies.com/programming/c/the-real-difference-between-integers-and-floating-point-values/), which you might find interesting, but absolutely don't need to know for any practical purpose (at least in Python). Here's what we need to know about _the integers_ and _floats_:

- _Integers_ are whole _numbers_, positive and negative, like 10, 600001, and -7.
- _Floats_ are _numbers_ with a decimal, like 3.14, 806.63, and 1.0.

That's about it. We are going to be working mostly with _integers_. Sometimes, _floats_ will show up. Most of the things that we're going to do work the same way for _integers_ and _floats_. If we have _an integer_ and we'd like it to be _a float_, we can just pass it to the `float()` function. The same thing works in reverse. We can pass _a float_ to the `int()` function:

Instruction

Try using the `float()` and `int()` functions with different _numbers_ to see how they work.

#### Incrementation

Suppose you have a value like _x_ = 3, and you want to increase its value by 1. Here is how you would do that in Python:

```python
x = x + 1
print(x)
```

The output will be 4. The computer reads from left to right and says that _x_ equals whatever _x_ was before plus 1. Of course, this is where computer programming differs from mathematics. In mathematics, the equation _x_ = _x_ + 1 is not possible because you can bring the variables all to one side and end up with 0_x_ = 1, or in other words, 0 = 1.

To _increment_ means to increase and to _decrement_ means to decrease. Most coders don't write _x_ = _x_+ 1 as they prefer the shorter notation, _x_ += 1, which means the same thing.

Let's consider the following task: ask a user to input any integer and decrease its value by 5. Try this out in your notebook:

```python
any_num = int(input())
any_num -= 5
print(any_num) 
```

If we can increase and decrease values, what more can we do? Yup, you probably guessed it. You can also change a value by a multiple. Try this out in your notebook:

```python
triple_up = 5
triple_up *= 3
print(triple_up) 

quarter_value = 100
quarter_value /= 4
print(quarter_value)
```

The last thing we'll look at is how to sum up any three integers that you input using incrementation. Try this out in your notebook:

```python
# It's important to start by defining your sum as 0 to start with. 
sum = 0

num = int(input())
sum += num

num = int(input())
sum += num

num = int(input())
sum += num

print(sum)

```

Obviously, it's redundant to keep writing out input() and sum += num so many times. Soon, we'll learn about _loops_ which repeat a process as many times as you want.

> #### Python Primer
> 
> Follow [this video](https://learningimages.lighthouselabs.ca/Data+BC/Statistical+Modelling+in+Python/1.+Python+Fundamentals/Python+Primer_+Number+Data+Type.mp4) for some more details on how to work with the numeric data type.