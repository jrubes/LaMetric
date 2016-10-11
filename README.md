# Sonos Display Now Playing on LaMetric

This is a SmartThings SmartApp that enables the ability to display what is currently Now Playing on a specified Sonos speaker on your LaMetric Clock (www.lametric.com). With that in mind, it should be obvious that you A) Have SmartThings in your household and B) Already connected your Sonos speakers to your SmartThings hub.

This guide is under the assumption that you have created a developer account for both LaMetric and SmartThings. If you have not, then please do so before continuing. It is free after all :)

SmartThings Developer Site: https://graph.api.smartthings.com/register

LaMetric Developer Site: https://developer.lametric.com

#Step 1 - Create LaMetric Indicator App

Log in to LaMetric Developer Portal and create your app:

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-1.png)

Click on Indicator App

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-2.png)

#Step 2 - Choose Icon and Default Text

Click on Select Icon:

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-3.png)

Now search for an icon you want to display for the app. I like to use #2020 Music Note Orange Big (Pay attention to the icon ID number, you will need it later).

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-4.png)

With your icon selected, now give your app the default text. I choose " Now Playing" (no quotes) as my default text. I also like to have a leading space before the word "Now" because it tends to look cramped placed directly next to the icon, but your preference may vary.

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-5.png)

#Step 3 - Create Push Communication Type and Take Action on Button Push

Now scroll down and select "Push" for the Communication Type. You will see the URL for pushing data populate in the screen:

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-6.png)

Scroll down further and you will see your sample Push Requst along with your Access-Token. This token is critical so take note of it.

OPTIONAL: If you want to have the action button on the LaMetric display be able to trigger between Pause/Playing, then check the box for "Take action when user clicks action button"

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-7.png)

#NOW HOLD HERE, DON'T CLICK ANYTHING YET AND MOVE ONTO NEXT STEP

#Step 4 - SmartThings SmartApp Install

Now, open a new we browser tab and log into your SmartThings Developer Portal and go to "My SmartApps" at the top, and click on "+New SmartApp"

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-8.png)

Click on "From Code"

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-9.png)

Paste in the code from https://github.com/jrubes/LaMetric/blob/master/SmartApp/sonos-lametric.groovy and click "Create" at the bottom.

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-10.png)

#Step 5 - Enable OAuth on SmartApp for Button Action

Once the SmartApp is created, click on "App Settings" so we can get to the OAuth settings.

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-11.png)

Towards the bottom, click on OAuth

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-12.png)

Then click on Enable OAuth in Smart App

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-14.png)

Once enabled, click on "Update"

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-15.png)

After it updates, click on the "Code" again in the top right corner to get back to the code in the IDE

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-32.png)

Then click on "Publish" -> "For Me"

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-16.png)

#Step 6 - Install SmartApp in SmartThings

Now that you have published the app, open up the SmartThings App on your phone. The example here is with the Android App, but you can do the same with the iOS app as well.

Once opened, go to "Marketplace" -> "SmartApps" -> + "My Apps"

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-17.png)

Click on the "Display Sonos Now Playing on LaMetric Display" SmartApp that you just installed.

You should now see the following screen (Fields with red to the side are required):

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-18.png)

Now choose which Sonos speaker you want to display the Now Playing info from

#Go back to your other web browser tab at the LaMetric Developer Portal for the remaining info

Now back at the LaMetric Developer Portal on your app, copy the URL for pushing data into the Push URL on your SmartApp. THIS IS CASE SENSITIVE so I recommend you email it to yourself or use something like Pushbullet to copy and paste between devices. 

Pay attention to the screenshot COPY EVERYTHING UP TO THE "/1" at the very end (no quotes). This will ensure that your app will receive the push data in the event you ever update your LaMetric app with a new version. (This will push to all versions of the app)

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-19.png)

After you have copied over your Push URL info, now copy the Access-Token from the Sample Push Request at the bottom. COPY EVERYTHING UP TO THE QUOTE (INCLUDING THE DOUBLE ==) This is your Access-Token for your LaMetric device. Paste this token into your SmartApp exactly as it is into the Access Token field of the SmartApp. This IS CASE SENSITIVE.

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-20.png)

Now copy the Icon ID from the sample Data Format into the Icon ID field of the SmartApp. NOTE: ONLY COPY THE NUMBERS, not the leading "i".

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-21.png)

Your SmartApp should look like the following:

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-22.png)

Now back at the SmartApp, scroll down and enter your Cell phone number so that the app can text you the LaMetric Action Button URL. It will come in 2 text messages because it is too long for 1. (This is ONLY for sending you the button action access URL and is only between you and SmartThings, NO ONE HAS ACCESS TO THIS NUMBER)

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-23.png)

Once all of the info is entered, click on "Done" and you will receive the SMS messages with the action URL.

#Step 7 - Add the Action Button URL to LaMetric App

Now that your SmartApp is installed and you have the URL for triggering Pause/Play, head back to your LaMetric Developer Portal browser tab, ensure the "Take action when user clicks action button" is checked, paste the entire URL (both parts) into the field and click "Next":

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-24.png)

#Step 8 - App Store Info

Give your LaMetric app a name. I recommend you name it "Sonos Now Playing - SPEAKER NAME" because in the event you have multiple LaMetric or Sonos speakers, you can repeat all of these steps and create multiple apps, each one displaying the information for the respective speaker.

Now give it a short description and MAKE SURE YOU HAVE PRIVATE APP CHECKED, and click Save:

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-25.png)

#Step 9 - Final Verification and Publish

After you click save, you will be at the following scren to verify your app and make sure everything looks good before you publish it.

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-26.png)

Scroll down and make sure your Action Button URL looks good to go as well.

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-27.png)

If everything looks good, then scroll up and click on "Publish"

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-28.png)

Now wait here until you get the confirmation email from LaMetric that your app is successfully published and released to the store. The system is VERY quick and only takes a couple of minutes (most I had to wait was 5 minutes once).

Once you have received the email, proceed to Step 10.

#Step 10 - Install LaMetric App

Open your LaMetric App on your phone and scroll down to add a new app

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-29.png)

Scroll over to "Private" app section and select your newly created LaMetric App. (Note, the following is just an example, yours will look different and probably have a different name)

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-33.png)

Click on your app and then click on add to install it

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-30.png)

Once installed, you can click on the app to have it notify when the song changes (I like to have this checked, you may prefer otherwise, play with whatever settings that suit you best).

![alt-tag](https://raw.githubusercontent.com/jrubes/LaMetric/screenshots/screenshots/Lametric-31.png)

And you're done! If you followed everything properly, your LaMetric will now display the currently playing track on your Sonos speaker.

#THINGS TO NOTE

Some caveats: This app will ONLY display the information that is being reported to SmartThings. I have noticed in my time building this that SmartThings is not real-time when it comes to refreshing the Now Playing information from Sonos.

To get around this, I have also included in this repo another SmartApp called "Pollster" that will manually refresh the information from Sonos. I have modified this version to refresh every six seconds instead of its original 60 seconds. I very much recommend that you install this SmartApp as well and have it refresh your Sonos speaker so your LaMetric is always up to date.

The Pollster app is located at https://github.com/jrubes/LaMetric/blob/master/SmartApp/pollster.groovy

All credit goes to Statusbits for this Pollster app.

Also, if you have multiple Sonos Speakers and/or multiple LaMetric Devices and want to run multiple instances of this app: 

Just create another Indicator App with the name of your second speaker (it will have a new Push URL) and install another instance of the SmartApp with this new Push URL.

You do NOT need to install the SmartApp again in the SmartThings developer console. Just go to the marketplace and install another instance of the same SmartApp as before. This instance will have its own Access-Token to be used for that speaker button action. 

You will now see multiple LaMetric Apps in your Private section of the store to each of your speakers.

#Good Luck!
