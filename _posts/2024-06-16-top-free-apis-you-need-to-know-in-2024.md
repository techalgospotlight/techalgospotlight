---
layout: post
title: "Top Free APIs You Need to Know in 2024"
excerpt: As per market trends and scenario APIs (Application Programming Interfaces) are essential tools for developers, allowing them to integrate third-party services into their applications. Here is an extensive list of free APIs available in 2024 and onwards across various categories, along with website links, descriptions, and sample code for each. Gaming APIs Steam Community API
date: June 19, 2024
author: neha
categories: 
    - general
image: /assets/techalgospotlight-og.png
keywords: api
published: true
---

As per market trends and scenario APIs (Application Programming Interfaces) are essential tools for developers, allowing them to integrate third-party services into their applications. Here is an extensive list of free APIs available in 2024 and onwards across various categories, along with website links, descriptions, and sample code for each.

* * *

Gaming APIs
-----------

### Steam Community API

*   **Website**: [steamcommunity.com/dev](https://steamcommunity.com/dev)
*   **Description**: The Steamworks Web API provides an interface to various Steam features such as user authentication, inventory management, and game data.

#### Sample Code

```js
const fetch = require('node-fetch');

const steamApiKey = 'YOUR_STEAM_API_KEY';
const steamId = 'STEAM_USER_ID';
const url = `http://api.steampowered.com/ISteamUser/GetPlayerSummaries/v0002/?key=${steamApiKey}&steamids=${steamId}`;

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


### Riot Games API

*   **Website**: [http://developer.riotgames.com](http://developer.riotgames.com/)
*   **Description**: Access data for games like League of Legends, Teamfight Tactics, Valorant, and more. Provides data on matches, rankings, champions, and other game-related statistics.

#### Sample Code

```js
const fetch = require('node-fetch');

const riotApiKey = 'YOUR_RIOT_API_KEY';
const summonerName = 'SUMMONER_NAME';
const url = `https://na1.api.riotgames.com/lol/summoner/v4/summoners/by-name/${summonerName}?api_key=${riotApiKey}`;

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


* * *

Language APIs
-------------

### Evil Insult Generator API

*   **Website**: [evilinsult.com/api](http://evilinsult.com/api "evilinsult.com/api")
*   **Description**: Generate random insults in various languages for fun or testing purposes.

#### Sample Code

```js
const fetch = require('node-fetch');

const url = 'https://evilinsult.com/generate_insult.php?lang=en&type=json';

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


### Fun Translations API

*   **Website**: [funtranslations.com/api](http://funtranslations.com/api "funtranslations.com/api")
*   **Description**: Translate text into various fun languages like Yoda, Shakespeare, Minion speak, and more.

#### Sample Code

```js
const fetch = require('node-fetch');

const text = 'Hello, world!';
const url = `https://api.funtranslations.com/translate/yoda.json?text=${encodeURIComponent(text)}`;

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


* * *

Music APIs
----------

### Spotify Web API

*   **Website**: [developer.spotify.com/documentation/web-api](http://developer.spotify.com/documentation/web-api "evilinsult.com/api")
*   **Description**: Access music data such as albums, artists, playlists, and user data. Control Spotify playback and more.

#### Sample Code

```js
const fetch = require('node-fetch');

const accessToken = 'YOUR_SPOTIFY_ACCESS_TOKEN';
const url = 'https://api.spotify.com/v1/me/player/recently-played';

fetch(url, {
    headers: {
        'Authorization': `Bearer ${accessToken}`
    }
})
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


* * *

Security APIs
-------------

### Have I Been Pwned API

*   **Website**: [haveibeenpwned.com/API/v2](http://haveibeenpwned.com/API/v2 "evilinsult.com/api")
*   **Description**: Check if your email or username has been part of a data breach. Provides data on breaches, pastes, and password exposure.

#### Sample Code

```js
const fetch = require('node-fetch');

const email = 'test@example.com';
const url = `https://haveibeenpwned.com/api/v2/breachedaccount/${email}`;

fetch(url, {
    headers: {
        'User-Agent': 'Node.js'
    }
})
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


### Shodan API

*   **Website**: [developer.shodan.io](http://developer.shodan.io/ "evilinsult.com/api")
*   **Description**: Shodan is a search engine for Internet-connected devices. It provides data on various servers, devices, and systems worldwide.

#### Sample Code

```js
const fetch = require('node-fetch');

const shodanApiKey = 'YOUR_SHODAN_API_KEY';
const query = 'apache';
const url = `https://api.shodan.io/shodan/host/search?key=${shodanApiKey}&query=${query}`;

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


* * *

Science & Math APIs
-------------------

### NASA API

*   **Website**: [api.nasa.gov](http://api.nasa.gov/ "api.nasa.gov")
*   **Description**: Access data from NASA’s datasets including astronomy photos, planetary data, and more.

#### Sample Code

```js
const fetch = require('node-fetch');

const nasaApiKey = 'YOUR_NASA_API_KEY';
const url = `https://api.nasa.gov/planetary/apod?api_key=${nasaApiKey}`;

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


### Wolfram Alpha API

*   **Website**: [products.wolframalpha.com/api](http://products.wolframalpha.com/api "api.nasa.gov")
*   **Description**: Provides access to the vast computational knowledge of Wolfram Alpha, including math calculations, data analysis, and more.

#### Sample Code

```js
const fetch = require('node-fetch');

const wolframAppId = 'YOUR_WOLFRAM_APP_ID';
const query = 'integrate x^2';
const url = `http://api.wolframalpha.com/v2/query?input=${encodeURIComponent(query)}&appid=${wolframAppId}&output=json`;

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


### Open Science Framework API

*   **Website**: [developer.osf.io](http://products.wolframalpha.com/api "api.nasa.gov")
*   **Description**: Access research data, project management tools, and other scientific resources from the Open Science Framework.

#### Sample Code

```js
const fetch = require('node-fetch');

const url = 'https://api.osf.io/v2/nodes/';

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


* * *

Sports APIs
-----------

### NBA API

*   **Website**: [any-api.com/nba\_com/nba\_com/docs/API\_Description](http://api.nasa.gov/ "api.nasa.gov")
*   **Description**: Access data on NBA teams, players, and games.

#### Sample Code

```js
const fetch = require('node-fetch');

const url = 'https://api-nba-v1.p.rapidapi.com/teams/league/standard';
const options = {
    method: 'GET',
    headers: {
        'X-RapidAPI-Key': 'YOUR_RAPIDAPI_KEY',
        'X-RapidAPI-Host': 'api-nba-v1.p.rapidapi.com'
    }
};

fetch(url, options)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


* * *

Web Apps APIs
-------------

### Discord API

*   **Website**: [discord.com/developers/docs/intro](http://discord.com/developers/docs/intro "api.nasa.gov")
*   **Description**: Integrate your applications with Discord, allowing for user authentication, messaging, and more.

#### Sample Code

```js
const fetch = require('node-fetch');

const discordToken = 'YOUR_DISCORD_BOT_TOKEN';
const url = 'https://discord.com/api/users/@me';

fetch(url, {
    headers: {
        'Authorization': `Bot ${discordToken}`
    }
})
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


### Slack API

*   **Website**: [api.slack.com](http://api.slack.com/ "api.nasa.gov")
*   **Description**: Access Slack features such as messaging, user data, and workspace management.

#### Sample Code

```js
const fetch = require('node-fetch');

const slackToken = 'YOUR_SLACK_API_TOKEN';
const url = 'https://slack.com/api/conversations.list';

fetch(url, {
    headers: {
        'Authorization': `Bearer ${slackToken}`
    }
})
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```


* * *

Conclusion
----------

This comprehensive list of free APIs for 2024 spans a wide range of categories, offering developers numerous opportunities to enhance their applications with powerful and diverse functionalities. From gaming and music to science and government data, these APIs provide valuable resources for creating innovative and engaging projects.

Feel free to explore these APIs and integrate them into your projects to unlock new possibilities and features. Happy coding!