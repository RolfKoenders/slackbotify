
# slackbotify
[![XO code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg)](https://github.com/sindresorhus/xo)

> Simple slackbot framework

## Installation
```
npm install slackbotify
```

## Usage
Creating a slackbot is as easy require the dependency, load the config and register a handler. Run it. Done. Slackbot is ready!

```
const Bot = require('slackbotify');

let bot = new Bot({
	"bot": {
		"token": "xoxb-XXXXX-XXXXX",
		"name": "butler"
	}
});

bot.registerHandler({
	group: 'direct',
	match: /hi/ig,
	handler: function (message, callback) {
		callback('Hi there! :smiley:');
	}
});

bot.run();
```

## Configuration
The only thing you have to pass to the constructor is a config object, and this config object should have at least a `bot` object with 2 properties: `token` & `name`. _(example above)_

## Handlers
To register a handler to the bot simple pass an object to the `registerHandler` function. This object needs to contain the following properties: `group`, `match`, `handler`.

### Group
The group defines where the command is avilable. There are 3 groups. `channel`, `direct`, `admin`. Handlers which are registered to the 'channel' group will fire when a message is send in a channel where the bot is invited to. 'Direct' handlers are private messages to the bot, and the 'admin' group handlers can only be called by an admin user in a private message.

### Match
The 'match' property is what the message should match in order to get called. This can be a regex or a string.

### Handler
The handler is a function which receives as the first argument the actual messages which is send, parsed by the `.match()` function. The second argument is the callback. The response you give to that callback is send to the user, so basically what the bot will answer.

## License
[MIT](https://opensource.org/licenses/MIT)
