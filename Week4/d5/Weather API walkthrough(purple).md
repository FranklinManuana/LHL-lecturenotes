## World Weather Online API

We will introduce an API which we can use to obtain weather information, both historical and predictions. The data collected from this API will be used during upcoming activities. In those activities, we will provide you with the data, but this stretch activity is an opportunity for you to get a litte more practice workign with APIs.

Instruction

Create a free account for the [**World Weather Online API**](https://www.worldweatheronline.com/developer/api/historical-weather-api.aspx).

Warning

The API is free for the **first 30 days** and we will get 500 free requests per day.

Once you are logged in you will see a home page similar to this:

![](https://i.postimg.cc/RVzPw0Wh/Screenshot-2021-01-05-at-13-51-57.png)

Let's break this down:

1. Your **secret** API key – make sure to keep it safe. It works as an authentification against their server and date when your trial ends.
2. Number of free requests per day.

Instruction

Read through the [**Historical Weather API Documentation**](https://www.worldweatheronline.com/developer/api/docs/historical-weather-api.aspx).

Now we can return to Postman and test the API.

Instruction

Let's get a Christmas 2020 weather for Vancouver (lon=-122.6615; lat=45.6387):

According to the documentation, this is how we construct our URL:

- base_url = `https://api.worldweatheronline.com/premium/v1/past-weather.ashx`
- location = `q=45.6387,-122.6615`
- date = `date=2020-12-24`
- format (optional) = `format=json`
- key = `key=<your api key>`

Using the parameters the final URL is:

`https://api.worldweatheronline.com/premium/v1/past-weather.ashx?q=45.6387,-122.6615&date=2020-12-24&format=json&key=<your api key>`

Instruction

Use Postman to send the GET request to the API and obtain the weather information.

![](https://i.postimg.cc/JzyGmjLd/Screenshot-2021-01-05-at-15-00-25.png)

We can see that Postman automatically recognized the different parameters we used in the URL.
