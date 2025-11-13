We will now practice accessing different APIs using Python. The goal is to see how this particular communication works.

The library we use for sending various requests from Python is called `requests`. First of all, we need to import it to our notebook:

```python
import requests
import os
```

The `os` package is used to access the values of environment variables.

Let's start with our well-known _Foursquare Places API_.

Instruction

Collect the venues near Toronto, Canada. (Try to do this on your own before you look at the instructions below).

#### Step 1

Load the FOURSQUARE API credentials into Python

Warning

Be careful and **don't** store your API keys, or any passwords in general, inside your code. We often push it to GitHub to public repositories where anyone could see it. It's a good practice to keep them stored in the environment variables as we saw earlier.

Previously, we learned how to create our own environment variables. Now, we are going to see how we can load the values of these variables to Python.

```python
api_key = os.environ["<variable_name>"]
# os.environ loads the dictionary with environment variables where os.environ.keys() are all variable names
```

Warning

You have to start Jupyter Lab from the environment where environment variables were created. The other option is to create them permanently but, in that case, don't forget to restart Terminal.

Now, we can assign variables `location`.

```python
location = "Toronto,Canada"
```

#### Step 2

Prepare the url for the API:

```python
url = "https://api.foursquare.com/v3/places/search?near=" + location
```

#### Step 3

Prepare a dictionary that can be sent as _headers_ of our request. This `Accept: application/json` header is asking the API to send us data in JSON format if it is able.

```python
# Create dictionary for headers
headers = {"Accept": "application/json"}
# Add key with our API KEY
headers['Authorization'] = api_key
```

#### Step 4

Send the request to Foursquare:

```python
result = requests.get(url, headers=headers)
```

#### Step 5

The request will return an object with the result inside. When you print the object, you will see the following:

![](https://i.imgur.com/dcYM0DN.png)

200 means success but more about that later on :)

#### Step 6

If we want to see the actual data, we need to access it using the method `.json()` The `.json()` method attempts to parse data in JSON format in the response object into python lists and dictionaries.

```python
print(result.json())
```

It looks a bit messy, right? The format of the data is **JSON** and we will learn what to do with that later in the following activities. For now, it's important that we are able to communicate with APIs using Python.

## Conclusion

These were the basics of how to send requests to APIs. However, Python is very popular so, for common APIs, there often exist specific Python packages. Real Python has put together [a list of Python API Wrappers](https://github.com/realpython/list-of-python-api-wrappers) that is worth bookmarking for future reference.

