The goal of this activity is to walk through some APIs and explore how they work and what results they return.

### GitHub API

We will be working with GitHub user's API with your own username.

#### Web Browser

Instruction

Type the following link into your web browser:

`https://api.github.com/users/<your_user_name>`

We sent the string to the GitHub server and information about the user was returned in JSON format.

We can say that our web browser "asked" for the information and GitHub sent the reply.

#### Postman

However, we can also ask for the same information using different tools. One of the most often used tools to test APIs is [**Postman**](https://www.getpostman.com/product/api-client).

Instruction

Download [**Postman**](https://www.getpostman.com/downloads/).

Once you start the application, it will look like this:

![](https://i.imgur.com/RIo3wJJ.png)

Instruction

By clicking `Create a request` on the launch pad, you will open a new tab where you can send requests to different APIs.

![](https://i.imgur.com/Fy1uAhN.png)

Instruction

Enter the URL from the previous example: `https://api.github.com/users/<your_user_name>` and press send.

You will see the same response as in the browser before.

#### Terminal

We can work similarly inside the terminal using the `curl` command. This command sends requests to the specified URLs.

Instruction

Open the terminal and type the following command:

```shell
curl https://api.github.com/users/<your_user_name>
```

Again, the same output will be displayed but this time inside the terminal.

### Foursquare API

Now we are going to look at one more API which can be very useful and will be used in a few other activities: **Foursquare Places API**.

Since we've already registered for _Foursquare Places API_, we should have our Client ID and Client Secret ready. We will be using them as our unique identification when using the API. If we don't have those we need to go back to the [Foursquare API Registration activity](https://web.compass.lighthouselabs.ca/ac20fb6c-8bd2-4bf0-acf8-35941160ca94).

Warning

Our account has only 40000 calls per month for free [(200$ in credits)](https://foursquare.com/products/pricing/). We need to make sure we use them wisely so we don't run out of requests.

Instruction

Skim through the [**Foursquare Places API Documentation**](https://developer.foursquare.com/reference/place-search). We don't have to read everything of course. We will be coming back to the documentation when working with the API.

Now we can return to Postman and test the API.

Instruction

Let's get a venues for Vancouver(lon=-122.6615; lat=45.6387):

Our URL will look like this: `https://api.foursquare.com/v3/places/search?ll=45.6387,-122.6615&radius=100`. Furthermore, we have to specify our API Key inside the **Headers** using **Key** `Authorization` and API Key as **Value**.

![](https://i.postimg.cc/JzNpsBpp/Screenshot-2021-12-01-at-14-18-06.png)

When we click **Send** we will see the response in the JSON format.

---