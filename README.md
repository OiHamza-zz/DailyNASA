Build a Twitter NASA app 🚀 
====
A Twitter bot that Tweets Daily Images provided by NASA's API

By [Hamza](https://twitter.com/oihamza) 👨🏽‍🚀

###### This project is hosted on Glitch: https://glitch.com/~dailynasa

Once a day, NASA features an astronomy or space science related image through their public API. The images are pretty cool and teach you about the incredible solar system we live in!  

As an astronomy enthusiast, I wondered how I could easily view these images and even get them to appear on my Twitter timeline. I got to work on this, and ended up putting together this fully automated Daily NASA app that Tweets images released each day by NASA.

Our node.js app will connect to the NASA API, temporarily store media provided and post a Tweet with the title + image/video via the Twitter API. Here is an [example](https://twitter.com/DailyNASA/status/1161986403653292035). Pretty simple!

In this tutorial, I'll also show you how to build this app using the Twitter and NASA APIs. To see the app in action, check out the Twitter page [@DailyNASA](https://twitter.com/dailynasa). 


What will we be doing today?
------------

Our app is going to be hosted on [Glitch](https://glitch.com/~dailynasa), so we won't be doing much except making sure our app is properly configured.

Once our project has been remixed and the `.env` file's keys and tokens properly configured, we'll schedule a cron-job to make our app Tweet. A cron-job is essentially an automated wake-up call.


How does the code work exactly?
------------

1. The app will be activated via a webhook. The webhook will be pinged by our cron-job at a specified time of day ⏰
2. Our app will connect to the NASA API 🚀
3. The app will check if the media provided by the NASA API is an image URL or video URL. If it’s a photo, our app will download the image and Tweet it. If it’s a video, the app will just Tweet the video URL:
  * **Video** 📹 - the app will save the video URL + title and Tweet this via the Twitter [statuses/update](https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/post-statuses-update) endpoint.  Here’s an [example](https://twitter.com/DailyNASA/status/1151477103306649604).
  * **Image** 📷 - the app will save the image to a temporary directory and Tweet this via the Twitter [statuses/update](https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/post-statuses-update) endpoint. Here’s an [example](https://twitter.com/DailyNASA/status/1161986403653292035). Because it's a temporary directory, we don't have to worry about filling up space (pun intended) 🥁



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

a) On our [Glitch project page](https://glitch.com/~dailynasa), remix this project! Click on the "Remix Project" button on the top left of this page.

![Remix](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen%20Shot%202019-08-08%20at%203.54.26%20PM.png?v=1565294080315)


b) Name your app.

I called mine  `dailynasa`

![Name](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen%20Shot%202019-08-08%20at%203.57.37%20PM.png?v=1565294269445)


Step 2 - 🔑

A) Enter your Twitter apps keys and tokens in the projects `.env` file

![Keys](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen1%20Shot%202019-08-08%20at%205.20.35%20PM%20copy.png?v=1565300721909)

B) Enter your NASA API Key on the projects `.env` file

C) Give your app endpoint a name 

For example, if I label mine `wakeup`, your `.env` file should look like this: `BOT_ENDPOINT='awaken'`. My final endpoint will look like this: `https://dailynasa.glitch.me/wakeup`

🚨 IMPORTANT - keep all access keys, tokens, and endpoint names private 🚨

Step 3 - TESTING TESTING !!

Now you've configured our app, let's test it out.

I usually reccomend viewing the logs in Tools → Logs to verify our app runs when we wake it up. 

In a new browser window, enter your unique endpoint URL and hit enter. (You can also test the URL via your command line using the following command: `curl https://dailynasa.glitch.me/wakeup`

Give it a second, and on your Twitter account you should see the daily NASA Tweet posted!

Now you've verified that it works, let's make sure that it's automated so you don't have to keep doing this every single day.

Step 4 - ⏰ 

We'll be using [cron-job.org](https://cron-job.org/en/) to ping our endpoint and make our app post a daily Tweet.

Create a [new cron-job](https://cron-job.org/en/members/jobs/add/) and fill out the page to this effect:

![cron-job](https://cdn.glitch.com/40a2e399-2bcb-4c11-b356-fdb1d9baa5e9%2FScreen%20Shot%202019-08-08%20at%206.13.22%20PM.png?v=1565302473410)

🚨 IMPORTANT - scheduling your app to run too frequently can seem spammy and lead to violation of Twitters [automation policy](https://help.twitter.com/en/rules-and-policies/twitter-automation). 🚨

Once a job has run, you can view the response on [this page](https://cron-job.org/en/members/jobs/). 

And just like that, we're done!


Congratulations!
-------------------

You did it! 😎 

If you enjoy learning from tutorials or have any questions, check out [Twitter’s Community Forums](https://twittercommunity.com/).
