# Creating the main file

::: tip
This page assumes you've already prepared the [configuration files](/creating-your-bot/#creating-configuration-files) from the previous page. We're using the `config.json` approach, however feel free to substitute your own!
:::

Open your code editor and create a new file. We suggest that you save the file as `index.js`, but you may name it whatever you wish.

Here's the base code to get you started:

```js
// Require the necessary discord.js classes
const { Client, GatewayIntentBits } = require('discord.js');
const { token } = require('./config.json');

// Create a new client instance
const client = new Client({ intents: [GatewayIntentBits.Guilds] });

// When the client is ready, run this code (only once)
// We use 'c' for the event parameter to keep it separate from the already defined 'client'
client.once('ready', c => {
	console.log(`Ready! Logged in as ${c.user.tag}`);
});

// Log in to Discord with your client's token
client.login(token);
```

This is how you create a client instance for your Discord bot and log in to Discord. The `GatewayIntentBits.Guilds` intents option is necessary for the discord.js client to work as you expect it to, as it ensures that the caches for guilds, channels, and roles are populated and available for internal use.

::: tip
The term "guild" is used by the Discord API and in discord.js to refer to a Discord server.
:::

Intents also define which events Discord should send to your bot, and you may wish to enable more than just the minimum. You can read more about the other intents on the [Intents topic](/popular-topics/intents).

## Running your application

Open your terminal and run `node index.js` to start the process. If you see "Ready!" after a few seconds, you're good to go! The next step is to start adding [slash commands](/creating-your-bot/slash-commands.md) to develop your bot's functionality.

::: tip
You can open your `package.json` file and edit the `"main": "index.js"` field to point to your main file. You can then run `node .` in your terminal to start the process!

After closing the process with `Ctrl + C`, you can press the up arrow on your keyboard to bring up the latest commands you've run. Pressing up and then enter after closing the process is a quick way to start it up again.
:::

#### Resulting code

<ResultingCode path="creating-your-bot/initial-files" />