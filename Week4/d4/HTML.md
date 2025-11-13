In this activity, we will learn how we can load HTML tables directly into Pandas, and learn the basics of web scraping which is a very popular way of data gathering.

If a webpage (HTML) has a table inside, we can easily extract it with `Pandas` and `requests`.

```python
import pandas as pd
import requests
import io 
```

We will work with the following URL [https://www.worldcoinindex.com/](https://www.worldcoinindex.com/)

Instruction

Visit the URL in a browser and explore the source code. See if there are any `<td>` tags.

Now, we will download the source code to Python.

```python
url = 'https://www.worldcoinindex.com/'
crypto_url = requests.get(url)
crypto_url
```

We will talk about these responses more shortly in the APIs section. For now, to take the main body of the URL's HTML, we need to take the attribute `text`.

```python
body = crypto_url.text
```

Body now consists of full HTML source code of our webpage. Now if the HTML source has a table which is marked by the HTML tag `<table></table>` (this tag is used for defining a table in HTML) `Pandas` uses `read_html()` to extract the table from the HTML document.

Warning

So, whenever you pass an HTML to pandas and expect it to output a nice looking data-frame, make sure the HTML page has a table in it!

```python
body = io.StringIO(body)
crypto_data = pd.read_html(body)
print(type(crypto_data))
print(len(crypto_data))
```

Note

In newer versions of Pandas (`>=2.1.0`), `pd.read_html()` expects a file-like object, rather than a string like the `.text` attribute of a request. This is why we include the line `body = io.StringIO(body)`. If you are using an older version of Pandas you can comment out or skip this line.

From the above output, it is clear that there is a `list` with one element which is our table. Therefore

```python
crypto_data = crypto_data[0]
crypto_data.head()
```

### What if there is no table in HTML?

If we want to extract information from HTML, which doesn't have a table, we need to use a different approach: **Scraping**. Fortunately, Python has a great package for this called `Beautiful Soup`.

Instruction

For a simple scraping tutorial, follow the [instructions in this resource from DataQuest](https://web.archive.org/web/20230204233808/https://www.dataquest.io/blog/web-scraping-python-using-beautiful-soup/).