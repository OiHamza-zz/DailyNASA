BUILD A TWITTER NASA APP 🚀 🌎 ✨ 🌚
====

By [Hamza](https://twitter.com/oihamza) 👨🏽‍🚀


Once a day, NASA release an image or video through thier public API. I put together this automated Daily NASA app that Tweets media released by NASA. 

Our app will connect to the NASA API and temporarily store media provided, and post a Tweet with the title + image/video via the Twitter API. Pretty simple!

In this tutorial, I'll show you how to also build this app using the Twitter and NASA API. To see the app in action, check out the Twitter page [@DailyNASA](https://twitter.com/dailynasa). 


What will we be doing today?
------------

Our app is going to be hosted here on Glitch, so we won't be doing much except making sure our app is properly configured.

Once this project has been remixed and the `.env` file's keys and tokens properly configured, we'll schedule a cron-job to make our app Tweet. A cron-job is essentially an automated wake-up call.


How does the code work exactly?
------------

1. The app will be activated ~~woken up~~ via a webhook. The webhook will be pinged by our cron-job at a specified time of day ⏰
2. Our app will connect to the NASA API 🚀
3. The app will check if the media provided by the NASA API is a video URL or image URL:
  * If it's a **video** 📹, the app will save the video URL + title and Tweet this via the Twitter [statuses/update](https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/post-statuses-update) endpoint
  * If it's an **image** 📷, the app will save the image to a temporary directory and Tweet this via the Twitter [statuses/update](https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/post-statuses-update) API. Because it's a temporary directory, we don't have to worry about filling up space (pun intended) 🥁


Prerequisites
------------

Before we get started, you'll need the following:

  * A Twitter developer account - [click here](https://t.co/developeraccount) to apply
  
  * A registered [Twitter app](https://developer.twitter.com/en/apps) - [click here](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen%20Shot%202019-08-08%20at%205.20.15%20PM%20copy.png?v=1565299668056) to see how

  * A copy of your [Twitter API](https://developer.twitter.com/en/apps) keys and tokens - [click here](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen%20Shot%202019-08-08%20at%205.20.35%20PM%20copy.png?v=1565300041251) to see how
  
  * A NASA API key 🔑 - [click here](https://api.nasa.gov/#apply-for-an-api-key) to get one
  
  * A cron-job account - [click here](https://cron-job.org/en/signup/) to register


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

A) Enter your Twitter apps keys and tokens in the projects `.env` file

![Keys](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen1%20Shot%202019-08-08%20at%205.20.35%20PM%20copy.png?v=1565300721909)

B) Enter your NASA API Key on the projects `.env` file

C) Give your app endpoint a name 

For example, if I label mine `awaken`, my final endpoint will look like this: `https://daily-nasa.glitch.me/awaken`

🚨 IMPORTANT - keep all access keys, tokens, and endpoint names private 🚨

Step 3 - TESTING TESTING !!

Now you've configured our app, let's test it out.

I usually reccomend viewing the logs in Tools → Logs to verify our app runs when we wake it up. 

In a new browser window, enter your unique endpoint URL and hit enter. (You can also test the URL via your command line using the following command: `curl https://daily-nasa.glitch.me/awaken`

Give it a second, and on your Twitter account you should see the daily NASA Tweet posted!

Now you've verified that it works, let's make sure that it's automated so you don't have to keep doing this every single day.

Step 4 - ⏰ 

We'll be using [cron-job.org](https://cron-job.org/en/) to ping our endpoint and make our app post a daily Tweet.

Create a [new cron-job](https://cron-job.org/en/members/jobs/add/) and fill out the page to this effect:

![cron-job](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen%20Shot%202019-08-08%20at%206.13.22%20PM.png?v=1565302473410)

🚨 IMPORTANT - Scheduling your app to run too frequently can seem spammy and lead to violation of Twitters [automation policy](https://help.twitter.com/en/rules-and-policies/twitter-automation). 🚨

Once a job has run, you can view the response on [this page](https://cron-job.org/en/members/jobs/). 

And just like that, we're done!!!


Congratulations!
-------------------

You did it! 😎 Tweet me your Twitter app at [@oiHamza](https://twitter.com/oihamza), and let me know what other Twitter app tutorials you'd like to see.

