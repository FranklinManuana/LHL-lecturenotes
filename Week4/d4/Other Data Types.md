In this activity, we will practice our skills in working with different data types. By the end of this activity, it should be clear that Python is fully compatible with various data types.

```python
import pandas as pd
```

### XLSX

Pandas has a very simple way to deal with Excel files.

Instruction

Download [the test Excel file](https://drive.google.com/file/d/1x_HdaboZzRjFySMxpd768ZNjFrNGuoga/view?usp=sharing).

#### Reading

```python
df = pd.read_excel("test.xlsx", sheet_name = "months", engine='openpyxl')
df
```

#### Exporting

```python
df.to_excel("test2.xlsx", sheet_name="test")
```

### Text

Instruction

Download [this text file](https://drive.google.com/file/d/1-ozVnH1nFrIDt3jvz3kBrTICUCpH7wU3/view?usp=sharing).

We will load the `.txt` file directly with tools from standard Python:

```python
text_file = open("text.txt", "r")
text_file
text_file.read()
```

Instruction

Run `.read()` again

Warning

When you say `read` on a file object, you move the file pointer to the end, and hence your next calls to `read` would return empty.

You need to store the results into the variable:

```python
text_file = open("text.txt", "r")
text = text_file.read()
```

We can also read the first line only:

```python
text_file = open("text.txt", "r")
text_file.readline()
```

Instruction

Run `.readline()` twice more.

Note

After reading the first line, the file pointer was at the beginning of the second line. Our file consists of 2 lines. Therefore, after the second line loads, the pointer was at the end and the next read returned nothing.

We can load all the lines into a list:

```python
text_file = open("text.txt", "r")
text = text_file.readlines()
print(type(text))
```