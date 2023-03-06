<h1 align="center">Discord Bot <img src="https://edu.stacktrek.com/logo192.png" width="30px"></h1>
<p align="center">A Template for Stacktrek Bootcampers</p>

## ✨Latest Updates

- Last Updated March 2023
<br><br>

## 🚧 Prerequisites

- Install [Node.js](https://nodejs.org/en/download/)

<br>

## 📝 Steps

Please follow steps below:
1. Go to https://discord.com/developers/applications. Create an application. Under Bot tab, add a bot.

2. Create a folder named
    ```discord-bot```

3. Create the following files and copy correct tokens and ids from your discord application:

```.env```
```
BOT_TOKEN=
CLIENT_ID=
```

```.gitignore```
```
.env
\node_modules
```

```bot.js```
```
require('dotenv').config()
const { REST, Routes } = require('discord.js');

const commands = [
  {
    name: 'sith',
    description: 'Saying hi!',
  },
];

const rest = new REST({ version: '10' }).setToken(process.env.BOT_TOKEN);

(async () => {
  try {
    console.log('Started refreshing application (/) commands.');

    await rest.put(Routes.applicationCommands(process.env.CLIENT_ID), { body: commands });

    console.log('Successfully reloaded application (/) commands.');
  } catch (error) {
    console.error(error);
  }
})();

const { Client, GatewayIntentBits } = require('discord.js');
const client = new Client({ intents: [
    GatewayIntentBits.Guilds,
    GatewayIntentBits.GuildEmojisAndStickers,
] });

client.on('ready', () => {
  console.log(`Logged in as ${client.user.tag}!`);
});

client.on('interactionCreate', async interaction => {
  if (!interaction.isChatInputCommand()) return;
  const { commandName } = interaction;

  if (commandName === 'sith') {
    try {
        const message = await interaction.reply({ content: 'Hi my name is Sith.', fetchReply: true });
        await message.react('🇯');
    } catch (error) {
        // handle failure of any Promise rejection inside here
    }
  }
});

client.login(process.env.BOT_TOKEN);
```

3. Install the following using a terminal

```
npm init -y
npm install discord.js
npm install nodemon
npm install dotenv
```

4. On your ```package.json``` file edit the scripts:
```
"scripts": {
    "start": "node bot.js",
    "devStart": "nodemon bot.js"
  },
```


5. In [Discord Application](https://discord.com/developers/applications), authorize your discord bot app in OAuth.


You need to check the following:
- bot
- applications.command
- administrator

Copy the URL that is generated and paste it in a new tab. Select a server and authorize.

6. Check if your bot is now on discord and if it is still offline, need to run the last step.

7. Make your bot alive by running in the terminal.

```
npm run devStart
```


## 📝 [Support Server](https://discord.gg/sbySMS7m3v)

If you have issues with this sample template, please ask for help.


## 💨 Run the projects
```
npm run start
```

Made with :heart: and JavaScript!
