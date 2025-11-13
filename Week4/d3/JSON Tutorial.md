In this activity, we will improve our skills in working with JSON files.

Let's start with the import of Pandas.

```python
import pandas as pd
```

Pandas has the function, `read_json()`, that can load JSON either from a file or a url.

```python
url = "http://api.open-notify.org/astros.json"
first_json = pd.read_json(url)
first_json.head()
```

Writing the JSON data is as simple as reading and is one line of code. Instead of `read_json()`, you will use `to_json()` with a filename and that's all!

```python
first_json.to_json('json_columns.json', orient="columns")
first_json.to_json('json_index.json', orient="index")
```

If the output directory is not specified `to_json()` stores the file **in the same directory** as our notebook. Find the two files there, check the two files and see the difference. These functions are the best option to deal with JSON. However, they don't always work.

Warning

`read_json()` and `to_json()` works only with simple JSON. All arrays inside need to have arrays of same length.

So what about the nested JSON files?

Instruction

Open the file [**nested.json**](https://drive.google.com/file/d/1PWg4uKcwO010y8MhnBIYAZbMi33vXOj7/view?usp=sharing) and take a look at its structure.

Then download it, and move it to the same directory where you are currently running this code.

Instruction

Try to load it into pandas with `pd.read_json()`

```python
df = pd.read_json("nested.json")
```

We can see that it doesn't work. Fortunately, we have another method. This is not a Pandas function but the method from package **JSON** which comes with core Python.

```python
import json
#load json object
with open('nested.json') as f:
    nested_json = json.load(f)
print(nested_json)
print(type(nested_json))
```

We can see that the file is automatically loaded as a Python dictionary.

Note

We can use package [pprint](https://pymotw.com/2/pprint/) for pretty printing dictionaries. This makes the human-parsing of json requests much easier to understand.

We will use a function from Pandas `json_normalize()`,

```python
pd.json_normalize(nested_json)
```

We can see from above that the primary keys are the columns of the DataFrame. We were able to load it as a Pandas DataFrame but it still looks weird.

We are going to add a parameter `record_path` to `json_normalize` to put a focus on a specific key from the file:

```python
blog = pd.json_normalize(nested_json,record_path ='blog')
blog.head()
```

and

```python
article = pd.json_normalize(nested_json,record_path ='article')
article.head()
```

`json_normalize()` has 3 main parameters:

1. **data** - input data
2. **record_path** - nested elements
3. **meta** - let them as they are elements

Instruction

Let's practice a bit more with `json_normalize()` on different data that are specified below

```python
# define json string
data = [{"state": "Florida", 
        "shortname": "FL",
        "info": {"governor": "Rick Scott"},
        "counties": [{"name": "Dade", "population": 12345},
                     {"name": "Broward", "population": 40000},
                     {"name": "Palm Beach", "population": 60000}]},
       {"state": "Ohio",
        "shortname": "OH",
        "info": {"governor": "John Kasich"},
        "counties": [{"name": "Summit", "population": 1234},
                     {"name": "Cuyahoga", "population": 1337}]}]
```

```python
pd.json_normalize(data)
pd.json_normalize(data=data, record_path='counties', meta=['state', 'shortname', ['info', 'governor']])
```