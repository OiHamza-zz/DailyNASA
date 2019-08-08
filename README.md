BUILD A TWITTER NASA APP 🚀 🌎 ✨ 🌚
====


Once a day, NASA release an image or video through thier public API. I put together this Daily NASA app that Tweets media released by NASA. 

Our app will connect to the NASA API and temporarily store media provided, and post a Tweet with the title + image/video via the Twitter API.

In this tutorial, I'll show you how to also build this app using the Twitter and NASA API! To see the app in action, check out the Twitter page [@DailyNASA](https://twitter.com/dailynasa). 

By [Hamza](https://twitter.com/oihamza) 👨🏽‍🚀



What will we be doing today?
------------

Our app is going to be hosted (living) here on Glitch. Glitch is a simple and powerful free tool to create, share, and use apps. 
Once we've configured our app, we'll set up a cron-job (daily call) using a callback URL to the endpoint which will wake up our app and make it post a Tweet at a specified time of day.

An endpoint is a URL (like twitter.com), and whenever we submit a GET request we're asking the internet to go *get* this website for us. Once we've got the website, the app will wake up and do its job.





How does the app work exactly?
------------

Our app will 
On a very high level:

our app will connect to the NASA API → <br>
The app will check if the media provided by the NASA API is a video URL or image URL → <br>
→ If it's a video, the app will save the video URL + title and Tweet this via the Twitter [statuses/update](https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/post-statuses-update) API <br>
→ If it's an image, the app will save the image to a temporary directory and Tweet this via the Twitter [statuses/update](https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/post-statuses-update) API. Because it's a temporary directory, we don't have to worry about filling up space (pun intended).
→ Our app will be activated (woken up) by a webhook, and only Tweet when that webhook is pinged. This lets you Tweet at specific times of day. We'll use cron-job.org to set up a cron job that basically pings the URL at specific times that we specify
→ To wake Bert up and let him know it's time to get to work, we'll use an endpoint and a cron-job service to set an alarm for him to get up and start working. 


Prerequisites:
------------

A Twitter developer account - link to DTC developer application page
A registered app - link to DTC apps page 
Collect your keys and tokens from your registered app - link to docs that shows how to get keys and tokens 
A NASA API key 🔑 - link

Once you have all of these, you're ready to launch 🚀!


Recipe
-------------------

Step 1 - 💿

a) Remix this app! 

![Remix](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen%20Shot%202019-08-08%20at%203.54.26%20PM.png?v=1565294080315)


b) Name your app! 

I called mine  `daily-nasa`

![Name](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen%20Shot%202019-08-08%20at%203.57.37%20PM.png?v=1565294269445)


Step 2 - 🔑

A) Using your Twitter keys and tokens, enter them into the .env file 

Image of DTC Apps page
Image of .ENV page with keys and tokens

B) Enter your NASA API Key

Image of NASA API page 
Image of .ENV page with API key

C) Choose your app endpoint name 

For example, if I call mine wakeupapp, my final endpoint will look like this:

https://my-twitter-nasa.glitch.me/wakeupapp

IMPORTANT :alert: - keep your webhook information private. If your webhook information is public, people who ping it will wake your app (and get it to tweet without your knowledge)

Step 3 - TESTING TESTING !!

Now you've configured your app, let's test it out. You can use either of the following ways to check if the endpoint works properly:

option 1 - in a new browser window, enter your URL and hit return/enter. Give it a second.

or 

option 2 - on your command line, enter the following command: `curl {example-url}`

Check your Twitter account to see that the Tweet posted! Try not to keep hitting the URL and posting the same image/title too frequently as it can lead to rate limiting from the API and might be detected as spam by Twitter. 

Now you've verified that it works, let's make sure that it's automated so you don't have to keep doing this every single day.

Step 4 - Wake me up, before I go Go! 

In this example, we'll be using cron-job.org to ping our endpoint and make our app post a daily Tweet. 

a - go onto crong-job (url) and create a free account. Select create cronjobs on this page. 

Fill out the page to this effect:

IMAGE 

I like to save the responses of the cronjob to make sure that I can see what happens.
 
And just like that, we're done!!!


Congratulations!
-------------------

You did it! 😎 Tweet me your Twitter app at [@oiHamza](https://twitter.com/oihamza), and let me know what other Twitter app tutorials you'd like to see.

