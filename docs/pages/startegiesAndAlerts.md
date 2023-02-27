
## Strategies & Alert

This is where BotVox differs from many other Trading Bots, Creating Alerts and Strategies is super simple and easy.
The Simplicity is achieved by using VoxStates that are validated at the VoxEngineLevel. With just a few lines of code you can
Implement complex strategies and Validate them through the VoxEngine Back-testing interface. And install the final product into your botvox strategy repository

### Back-Testing Strategies

As you saw in usage example's the VoxEngine ``--strategy`` commandline flag allows a specific flag ```--backtest=true```
to be supplied. 
When this flag is provided as true the VoxEngine runs your Strategy through a Back testing scenario and returns
a JSON output outlining a few details about your strategy and success rate.

![bv-3](https://github.com/bot-vox/botv-resources/blob/main/_resources/back-test.jpg?raw=true)

Currently, all test results are stored and persisted in botvox internal backtest directory in ```botvox\output\backtest```
which makes these files not really accessible, but we will add additional Tooling in the future that allows for viewing and analyzing back test results.

Work to improve the back-testing engine are in pipelines, and exciting new features are coming in the future.

## Alerts & Notifications

Currently, there are 3 Different types of Notification mechanisms that you can leverage to receive Alerts from your Alerting and Notification Solutions.

1. Email
2. Slack
3. Telegram

Each of which have slightly different Setup and Configuration requirements that you need to follow very carefully in order to receive Alerts!

### Email

We are using SendGrid to send emails, so in order for you to send Emails to a dedicated Email Account you must first create a free or paid Account.

Visit this link: https://sendgrid.com/ to follow the Account Setup Instructions and optain an API Key, 
you need to provide this key when you start your Alerting Bot.

As a side note, its important that after you have created an Account and generated an API Key that you also create a verified sender email address we found
this link useful and helpful: https://app.sendgrid.com/settings/sender_auth/senders

### Slack

In Order to for to leverage Slack Notifications you need to the following ready to hand:

1. A Slack Account and a Work Space
2. A Bot User that you need to configure in order to retrieve an oAuth token to make API request!

To Sign in or Create an Account got to https://slack.com

Here is a Good Guide on how to Generate a Slack Bot User you can skip the (Making Your First Request) section
Since botvox will handle that for you!
This is a good place to learn and start setting up a Slack Account & Channel!

https://thecodebarbarian.com/working-with-the-slack-api-in-node-js.html

### Telegram
In Order to for to leverage Telegram Notifications you need to go through a few simple steps

1. Create a Bot with Bot Father
2. Take Note of the API token
3. Retrieve your session or Chat ID.

To Create a Bot with BotFather visit this link:https://blog.devgenius.io/how-to-set-up-your-telegram-bot-using-botfather-fd1896d68c02

Follow the Instructions and once you have created a bot all you need to do, is start your alerting bot with botvox, 
and open your newly created Bot on Telegram and enter ``/start`` In the chat box.

This will Create an internal Chat ID on the Bot side and the bot will start sending Notifications to your Chat!

