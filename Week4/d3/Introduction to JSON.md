Let's now learn about a new data type: **JSON**, what it looks like and what its advantages are.

JSON stands for JavaScript Object Notation. It became very popular with the increasing popularity of JavaScript because it represents the way objects are built in it. It is a "subset" of the JavaScript language.

Instruction

Read more about JSON structure in [this resource from W3 schools](https://www.w3schools.com/js/js_json_intro.asp).

When we create a data using the information from the previous article we will end up with an example of JSON:

![](https://i.imgur.com/ot8jP7H.png)

The name can be quite misleading since JSON is nowadays used not only in JavaScript. For example in data science, it has become a very popular way of storing our data. We can say that it is very similar to its predecessor, XML.

JSON is like XML because:

- Both are self-describing, meaning that the values are labeled, therefore 'human-readable'
- Both are hierarchical (nested), i.e. they can have values within values.
- Both can be parsed and used by lots of programming languages.
- Both can be passed around using HTTP request (important for APIs).

JSON is unlike XML because:

- JSON has a tag name only at the beginning of an element (no tag at the end of an element), which results in a smaller size.
- JSON is less verbose therefore quicker for humans to write and read.
- JSON can include arrays, which leads to even smaller file sizes.
- JSON can't use reserved words from JavaScript as tags.

## Conclusion

So now, you will recognize JSON when you see it, right? And you can see that it is very similar to the Python type `dict` which helps a lot when working with JSON in Python.