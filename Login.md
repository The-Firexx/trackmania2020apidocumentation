# Login Process and Tokens

## Login Process

For the game to work, first we need to authenticate. The next picture ilustrates the process of login in the APIs and how the different tokens have different uses

![LoginProcess](D:/Firo/Documents/Projects/TrackmaniaAPIUnofficialDocumentation/loginTrackmania.png)

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

