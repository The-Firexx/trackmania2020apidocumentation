# Trackmania 2020 Unofficial API Documentation
This repository is a series of markdown files containing all the documentation myself and others found about Trackmania 2020 and the API calls the game makes to work.

## Progress

This is in a very begin phase so please pull request to help this project by fixing typos, fix errors, describe in more detail the use of the endpoints, helping in the structure of documentation, and most important add more information.

Any help is appreciated!

## TODO

* **Since I don't have club access, I can't test some functions inside the game like rooms and clubs, so that part are lacking in this documentation**

## General View

For the game to work, first we need to authenticate. The next picture ilustrates the process of login in the APIs and how the different tokens have different uses

![LoginProcess](loginTrackmania.png)

*Although this is the primary login process, there's more like we found in the UbiServices*

As you can see, you only need to use the Login Level 0, 1 and 2 only one time, after that you only need to refresh the token from Level 1 and 2 without needing for Uplay login anymore.

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
* AccountId - Used ingame to identify a user. ***Idk when the game knows our accountId***
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