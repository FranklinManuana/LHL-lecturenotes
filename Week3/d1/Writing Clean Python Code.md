## Writing Clean Python Code

Writing clean, understandable, and maintainable code is a skill that is crucial to master.

**_But what is clean code?_**

Clean code is a set of rules and principles that helps to keep our code readable, maintainable, and extendable. It's one of the most important aspects of writing quality code.

Writing and keeping your code clean has many benefits including:

- Your code will stand the test of time. When you revisit your code in 2 months, will you be able to understand your thought process and why you made the decisions you made? Writing clean code is in your best interest as the writer of the code.
- Your code will be more efficient.
- Other will find it easier to understand your code.
- It will be easier to maintain, scale, debug, and refactor.

Outlined below are some best practices that will help guide you in writing clean code.

### Variable Naming

There are several things to keep in mind when naming variables.

#### Avoid comments as explanations for variable names

Do not use comments to explain why a variable is used. If a name requires a comment, then you should take your time to rename that variable instead of writing a comment.

```python
# This is bad 
# represents the number of active users 
au = 55

# This is good 
active_user_amount = 55
```

#### Use descriptive/intention-revealing names

```python
# This is bad
c = 5 
d = 12 

# This is good
city_counter = 5 
elapsed_time_in_days = 12
```

#### Use pronounceable names

You should always use pronounceable names; otherwise, you'll have a hard time explaining your algorithms out loud.

```python
from datetime import datetime 

# This is bad 
genyyyymmddhhmmss = datetime.strptime('04/27/95 07:14:22', '%m/%d/%y %H:%M:%S') 

# This is good 
generation_datetime = datetime.strptime('04/27/95 07:14:22', '%m/%d/%y %H:%M:%S')
```

#### Avoid using ambiguous abbreviations

```python
# This is bad 
fna = 'Bob' 
cre_tmstp = 1621535852 

# This is good 
first_name = 'Bob'
creation_timestamp = 1621535852
```

#### Use consistent naming

```python
# This is bad 
client_first_name = 'Bob' 
customer_last_name = 'Smith' 

# This is good 
client_first_name = 'Bob' 
client_last_name = 'Smith'
```

Note that in the above example, there is no reason to use both client and customer.

#### No magic numbers

Magic numbers are strange numbers that appear in code, which do not have a clear meaning. Let's take a look at an example:

```python
import random 

# This is bad 
def roll(): 
  return random.randint(0, 36) 
# what is 36 supposed to represent? 

# This is good 
ROULETTE_POCKET_COUNT = 36 
def roll(): 
  return random.randint(0, ROULETTE_POCKET_COUNT)
```

Instead of using magic numbers, we can extract them into a meaningful variable.

### Writing Functions

There are several best practices that can be followed when writing functions.

#### Don't repeat yourself

Code repetition may be the root of all problems in coding. Duplicate code means you need to change things in multiple places when there is a change in logic and it is very error-prone.

Instead of repeating your code, you should put the code inside a function, and call the function instead.

#### Create single function functions

Your functions should do only one thing. The thing that function does should be stated in its name.

```python
# This is bad 
def fetch_and_display_personnel(): 
  data = # code to extract the data
  for person in data: 
    print(person) 

# This is good 
def fetch_personnel(): 
  data = # code to extract the data
  return data

def display_personnel(data): 
  for personin data: 
    print(person)
```

## Conclusion

There are quite a few best practices to keep in mind as you code. Remember that with time and practice these things will become second nature to you. It might be a good idea to keep a check list of the above best practices to reference as you start on your coding journey!