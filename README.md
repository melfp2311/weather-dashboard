# TDM coding bootcamp
# Melissa Flores
# 06 Server-Side APIs: Weather Dashboard



## User Story

```
AS A traveler
I WANT to see the weather outlook for multiple cities
SO THAT I can plan a trip accordingly
```

## PSeudocoding 

```
GIVEN a weather dashboard with form inputs
WHEN I search for a city
THEN I am presented with current and future conditions for that city and that city is added to the search history
WHEN I view current weather conditions for that city
THEN I am presented with the city name, the date, an icon representation of weather conditions, the temperature, the humidity, the wind speed, and the UV index
WHEN I view the UV index
THEN I am presented with a color that indicates whether the conditions are favorable, moderate, or severe
WHEN I view future weather conditions for that city
THEN I am presented with a 5-day forecast that displays the date, an icon representation of weather conditions, the temperature, and the humidity
WHEN I click on a city in the search history
THEN I am again presented with current and future conditions for that city
WHEN I open the weather dashboard
THEN I am presented with the last searched city forecast

Used the [OpenWeather API](https://openweathermap.org/api) to retrieve weather data for cities. 
```

## Tech and Features Used

Bootstrap
Javascript
JQuery
Open Weather API
Postman
​

How to use
​Type in a cities name in the search bar and click search. on the right side of the screen you will see the current weather on a large card. underneath that card you will see the five day forecast. After you click search, a button will appear on the left side of the screen underneath the search bar with the name of the city that you just searched for. When you click on that button the right side of the screen will populate the weather information for that city. When you search for a new city the search button will generate a new history button underneath the search bar, and the old search button will move down a level. Everytime you search for a new city the same process will take place until you have reached five cities and then the oldest city button will dissapear.​

Technical Overview
The search button triggers the ajax call to the open weather current weather api, the uv index api, the five day forecast weather api, and saves the city name to a variable,saves the city name to an array in local storage and if there is any information populated on any of the weather cards it clears that information.
The openweather api will send back the weather information including the latitude and longitude for the city we are searching for.
The uv index api is going to use the latitude and longitude information from the current weather api to give us the uv index.
the city name variable is going to be used in the ajax call for the 5 day forecast api.
the city name will be saved in local storage.
there is a function that is called before the ajax calls that takes the saved information from local storage and loops through the city list array and creates a list of buttons with the name of the city on each button.
the button will go through the same process of the seach button with the exception of saving the city name to the local storage array, and therefore does not create a new city button under the search bar.
As the API calls finish the information needed (temperature, humidity, uv index and windspeed) populate the current weather card, as well as the five day forecast cards.


Challenges
Some of the challenges I faced:

the JQuery click method did not like working on dynamically created classes, I learned that click methods need to be grabbed from the static parent of the created buttons. with the syntax being $("#city-list").on("click", "button",function()) with the selector being city-list, then the event handler, then the event selector being button.

the other challenge i had were the ajax calls being synchronous and how or if I could wait for the information i was getting would affect the next multiple ajax calls. The uv index call required lon and lat information which came from the current weather api. so I nested the uv index ajax call in the current weather call.

the five day forecast also needed the city ID code, if I wanted to make sure that the same city that was being called from the current weather api, so I nested that in the .then method after the ajax call as well so to wait for the information to get back. ultimately i did not have to do any async manipulation with this app.​L
