The goal of this activity is to revisit environment variables to remind us of what they are and how we use them in APIs.

We first explored environment variables when we covered [virtual environments.](https://web.compass.lighthouselabs.ca/c0925771-f4c6-41d2-b608-c0bad7efb4fe)

Instruction

In case you need a refresher, take a moment to review the article [**What are environment variables in Bash?**](https://opensource.com/article/19/8/what-are-environment-variables)

Previously, in the [API Examples activity](https://web.compass.lighthouselabs.ca/50f7be5e-ecec-450f-8e2f-1ea64cf76ed0), we worked with `API-KEYs (access tokens)`. It is very important to keep these safe because they can be easily misused.

Imagine that you pay **0.01$** per API request. If someone gets access to your `API-KEY`, it will be very easy for them to use it. We must store the keys somewhere, where we can access them from different tools but they won't be shared when we push our code to GitHub or send it by e-mail. At this point, surely you guessed right, an environment variable is such a place.

Instruction

Let's get a venues for Vancouver(lon=-122.6615; lat=45.6387) using `curl`:

**Linux and Mac:**

Open your **Terminal** and use the command below.

**Windows:**

Open your **Bash On Windows** we set up in the activity [Bash](https://web.compass.lighthouselabs.ca/c4123025-556c-454d-9a2c-0842250ff873) and use the command below.

```shell
curl --request GET \
     --url "https://api.foursquare.com/v3/places/search?ll=45.6387,-122.6615&radius=100" \
     --header 'Accept: application/json' \
     --header 'Authorization: your_api_key'
```

We can see that we put our `API_KEY` as `Authorization` into the command. Therefore, once we push this code to Github, everyone who has an access to the repository could see it. **Environment variable should be used to avoid this**.

Instruction

Create an environment variables `FOURSQUARE_API_KEY` with the value from your key (without <>):

```shell
export FOURSQUARE_API_KEY=<your_api_key>
```

Note

In **Windows**, `export` will create environment variables in our Linux subsystem. If we want to create and edit them in Windows we can follow [this thread](https://superuser.com/questions/949560/how-do-i-set-system-environment-variables-in-windows-10). We will need this once we use them directly inside the Jupyter or Python.

Instruction

Now, let's run the same request but instead of the value of your key, type the name of the variable:

```shell
curl --request GET \
     --url "https://api.foursquare.com/v3/places/search?ll=45.6387,-122.6615&radius=100" \
     --header 'Accept: application/json' \
     --header 'Authorization: '"$FOURSQUARE_API_KEY"''
```

Warning

Notice quotes `'"` and `"'` around the environment variable. If we don't use `'"` around the name $FOURSQUARE_API_KEY it will use the variable name as API key and not the actual contents of that variable.

Now, when you push this code to GitHub, the key will be safely stored on your local machine.

Warning

When the command `export` is used in Terminal the variable will be created **only in local** Terminal session.

**Linux and Mac:**

Check out [this article](https://www.sudhanshutheone.com/posts/environment-variables-mac) to create permanent environment variables in Mac or Linux. The **option 1** should be sufficient. The name of the file from the article, `.bash_profile`, may be different in various linux distributions.

**Windows:**

We can follow [this guide](https://docs.oracle.com/en/database/oracle/machine-learning/oml4r/1.5.1/oread/creating-and-modifying-environment-variables-on-windows.html) to manage permanent environment variables in Windows.

> #### Reflection Opportunity
> 
> Have you wondered why you should go through all the trouble learning about environment variables?
> 
> Environment variables are a commonly used tool for storing sensitive information, such as credentials and API keys, in a secure manner. They are stored outside of the codebase, usually in the server's environment, and can be referenced in the code as needed. This helps to prevent sensitive information from being accidentally leaked or exposed in the event of a codebase breach.
> 
> However, proper security measures must be taken to ensure that the environment variables are secure. This may include implementing proper access controls, encryption, and monitoring for unauthorized access. Additionally, it's important to keep the environment variables updated and to rotate them regularly to minimize the risk of exposure.
> 
> **What process can you implement in your workflow to ensure your environment variables are updated and rotated at an appropriate frequency?**