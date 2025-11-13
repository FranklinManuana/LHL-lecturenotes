In programming, **data** is any information that is represented digitally in a way that a computer can interact with it.

**Logic** is the plan that the computer has for interacting with data. Learning to program is simply learning to create interactions between data and logic. We might call that interaction **behaviour**.

If the data is a text message, the behaviour we create could be to spot typos and correct them automatically. If the data is the reading of a clock, the behaviour might be to notice what time it is and remind you about appointments that you've set up (which are also data). It could be to capture the details of your pizza order and arrange for it to reach someone in a kitchen who is proficient with cheeses and dough. Computers don't know about pizza. To a computer, data and logic are all that exist.

### Representing Data

Let's work with the pizza example. Here's how we might express a pizza order in plain English:

"I'd like a large pizza with feta cheese, prosciutto, olives, and arugula, on a gluten-free crust. Please deliver it to 401 Somewhere St. Specifically, to the treehouse in the back yard."

Imagine it's the year 1998, and it's you on the other end of that landline call. With the receiver of the restaurant's rotary telephone pinched between your ear and shoulder, you jot down the details of this order to hand off to the kitchen. You might write something like this:

![](https://i.imgur.com/zvDpcxB.png)

Though you might not think of it this way, you've captured the data of the order and encoded it in written text. It's broken up into just the facts that the system (in this case, the kitchen and delivery personnel) can make use of. All of the relevant data is captured succinctly, with no unnecessary fluff. The representation of a pizza order in plain English is actually quite similar to how it might be represented in plain Python:

```python
pizza = {
    'size': 'large',
    'toppings': [
        'feta',
        'prosciutto',
        'olives',
        'arugula'
    ],
    'crust': 'gluten free',
    'address': '401 Somewhere St.',
    'note': 'Deliver to treehouse in back yard.'
}
```

There is actually a great deal going on here (including spoilers for later), but for now, just notice how our data can be structured in a very reasonable and readable way. This example isn't simplified, either – the above would not be surprising to see, exactly as-is, in an app taking orders for a real pizza parlour right now.

So we have a taste now of what data is, and what it looks like in Python.

### Types

Programming languages make the distinction between different data types. A data type is important because it lets us know what we can do with it. The sorts of things that we might want to do with a number are different from the sorts of things that we might want to do with a string of text.

For example, we might want to perform **multiplication** with a number. With a bit of text, we might want to convert it to **ALL UPPERCASE**. However, it's unclear what it would mean to divide the phrase `"Treehouse in the back yard"` by `3`, and similarly, the prospect of converting the number 128 to uppercase is... confusing.

For that reason, Python, like most programming languages, keeps data types neatly separated. We are going to talk about all data types and the sorts of things that we can do with them. In programming languages, there are many more data types than `numbers` and `strings`. Strings could be considered the most important data type (though this is not objectively true it can be an expedient way to start arguments with computer scientists!), so we'll start with strings first.

> #### Reflection Opportunity
> 
> Separating data and logic in a program is a fundamental concept in computer science, and it is often referred to as the "separation of concerns." This principle states that different parts of a program should be responsible for different tasks or concerns, and should not overlap or depend on one another.
> 
> In the context of data and logic, this means that the data should be separate from the code that manipulates it. This allows for better organization, readability, and maintainability of the code, as well as greater flexibility and reusability of the data.
> 
> Variable naming is an important aspect of this separation of concerns, as it helps to clearly identify the role of each variable and how it is used in the program. Clear, meaningful variable names can make it much easier to understand the intent of the code and how it works, especially when working with large or complex codebases.
> 
> For example, if a variable named `current_temp` is used in a program, it is clear that the variable stores some kind of temperature value. Similarly, if a variable named `customer_name` is used, it is clear that the variable stores a name of a customer.
> 
> By following these principles, we can make our code more readable, understandable and maintainable, which makes it easy for others to understand and collaborate on it, and also make it easy for ourselves when we come back to the code after a long time.
> 
> **What system or method can you develop for yourself to help implement best practices for variable naming so that the names are intuitive and easy to understand?**