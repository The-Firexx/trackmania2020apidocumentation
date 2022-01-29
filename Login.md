# Login Process and Tokens

## Login Process

For the game to work, first we need to authenticate. The next picture ilustrates the process of login in the APIs and how the different tokens have different uses

![LoginProcess](loginTrackmania.png)

*Although this is the primary login process, there's more like we found in the UbiServices*

As you can see, you only need to use the Login Level 0, 1 and 2 only one time, after that you only need to refresh the token from Level 1 and 2 without needing for Uplay login anymore.

### Login Process Example

### Token Level 0

For the level 0 token we need to do the following:

POST Request
URL: https://public-ubiservices.ubi.com/v3/profiles/sessions

Header:
| Key                       | Value                                |
|---------------------------|--------------------------------------|
| Authorization             | Basic \<basic-encodedString\>        |
| Ubi-AppId                 | 86263886-327a-4328-ac69-527f0d20a237 |
| Ubi-RequestedPlatformType | uplay                                |
| Content-Type              | application/json                     |
| User-Agent                | \<something\>                        |

For the User-Agent you sometimes need to out something in there like "PostmanRuntime/7.28.4".
I tried to send a request via python without the User-Agend field and it didn't work and only worked after adding it. So i am guessing that it is needed.

To get the basic-encodedString you need to append your ubisoft email with a ':' and then append this new string again with your ubisoft passwort. After that encode this string in base64.

eg. 
```
basic-encodedString = encodeBase64("<email>" + ":" + "<password>")
```

Body: is not needed (None)

After sending this request you will get a response that looks like this:

```json
{
    "platformType": "uplay",
    "ticket": "<redacted>",
    "twoFactorAuthenticationTicket": null,
    "profileId": "<redacted>",
    "userId": "<redacted>",
    "nameOnPlatform": "<your username>",
    "environment": "Prod",
    "expiration": "2021-10-28T02:07:39.9132598Z",
    "spaceId": "<redacted>",
    "clientIp": "<redacted>",
    "clientIpCountry": "<redacted>",
    "serverTime": "2021-10-27T23:07:39.9159598Z",
    "sessionId": "<redacted>",
    "sessionKey": "<redacted>",
    "rememberMeTicket": null
}
```
From this response you need to copy the string from the "ticket" field (very long string).
<br>This string is the level 0 token.

### Token Level 1

For the level 1 token you need to have a level 0 token and do the following:

POST Request URL: https://prod.trackmania.core.nadeo.online/v2/authentication/token/ubiservices

Header:
| Key           | Value                     |
|---------------|---------------------------|
| Authorization | ubi_v1 t=\<level-0-token\>|

<br>
Body: is not needed (None)
<br><br>
After sending this request you will get a response that looks like this:

```json
{
    "accessToken": "<redacted>",
    "refreshToken": "<redacted>"
}
```

The string that is stored in the accessToken field is the level 1 token and the string stored in the refreshToken field it the token that can be used to get a new accessToken and refreshToken if the current accessToken for level 1 is expired.

### Token Level 2

For the level 1 token you need to have a level 1 token and do the following:

POST Request URL: https://prod.trackmania.core.nadeo.online/v2/authentication/token/nadeoservices

Header:
| Key           | Value                       |
|---------------|-----------------------------|
| Authorization | nadeo_v1 t=\<level-1-token\>|

<br>
Body: should be JSON

```json
{"audience" : "NadeoLiveServices"}
```
The value in the body can be changed, to fit the service you try to authenticate with. In this example we try to authenticate at the "nadeo live services".

<br><br>
After sending this request you will get a response that looks like this:

```json
{
    "accessToken": "<redacted>",
    "refreshToken": "<redacted>"
}
```

The string that is stored in the accessToken field is the level 2 token and the string  stored in the refreshToken field it the token that can be used to get a new accessToken and refreshToken if the current accessToken for level 2 is expired.

Now we have aquired all tokens and can access the APIs.

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

