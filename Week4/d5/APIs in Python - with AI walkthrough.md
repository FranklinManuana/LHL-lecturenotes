In this activity, you will continue practicing Python. But this time with some help from AI!

Before we dive in, let's cover some key best practices of using AI while learning. AI can certainly be a useful tool, but must be approached with caution.

Note

It's best to approach AI tools with a "learning first" attitude.

Yes, you might be able to generate code faster, but you're also responsible for _understanding_ everything that it gives you.

For example, say you use AI to generate very large blocks or entire assignments of code. Not only will it be very obvious, but your own coding skills won't develop or improve.

**Tips:**

- break your problem down into the smallest pieces that you can
- ask specific questions
- prompt the tool further if you don't understand something

Instruction

Read the following article about [how AI can be used to help you learn coding](https://www.codecademy.com/resources/blog/can-chatgpt-ai-teach-you-to-code/) and focus on its limitations.

## Learning Outcomes

- Use AI to help you learn how to code
- Practice building a GET request
- Practice adding arguments to a GET request
- Practice parsing a URL or use a parameter dictionary for the request

## Activity

In this activity you will learn how to use the Python requests library to make a GET request.

We'll provide you with suggested questions you can use to research with an AI tool. Use these questions to build your understanding of the concepts in this activity.

Instruction

Use ChatGPT to answer the following questions:

- What are the most common methods of the requests library?
- What are the attributes of a response?
- What is the most common form of a response?
- How can I make a request to the following endpoint, without using a parameter dictionary, and check that it worked properly? [https://reqres.in/api/users?page=1](https://reqres.in/api/users?page=1)

Instruction

Make a GET request to the user's endpoint with the URL from above.

```python
import requests

# make GET request here, replace None with the code for the request:

response = None

# check that the request was successful here:

# print the actual data from the response here:

```

Instruction

More questions you can use with ChatGPT:

- What other information can I obtain from the user's endpoint?
- How are arguments typically used in a GET request string?
- What's the difference between using a string and a parameter dictionary for passing arguments?

Instruction

Verify that this GET request returns the same information as the request you wrote from above:

```python
params = {"page": 1}
response = requests.get("https://reqres.in/api/users", params=params)

# print the response here and compare it with the response from above
```

```python
response.json()
```

## Conclusion

Not only did we practice making GET requests, but you also used AI to help your learning process.

It's important to approach AI tools with a "learning first" attitude, using them to enhance your understanding and coding skills rather than relying on them to do your work.