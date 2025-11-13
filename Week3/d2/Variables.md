There is no coding without `Variables` so it is important to understand what they are.

Imagine being the captain of a cruise ship. The day consists of...actually, you know what? Let's skip the analogy and just look at some code.

Lines that start with a "#" are **comments** and only exist as plain text to help the person reading the code – they are not code.

Have a look at the code below. What does each line do?

Go to your notebook from the previous activity and play around with the code below. Write the code out yourself, and try to change different parts of it – what happens?

```python
# name is a variable. It contains a string
name = "Thomas"
print("Hello " + name + ", it's very nice to meet you!")

# taxRate, subtotal, tax and total are all variables that contain numbers
taxRate = 0.14
subtotal = 20
tax = subtotal * taxRate
total = subtotal + tax
print("Your total bill is: ")
print(total)

# travelDestinations is a variable containing a list
# city is a variable - its value is changing a few times
travelDestinations = ["Vancouver","Montreal","Calgary","Toronto"]
for city in travelDestinations:
    print(city + " looks like a cool place to go!!")
```

Make sure you've run the code above before continuing. Don't worry, we'll wait.

There are a bunch of spoilers here for the upcoming activities and if you're lost, don't worry! The main thing we're interested in is the words in white. That's how this text editor's syntax highlighting shows that a word is _a variable_.

_Variables_ are names that we give to data. We use _variables_, in a sense, in English, too. Consider the following sentence:

_"I really want that phone, but the price is a dealbreaker."_

In that sentence, **"phone"** is _a variable_. The data it refers to is a particular model of phone. **"Price"** is also _a variable_. The data it refers to is a dollar amount. To understand what that sentence means, we could unpack it to say:

_"I really want that Nokia 3310, but $28.00 is a dealbreaker."_

### Why use variables?

One reason that _variables_ are so handy is that giving names to things is a powerful way to organize your ideas. In the second example, we could have just as easily written this totally valid Python code:

```python
print("Your total bill is:")

print(20 + 20 * 0.14)
```

But this version of the calculation is far less clear. What does each number represent? If you were explaining this calculation to another person, we'd use _variables_ in our explanation:

> "To calculate tax, you multiply the subtotal by the tax rate. That's the amount of tax you owe. Then, you add the tax to the subtotal, and that's what you pay in total."

We can apply that logic to any subtotal, and any tax rate. If we used the actual numbers, that procedure wouldn't make sense.

> #### Reflection Opportunity
> 
> When coding the equation of a line, clear and descriptive variable naming can help to make the equation more readable and understandable.
> 
> In the language of mathematics, the most common way to represent the equation of a line is in the form of
> 
> `y = mx + b`
> 
> Where:
> 
> `y` and `x` are the coordinates of the point on the line.
> 
> `m` is the slope of the line, which represents the rate of change of y with respect to x.
> 
> `b` is the y-intercept, which represents the point where the line crosses the y-axis.
> 
> While this is the most common way to represent the equation of a line, there are other mathematical notations that can be used.
> 
> With that in mind, if you were to code the equation of a line using Python, what naming convention would you use for the variables so that they are informative and easily interpretable?

---