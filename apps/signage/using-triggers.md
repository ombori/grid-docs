# Using Triggers in Signage Playlist
Triggers are great for dynamically adjusting the playlist based on external factors. However, there are a few rules to keep in mind for triggers.

- If a trigger is true, all content will be played inside the trigger.
- If multiple triggers are true, all of them will be played
  - Unless you check the "only play first trigger" checkbox, then all other triggers AND content will be ignored.

With that in mind, let's have a look at the trigger options

## Triggers

There are several triggers you can use

| Trigger         | Description                                                   |
| --------------- | ------------------------------------------------------------- |
| DATETIME        | Select a date/time range when it should be visible            |
| DATE            | Set a date range when the content should be visible           |
| TIME            | Set a time range when content should be visible               |
| DAY             | Specify which days of the weeks the content should be visible |
| WEATHER         | Specify what weather shows what content based on a city       |
| TEMPERATURE_MIN | From what temperature should the content show                 |
| TEMPERATURE_MAX | Until what temperature should the content show                |

## DATETIME
With the DATETIME trigger, you can specify a date/time range when to display certain content. This is a one-time trigger as you cannot specify multiple date/times.

The device configuration of date/time is used for this trigger.

![](/assets/trigger-datetime.png ":size=500 :no-zoom")

## DATE
The DATE trigger allows you to specify a date range when to display certain content. This is a one-time trigger as you cannot specify multiple dates.

The device configuration for DATE is used for this trigger.

![](/assets/trigger-date.png ":size=500 :no-zoom")

## TIME
The TIME trigger allows you to specify a time from and to when to display certain content. This trigger will be true every day it matches the time.

The device time is used for this trigger.

![](/assets/trigger-time.png ":size=500 :no-zoom")

## DAY
The DAY trigger allows you to select which days of the week certain content needs to be displayed. This trigger will be true every week it matches the day(s).

![](/assets/trigger-day.png ":size=500 :no-zoom")

## WEATHER
The WEATHER trigger allows you to play content specific to the weather at the specified city. Several weather types can be used as a trigger

- Clear
- Clouds
- Drizzle
- Rain
- Snow
- Thunderstorm

Weather triggers are based on the OpenWeather API data. 

![](/assets/trigger-weather.png ":size=500 :no-zoom")

## TEMPERATURE_MIN
The TEMPERATURE_MIN trigger allows you to display content as soon as the temperature rises above the specified number. 

Weather triggers are based on the OpenWeather API data. 

![](/assets/trigger-temp-min.png ":size=500 :no-zoom")

## TEMPERATURE_MAX

The TEMPERATURE_MAX trigger allows you to display content as long as the temperature is below the specified number. 

Weather triggers are based on the OpenWeather API data. 

![](/assets/trigger-temp-max.png ":size=500 :no-zoom")
