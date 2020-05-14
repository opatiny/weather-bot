# weather-bot

Node-red telegram bot that sends info about the weather.

## Running the project

You must have `node-red` installed to run this project.

The project uses two environment variables: `BOT_TOKEN` and `OWM_ID`.  `OWM_ID` is the private user key that you get when subscribing to openweathermap. `BOT_TOKEN` is the bothFather token of your telegram bot.

Their value must be set when running node-red:
```bash
BOT_TOKEN=<value1> OWM_ID=<value2> node-red
```

## Goal

Use Node-RED to retrieve weather data from [https://openweathermap.org/](https://openweathermap.org/), and send it to a Telegram group through a bot.

## Desired API

The bot should accept a bunch of commands beginning with `/`. Each command should return some weather information fetched on OpenWeather.

Some of the commands can be followed by a number, which is the number of hours in the future for which the forecast must be made. Max. number of hours is 120 h aka 5 days. You do the math to know when tomorrow is.

Optionally: The bot should warn you if there is going to be rain that day, given it is not muted.

### Commands / help text (in BotFather required format)

**Help**

/temp - Measured temperature

/tempfeel - Human perceived temperature

/wind - Wind speed

/weather - Weather description -> clear, cloudy, rain, ...

/clouds - Percentage of sky covered with clouds

/rain - Amount of rain fallen

/humidity - Humidity in percents

/all - Get all information given by other commands at once.

/city - Get all information like with "/all" for another city than Denges. City name should be only in lowercase letters.

/nextday - Temperature, perceived temperature and weather description for the next 24h in Denges

/help - Information about all available commands

- All commands excepted /city, /nextday and /help can be followed by a number (we call it time offset), which indicates for when the weather prediction must be (number of hours in the future from now). The maximal value of this number is 120 hours aka 5 days. If no time offset is used, current info is returned.

- /help and /nextday accept no parameters.

- /city must have two parameters. First the time offset, then the name of the city for which you want the forecast, all in lowercase.

To potentially implement someday?

mute - Mute the bot's rain warnings

talk - Unmute the bot's rain warnings
