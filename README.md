# dialogflow-ifttt-webhooks-smartlight-chatbot
Build a chatbot using Dialogflow, Webhooks, and IFTTT to control your smart light bulb. For this project, I'll be integrating it with telegram.

# 1. Dialogflow

###   1.1 Go to https://dialogflow.cloud.google.com/ and sign in using your Google account
###   1.2 Create an Agent (chatbot)
Go to the dropdown menu on the top-lefthand corner and select "Create new agent"
###   1.3 Create an Intent
- We'll be needing 3 intents for this project

![](https://github.com/rainyraina/dialogflow_ifttt_webhooks_smartlight/blob/master/github_photos/intents.PNG)
1. **Click "CREATE INTENT" and change the title to "lights"**
* Training Phrases : "/lights"

![](https://github.com/rainyraina/dialogflow-ifttt-webhooks-smartlight-chatbot/blob/master/github_photos/trainingphrases.PNG)
* Responses: Click on "+" and select Telegram. 
* "ADD RESPONSES", select "Quick Replies"
* Quick replies title: "On/Off lights?"
* Button titles: "On", "Off"

![](https://github.com/rainyraina/dialogflow-ifttt-webhooks-smartlight-chatbot/blob/master/github_photos/lightqr.PNG)



* Save and go back to Intents page
2. **Hover over the "lights" intent and select "Add follow-up intent"**
* Ensure that you add "lights-followup" as the input and output context

![](https://github.com/rainyraina/dialogflow-ifttt-webhooks-smartlight-chatbot/blob/master/github_photos/context.PNG)

* Change the title to "lights - on"
* Training Phrases: "On"
* Quick replies title:  "Switching on the lights..."
* Button titles: "Off"

![](https://github.com/rainyraina/dialogflow-ifttt-webhooks-smartlight-chatbot/blob/master/github_photos/quickreplies.PNG)

* Fulfillment: "Enable webhook call for this intent"

![](https://github.com/rainyraina/dialogflow_ifttt_webhooks_smartlight/blob/master/github_photos/enable_webhook.PNG)
* Repeat the steps for "lights - off"
3. **Telegram Integrations**
* Go to Integrations page
* Enable Telegram; Get a Telegram access token from BotFather and insert it in the ‘Telegram Token’ field.
* You should be able to start your Telegram bot

# 2.  IFTTT applet
### 1.1 Sign in to https://ifttt.com/
### 1.2 Create an applet to switch on the lights. You should see "If + This Then That"

![](https://github.com/rainyraina/dialogflow_ifttt_webhooks_smartlight/blob/master/github_photos/ifthisthenthat.PNG)
* click on the "+" and select "Webhooks" as the service. Select "Receive a web request".
* Event Name: "lights_on"
* click on the "+" and select "Yeelight" (or other supported brands) as the action. Select "Toggle lights on/off". Select your light's name and choose "On".
### 1.3 Repeat the steps for "lights_off"
### 1.4 You will notice that there are other options for your light settings. You can explore them on your own!
  
# 3.  Heroku (Webhook service)
### 1.1 Create a Heroku account
### 1.2 Browse to https://heroku.com/deploy?template=https://github.com/jpruden92/ifttt-dialogflow-webhook
### 1.3 Enter an app name and choose a region. Then click on "Deploy app".

![](https://github.com/rainyraina/dialogflow_ifttt_webhooks_smartlight/blob/master/github_photos/heroku.PNG)
### 1.4 Click on "View" and you should see the URL of your fulfillment: https://<app_name>.herokuapp.com/fulfillment
* Copy the Fulfillment URL and paste it under Dialogflow's Fulfillment > Webhook > URL*
* Basic Auth(Default): Username and password is "test" 

![](https://github.com/rainyraina/dialogflow_ifttt_webhooks_smartlight/blob/master/github_photos/fulfillment.PNG)
### 1.5 IFTTT Events URL: Browse to https://ifttt.com/maker_webhooks/settings and copy the URL
### 1.6 Connections:

![](https://github.com/rainyraina/dialogflow_ifttt_webhooks_smartlight/blob/master/github_photos/connections.PNG)
* Ensure that your Dialogflow intent and IFTTT are correct.
    
# 4. Start your Telegram Bot
- Type "/start" and "lights"
          
Special thanks to SoumyadeepPal for creating the IFTTT - Dialogflow connector (https://elements.heroku.com/buttons/soumyadeeppal/ifttt-dialogflow-webhook)
