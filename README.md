# Trackmania 2020 Unofficial API Documentation
This repository is a series of markdown files containing all the documentation myself and others found about Trackmania 2020 and the API calls the game makes to work.

## Warning!!

**This API is not intended to be used outside of the game!!**

Be aware that Nadeo can change the API without even warning us, since the API is intended only to be used in game, so don't except any support for them, and don't try to make anything serious out of this

Also, **don't abuse of this API, has they have the right to lock your account since, for them, it's someone that is trying to hack or just trying to give bad performance to the servers**

## Progress

This is in a very begin phase so please pull request to help this project by fixing typos, fix errors, describe in more detail the use of the endpoints, helping in the structure of documentation, and most important add more information.

Any help is appreciated!

## TODO

* **Since I don't have club access, I can't test some functions inside the game like rooms and clubs, so that part are lacking in this documentation**

## Contributors

* Myself, [The-Firexx](https://github.com/The-Firexx), for gathering most of this information and creating this repository
* [Marco97pa](https://github.com/marco97pa) for helping on completing some information. He's also creating this [companion app](https://play.google.com/store/apps/details?id=com.marco97pa.trackmania) that will benefit from this documentation
* [Codecat](https://github.com/codecat) from showing some [information](https://gist.github.com/codecat/4dfd3719e1f8d9e5ef439d639abe0de4) about this, and suggest to add the warning about the use of Trackmania API. Also made this [plugin](https://openplanet.nl/files/49) for OpenPlanet to inspect the packets ingame

## Login Process

For the game to work, first we need to authenticate. The next picture ilustrates the process of login in the APIs and how the different tokens have different uses

![LoginProcess](loginTrackmania.png)

*Although this is the primary login process, there's more like we found in the UbiServices*

As you can see, you only need to use the Login Level 0, 1 and 2 only one time, after that you only need to refresh the token from Level 1 and 2 without needing for Uplay login anymore.

## Tokens

The tokens that are being used in the process described before are of JWT type. So, if we try to decode them we get:

### Ticket Value from Response Level 0

This one is encrypted, probably because this response come from UbisoftServers to login on Uplay. We are only able to check their headers, that confirm the JWT token is a encrypted one (*JWE*)

```json
{
 "ver": "1",
 "aid": "*someId*", 
 "env": "Prod",
 "sid": "*someId*", 
 "typ": "JWE",
 "enc": "A128CBC",
 "iv": "*inicializerVector*",
 "int": "HS256"
}
```

*Missing description*

### Access Token Value from Response Level 1 and 2

This response came from the Trackmania API and this one is ***not*** encrypted. If we check the headers and payload of the JWT we get this:

**Header**

```json
{
 "typ": "JWT",
 "alg": "HS256",
 "env": "trackmania-prod",
 "ver": "1"
}
```

**Body**

```json
{
 "jti": "*someId*",
 "iss": "NadeoServices",
 "iat": 1595707067,
 "rat": 1595708867,
 "exp": 1595710667,
 "aud": "NadeoServices",
 "usg": "Client",
 "sid": "*someId*",
 "sub": "*accountId*",
 "aun": "*username*",
 "rtk": false,
 "pce": false,
 "ubiservices_pid": "*someId*"
}
```

**iss** is the name of the issuer, **exp** tells use the time until the token is valid, **rat** the time where after that we can refresh our token, **aud** is for where the token is to be used (Level 1 says NadeoServices, but Level 2 can say NadeoLiveServices or other), **usg** the type of use, **sub** is our accountId (this is were we know our accountId on the game), **aun** is our username. The **sid** is the same for both accessToken and refreshToken, and Level 1 and 2, although I don't know what is this. *Missing more description*

### Refresh Token Value from Response Level 1 and 2

The header JWT is the same as the last one, the body have this structure:

```json
{
 "jti": "*someId*",
 "iss": "NadeoServices",
 "iat": 1595707067,
 "rat": 1595750267,
 "exp": 1595793467,
 "aud": "NadeoServices",
 "usg": "Client",
 "sid": "*someId*",
 "sub": "*accountId*",
 "aun": "*username*",
 "rtk": true,
 "pce": false,
 "ubiservices_pid": "*someId*",
 "refresh_aud": "NadeoServices",
 "limit_type": "none"
}
```

We can see that this one have **rtk** to true (although I don't know what is this), and have a **refresh_aud**  (Level 1 says NadeoServices, but Level 2 can say NadeoLiveServices or other), and a **limit_type**. *Missing more description*



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
* AccountId - Used ingame to identify a user. ~~Idk when the game knows our accountId~~
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