In this activity, we will continue developing our AI Literacy skills! We'll use AI tools to help learn about the structure of a JSON response.

It's important to note that the skills acquired here are not limited to handling requests. JSON is a commonly used format for storing data.

You will apply your understanding in the next assignment by loading data from JSON files.

## Learning Outcomes

- Become familiar with financial data in preparation for the next assignment
- Practice how to read and parse JSON data
- Use AI for redundant tasks
- Practice building queries to answer the questions from the Python dictionary converted from JSON
- Load and wrangle JSON files
- Convert JSON files to useful dataframes

## Activity

Make the following request:

```python
import requests
import pandas as pd
from pprint import pprint # this will display the data in a structured, more readable manner

params = {"page": 1}
response = requests.get("https://reqres.in/api/users", params=params)

data = response.json()
```

Instruction

Run the following two cells and compare how the output is displayed:

```python
print(data, "\n")
pprint(data)
```

Instruction

Use ChatGPT to answer the following questions:

- When I access the JSON method of the response, what form is the data in when I'm using Python?
- What is the dictionary structure of this response? _(Copy response printout from previous question)_
- What are some strategies for parsing JSON responses data to dataframes?

Note

Using `json_normalize` is **not recommended** for the next assignment. It can be extremely complicated if you don't understand how to access each part of a dictionary manually. A Pandas dataframe is basically just a Python dictionary. One of the easiest ways to create a dataframe is to create a dictionary where the dictionary keys are the column names and the dictionary values are lists of values for the columns. If a JSON file, or a dictionary that has been created from a JSON file doesn't have an obvious structure, then using `json_normalize` will not be straightforward, and you'll have to provide the record path and meta arguments. If you're a dictionary pro, then you can try using `json_normalize`, otherwise, looping through and accessing keys and values manually should be mastered first.

Data from this response and data from the next assignment cannot be automatically converted to a dataframe. You might expect this code to work:

```python
df = pd.DataFrame(data)
df
```

However, inputting the data in this and the next assignment won't result in what you expect.

Instruction

Prompt ChatGPT with the following:

Note

Note that once the "data" key has been accessed, you can automatically use `pd.DataFrame()`.

You'll need to iterate through the dictionaries in the next assignment.

```python
# Create a dataframe from the API response above with the following columns: ['avatar', 'email', 'first_name', 'id', 'last_name']
# create your dataframe here:

```

#### Key Questions

Here are some questions to help you with the next assignment:

- What are the common daily values for stock prices?
- How can I load a JSON file in Python?
- How does the keyword `with` work when opening a file?
- When should I stop indenting after the `with` keyword?
- What format is the loaded JSON once I use the `json.load()` function?

Instruction

Try answering these on using your own research methods, and then also ask an LLM tool. How do the results compare?