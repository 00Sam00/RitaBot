---
title: "Installing RITA"
permalink: /new-bot/
excerpt: "Installing RITA"
last_modified_at: 2020-09-29T14:00:00+01:00   
redirect_from:
  - /theme-setup/
toc: true


---

Rita is a an automatic translation bot built using `discord.js` and `Google Translate API`.

## Setting up a Bot Manually

**To deploy a free translation bot that you can add to your discord server, follow these easy steps.**

### Step 1 - Fork this repository
* If you don't yet have a Github account, [create one](https://github.com/join)! It's free and easy.
* Click [here](https://github.com/ZyC0R3/RitaBot/fork) or use the button in the upper righthand side of this page to fork the repository so that it will be associated with your Github account.

### Step 2 - Create a new [Discord App](https://discordapp.com/developers/applications/me/create)
* Give app a friendly name and click the **Create App** button
  * I like the name **C-3PO**, but feel free to pick something different if you fear George Lucas's wrath. Maybe **C-4PO**
* Take note of the app **CLIENT ID**, you will need it later
* Scroll down to the **Bot** section
* Click the **Create a Bot User** button
* Click the **Yes, do it!** button
* Copy the bot's **TOKEN**, you will need it later


### Step 3 - Create a Heroku account
* Create a new app. It's name must be unique and composed of all lowercase letters and dashes. Something like `yourname-discordbot` is fine
* Under **Deployment Method** select Github. Connect to your Github account and search for this repository by name.
* Scroll down to the manual deploy section, and select the **Master** branch. Click deploy branch, and wait for the successfully deployed message.
* Go to the **Resources** tab and look for the addons section. Search 'Postgres', and add a 'Hobby Dev - Free' version of Heroku Postgres. This will be automatically attached as your bot's database.
* Go to the **Settings** tab. Click to reveal Config Variables, then add then add the following:
  * **KEY:** =  DISCORD_TOKEN
  * **Value:** = Your discord bot's token that you copied earlier.
  * **KEY:** =  NODE_MODULES_CACHE
  * **Value:** = false
    * *This is to ensure that when the bot updates it does not use any old Dependencies that Heroku has stored and gets fresh ones from the package.json file*
* Go to the **Overview** tab and click configure dynos. Turn off the default `web npm start` dyno and turn on the `worker node src/bot.js` dyno. Your bot will now be up and running!

### Step 4 - Invite your bot to your server and configure it!
* Replace the CLIENTID string in the following URL with your own apps client id from Step 2: https://discordapp.com/oauth2/authorize?&client_id=CLIENTID&scope=bot&permissions=8
* Visit the resulting URL and add your bot to any server where you have admin privileges.
* Once added, your bot should show up more or less instantaneously. Type `!t help` within the discord chat for more details on how to use it. Happy translating!
