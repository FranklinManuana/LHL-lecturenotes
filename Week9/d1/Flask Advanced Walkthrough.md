In the previous tutorial, we created a basic `Hello World` app in `Flask`. In this one, we're going to create a simple RESTful API with `Flask`.

Instruction

This time, we'll be working with a `.py` file instead of `.ipynb` file. So you can choose a `Python IDE` of your choice and create an empty file with the name `greeting_api.py`. You will be pasting the code from this tutorial there.

Our goal is to build an API that will greet the person who calls it.

Let's begin by importing the necessary libraries we'll need:

```python
# import Flask and jsonify
from flask import Flask, jsonify

# import Resource, Api and reqparser
from flask_restful import Resource, Api, request
```

Create an application:

```python
app = Flask(__name__)
```

Create an API from the application:

```python
api = Api(app)
```

Now that our API has been created, we need to add an endpoint. We can do that by creating a class with the name `Greet` (any other name will work as well). This class must inherit properties from the `Resources` class from the `flask_restful` module.

```python
class Greet(Resource):
    def get(self):

        name = request.args.get('name')

        if name:
            greeting = f'Hello {name}!'
        else:
            greeting = 'Hello person without name!'

        # make json from greeting string 
        return jsonify(greeting=greeting)
```

The class `Greet` contains only one method – `get`. This time the naming convention is strict (we can use only HTTP request methods: get, post, put, ...). Inside the `get` method, we initialize `RequestParser()` which allows us to parse optional arguments. We create only one optional argument `name` as a string type. In the variable `name`, we store an argument value that was passed by calling our API. If the user doesn't pass the argument `name` in an API call the value of the variable is `NULL`. We also create different greetings based on the value in the `name` variable.

Now that we have our class created, we need to assign an endpoint. The functionality of the `Greet` class will be available in the `/greet` endpoint.

```python
# assign endpoint
api.add_resource(Greet, '/greet',)
```

The last thing to do is to create an application run when the file `greeting_api.py` is called directly (not imported as a module from another script).

```python
if __name__ == '__main__':
    app.run(debug=True)
```

Now that we've created our API, it's time to test it.

Instruction

Run the API by opening the command line and type `python greeting_api.py`.

If there's no problem at all with our code, we will see the following in the command line:

```terminal
 * Serving Flask app "greeting_api" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 471-591-853
```

We can see that our API is running on our local machine at `http://127.0.0.1:5000/`.

To test it, let's open the browser and navigate to `http://127.0.0.1:5000/greet`. We should see in the browser something like this:

```python
{
  "greeting": "Hello person without name!"
}
```

If we want to pass a name to our API (in this case we pass "John" as a name) and show a personalized greeting, we can do this by navigating the browser to `http://127.0.0.1:5000/greet?name=John`. Now, we should see in the browser something like this:

```python
{
  "greeting": "Hello John!"
}
```

Instruction

Test your API by sending different requests from `Postman` as well.