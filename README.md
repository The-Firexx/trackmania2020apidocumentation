# Trackmania 2020 Unofficial API Documentation
This repository is a series of markdown files containing all the documentation myself and others found about Trackmania 2020 and the API calls the game makes to work.

## Warning!!

**This API is not intended to be used outside of the game!!**

Be aware that Nadeo can change the API without even warning us, since the API is intended only to be used in game, so don't except any support for them, and don't try to make anything serious out of this

Also, **don't abuse of this API, has they have the right to lock your account since, for them, it's someone that is trying to hack or just trying to give bad performance to the servers**

## Progress

This is in a very begin phase so please pull request to help this project by fixing typos, fix errors, describe in more detail the use of the endpoints, helping in the structure of documentation, and most important add more information.

Any help is appreciated!

Also, if you have any project that you are developing and you are using this documentation to help you in the interaction with the Trackmania API you can share with me and I will be glad to share here your project. It can be a simple wrapper library or even a full app. 

## TODO

* **Since I don't have club access, I can't test some functions inside the game like rooms and clubs, so that part are lacking in this documentation. If you have club access and wants to help, but you dont want to give your credentials to me, you can DM me and I can say how you can help me**

## Contributors

* Myself, [The-Firexx](https://github.com/The-Firexx), for gathering most of this information and creating this repository
* [Marco97pa](https://github.com/marco97pa) for helping on completing some information.
* [Codecat](https://github.com/codecat) from showing some [information](https://gist.github.com/codecat/4dfd3719e1f8d9e5ef439d639abe0de4) about this, and suggest to add the warning about the use of Trackmania API. Also made this [plugin](https://openplanet.nl/files/49) for OpenPlanet to inspect the packets ingame
* [Breeku](https://github.com/breeku) for helping on completing information about webidentities

## Projects using Trackmania API

* [Breeku](https://github.com/breeku/) made a [npm module](https://github.com/breeku/trackmania-api-node) that helps developers to use the Trackmania API by abstracting the HTTP requests and wrap them in methods that can be called for a more easy use of the API in a program.
* [Jonese1234](https://github.com/jonese1234/) created a [Leaderboard Scraper](https://github.com/jonese1234/Trackmania-2020-Leaderboard-Scraper) that, although it started without help, is using this documentation to use more functions.
* [Marco97pa](https://github.com/marco97pa) is creating this [companion app](https://play.google.com/store/apps/details?id=com.marco97pa.trackmania) that is in progress to add more functions by using the Trackmania API.

## Login Process and Tokens

[Here](Login.md) you can check all the process of login and getting the tokens, with a explanation of what information the tokens have.

## APIs

* **public-ubiservices.ubi.com** - used only to login and get a Level 0 Token
* **prod-trackmania.core.nadeo.online** - used to login and get a Level 1/2 Token and responsible for overall player stuff that needs to be configured and updated (settings, mapRecords, clubs, etc.)
* **live-services.trackmania.nadeo.live** - used to get seasons, track of the days, leaderboards, servers, clubcampaigns, map review. Maybe this API is different from the **prod-trackmania.core.nadeo.online** since it is responsible to save and retrieve content associated with users, like ghosts, but to avoid the overload cause by the game constantly checking the leaderboard, they decided to separate that part from the rest.
* **useast1-public.aws-ubiservices.ubi.com** - used to get the integration with Uplay like login and settings
* **msr-public.aws-ubiservices.ubi.com** - used to update information about the activity of a user
* **akamai.net** - used to download stuff like images, logos, archive, etc.
* **amazonaws.com** - where they have the files hosted like maps and stuff

## IDs

There are many IDs that are used to identify things and make requests. The follow list shows that IDs and their purpose:

* ProfileId - Obtained when we login to Uplay (Level 0)
* AccountId - Used ingame to identify a user. Obtained within the JWT Token from Level 1 or 2 Login Process
* MapId/MapUid - Used ingame to identify a map
* GroupId/GroupUid - Used ingame to identify a group (***Needs more info about what is a group***)
* SeasonId - Used ingame to identify a season (like the campaigns, club campaigns and track of the day)
* ClubId - Used ingame to identify a club
* RoomId - Used ingame to identify a room inside a club (***What type of rooms exist inside a club?***)

## Specification

You can access in more detail what endpoints exist, the information needed to send and the response received in the next links:

[Prod Trackmania API](ProdTrackmania.md)

[Live Services API](LiveServices.md)

[UbiServices](UbiServices.md)

[msr-public and akamai.net](MSR-Akamai.md)