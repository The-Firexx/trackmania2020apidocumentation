# Routes prod.trackmania.core.nadeo.online

Because most of the time the game uses the same headers, the next headers are "general headers", and then in every endpoint I will specify with just a number the headers needed, and that number represent the same number I list the headers in this section

***If I put in the JSON Responses \*\* is because I want to hide sensitive information***

## General Headers

#### 1

***I dont think this headers are needed, I can make the same requests without this, so probably you can ignore this headers***

* User-Agent: ManiaPlanet/3.3.0 (Win64; rv: 2020-07-23_20_22; context: none; distro: UPLAY)
* Pragma: no-cache
* Cache-Control: no-cache, no-store, must-revalidate
* Accept-Encoding: gzip,deflate
* Accept-Language: en-US,en
* Nadeo-Game-Build: 2020-07-23_20_22
* Nadeo-Game-Distro: UPLAY
* Nadeo-Game-Lang: en-US
* Nadeo-Game-Name: ManiaPlanet
* Nadeo-Game-Version: 3.3.0

#### 2

Authorization: nadeo_v1 t=

##### 2.1

accessToken from Level 1

##### 2.2

accessToken from Level 2 - NadeoLiveServices

##### 2.3

accessToken from Level 2 - NadeoClubServices

## GET /client/config

* Use: To get the configuration of a client

* Headers: **1**

* Response

  ```json
  {"keys":[{"id":1,"timeout":2592000,"key":"*key*"},{"id":2,"timeout":2592000,"key":"*key*"},{"id":3,"timeout":2592000,"key":"*key*"}],"settings":{"KillSwitch_ProfileChunk":1,"KillSwitch_TitleConfig":1,"KillSwitch_TitleLadder":1,"KillSwitch_TitlePolicy":1,"KillSwitch_TitleProfileChunk":1,"KillSwitch_Xp":1,"AdsClearCacheOnExit":0,"AdsMandatory":0,"MapRecordResetTimestamp":0,"ClientIP":"*ip*"}}
  ```

  * 3 Keys with id and timeout and settings

## PUT /waitingQueue/*some id*

* Use: ***Idk***

* Headers: **1**

* Response

  ```json
  {"rank":0,"refreshTime":900,"timestamp":"2020-07-24T18:15:51+00:00","waitingTime":0}
  ```

  * rank is the position in the waitingQueue (0 is for no waitingQueue), refreshTime, timestamp and waitingTime

## POST /v2/authentication/token/ubiservices

* Use: Login to get a Level 1 Token using the credentials from the Uplay

 * Headers: 1 and 

     * Authorization: ubi_v1 t=***ticketValueFromTheLevel0Login***

 * Response:

   * Vary: Authorization

     ```json
     {"accessToken":"*token*","refreshToken":"*token*"}
     ```

   * accessToken and refreshToken

## PUT /accounts/*accountId*/presence

* Use: Notify the Trackmania Servers that this user is online (???)

* Headers: **1 and 2.1**

* Response:

  * Vary: Authorization

    ```json
    {"accountId":"*accountId*","isOnline":true,"refreshTime":900}
    ```

  * accountId confirmation, isOnline e refreshTime

## GET /accounts/*accountId*/policies/global/rules

* Use: Get all the policies associated with a user (?)

* Headers: **1 and 2.1**

* Response:

  * Vary: Authorization

    ```json
    [{"policyRuleId":"052d3167-df15-4279-a8a3-37eda62b5065","policyRuleName":"client_OpenMainMenu","policyRuleValue":"1"}, ......]
    ```

  * Array of policyRuleId, policyRuleName and policyRuleValue

## GET /accounts/*accountId*/client/config

* Use: Get the configuration of the client from this account

* Headers **1 and 2.1**

* Response:

  * Vary: Authorization

    ```json
    {"settings":{"CDVBase":*number*,"CDVSignature":"*signature*","CDVSignatureKeyId":*number*,"PackageKeyDeleteThreshold":*number*,"PackageKeyExpirationThreshold":*number*}}
    ```

  * settings containing CSVBase, CSVSignature, CSVSignatureKeyId, PackageKeyDeleteThreshold and PackageKeyExpirationThreshold

## GET /accounts/*accountId*/client/signature?signature=*id related to last endpoint described*

* Use: Download the client signature

* Headers: **1 and 2.1**

* Response

  * Vary: Authorization

    ```json
    {"signature":"*signature*","public_key_id":1}
    ```

  * signature, public_key_id = 1(maybe deactivated or not used)

## GET /accounts/*accountId*/encryptedPackage/key

* Use: Download the public key of the user

* Headers: **1 and 2.1**

* Response:

  * Vary: Authorization

    ```
    "-----BEGIN PUBLIC KEY-----*public Key*-----END PUBLIC KEY-----\n"
    ```

  * Public Key, idk when is used

## GET /client/updaters/current

**This returns HTTP 422 Unprocessable Entity, still I will document how the game requested**

* Use: ***Idk***

* Headers: **1 and 2.1**

* Response

  * Vary: Authorization

    ```json
    {"code":"C-AD-01-01","correlation_id":"*id*","error_id":"0ecd55a7-bb50-4805-ae85-3711de0ad315","message":"Unknown client updater."}
    ```

  * ***Error, idk why***

## GET /accounts/*accountId*/client/urls

* Use: ***Idk***

 * Headers: **1 and 2.1**

 * Response

   * Vary: Authorization

     ```json
     {"test":"http:\/\/test.nadeo.com"}
     ```

   * ***maybe not used at all, or only used with specific conditions?***

## GET /accounts/*accountId*/client/plugins

* Use: **Idk**

* Headers: **1 and 2.1**

* Response:

  * Vary: Authorization

    ```json
    ["Media\/ManiaApps\/Nadeo\/System\/TrackmaniaAuth.Script.txt","Media\/ManiaApps\/Nadeo\/System\/keys\/Keys.Script.txt","Media\/ManiaApps\/Nadeo\/System\/report\/Report.Script.txt","Media\/ManiaApps\/Nadeo\/System\/settings\/Settings.Script.txt"]
    ```

  * Array containing list of scripts, this one are default i guess

## GET /zones

* Use: Get all the IDs from all the zones for internal use and to be able to call endpoints using this IDs

* Headers: **1 and 2.1**
* Response:
  * Big JSON with all the zones ids, names, links to flags, etc.
  * Each zone has an identifier called **zoneId** and it can be a children of other zones, so there is also a **parentId** 
  * The root of all zones is World that has a null parentId

## GET /accounts/*accountId*/zone

* Headers: **1 and 2.1**

* Response

  * Vary: Authorization

    ```json
    {"accountId":"*accountId*","timestamp":"2020-07-01T16:56:00+00:00","zoneId":"*zoneId*"}
    ```

  * accountId: again
  * timestamp: first time you joined Trackmania. In the above example it was on 2020-07-01, the day of game's launch
  * zoneId: ID of the zone of the player. See GET /zones for more info.

---

**This was all the requests the game make when you open Trackmania**

---

## POST /v2/authentication/token/nadeoservices

* Use: Login to get a Level 2 Token to be used in NadeoLiveServices, using the Level 1 token

* Headers: **1 and 2.1**

  * Content-Type: application/json
  
* Body:

  ```json
  {"audience" : "NadeoLiveServices"}
  ```

  or

  ```json
  {"audience" : "NadeoClubServices"}
  ```

  The type of audience used will affect where the token can be used

  ***Note that if you don't provide a json body, you get a token for audience `NadeoServices`***

* Response

  * Vary: Authorization

    ```json
    {"accessToken":"*token*","refreshToken":"*token*"}
    ```

  * accessToken and refreshToken

## POST /v2/authentication/token/basic

* Use: Login using Basic Authentication

* Headers:

  * Authorization: Basic authentication with username/password set to your dedicated server login/password
  * Content-type: application/json

* Body:

  ```json
  {"audience" : "NadeoLiveServices"}
  ```

  or

  ```json
  {"audience" : "NadeoClubServices"}
  ```

  The type of audience used will affect where the token can be used

  ***Note that if you don't provide a json body, you get a token for audience `NadeoServices`***

* Response

  * Vary: Authorization

    ```json
    {"accessToken":"*token*","refreshToken":"*token*"}
    ```

  * accessToken and refreshToken

## GET /mapRecords/?accountIdList=*some ids* *other parameters like seasonId or addPersonalBest* 

* Use: Get more info about a record, and the url leads to a ghost file

* Headers: **1 and 2.1**

* Params
  * accountIdList - list of accountIds
  * addPersonalBest - true or false, idk what is this for

* Response

  ````json
  [{"accountId":"*accountId*","filename":"*filename.replay.gbx*","gameMode":"TimeAttack","gameModeCustomData":"","mapId":"*mapId*","medal":4,"recordScore":{"respawnCount":4294967295,"score":0,"time":36217},"removed":false,"scopeId":"*scopeId*","scopeType":"Season","timestamp":"2020-07-05T12:57:04+00:00","url":"*url*"}, .........]
  ````

  

## GET /maps/?mapIdList=*ListMapIds*

* Use: Get info about a map and be able to download the map with the link included in the response

* Headers: **1 and 2.1**

* Params

  * mapIdList = List of Map Ids separated by %

* Response

  ```json
  [{"author":"*accountId*","authorScore":69537,"bronzeScore":105000,"collectionName":"Stadium","environment":"Stadium","filename":"Formule Gou1 .Map.Gbx","goldScore":74000,"isPlayable":true,"mapId":"*mapId*","mapUid":"*mapUid*","name":"Formule Gou1 ","silverScore":84000,"submitter":"*accountId*","timestamp":"2020-07-20T12:23:02+00:00","fileUrl":"https:\/\/prod.trackmania.core.nadeo.online\/storageObjects\/5d095673-130d-449a-a992-9eca4caab4ee","thumbnailUrl":"https:\/\/prod.trackmania.core.nadeo.online\/storageObjects\/4778b079-af49-4234-9e2b-beb60f1d901d.jpg"}, ***...***]
  ```

  * List of objects with author, authorScore, bronzeScore, silverScore, goldScore, collectionName(*always Stadium?*), environment(*always Stadium?*), filename, isPlayable,mapId,mapUid,name,submitter(*not confirmed but probably accountId*), timestamp, fileUrl, thumbnailUrl

## GET /trophies/settings

* Use: Get Trophies

* Headers: **1 and 2.1**
* Response
  * Vary: Authorization
  
    ```json
    {"gain":{"Solo":{"SoloMedal":{"ClubOfficial":{"allBronze":{"t1Count":1},"allSilver":{"t2Count":1},"allGold":{"t3Count":1},"allAuthor":{"t4Count":1}},"ClubUnofficial":{"allSilver":{"t1Count":1},"allGold":{"t2Count":1},"allAuthor":{"t3Count":1}},"SoloAll":{"allAuthor":{"t5Count":5}},"SoloBlack":{"allBronze":{"t2Count":1},"allSilver":{"t3Count":1},"allGold":{"t4Count":1},"allAuthor":{"t5Count":1}},"SoloBlue":{"allBronze":{"t1Count":1},"allSilver":{"t2Count":1},"allGold":{"t3Count":1},"allAuthor":{"t4Count":1}},"SoloGreen":{"allBronze":{"t1Count":1},"allSilver":{"t2Count":1},"allGold":{"t3Count":1},"allAuthor":{"t4Count":1}},"SoloRed":{"allBronze":{"t2Count":1},"allSilver":{"t3Count":1},"allGold":{"t4Count":1},"allAuthor":{"t5Count":1}},"SoloWhite":{"allBronze":{"t1Count":1},"allSilver":{"t2Count":1},"allGold":{"t3Count":1},"allAuthor":{"t4Count":1}},"TrackOfTheDay":{"allGold":{"t3Count":1},"allAuthor":{"t4Count":1}}}}}}
    ```
  
  * An object called Gain, with only another object called Solo, and then SoloMedal, and then for every other object inside this one (ClubOfficial, ClubUnofficial, SoloAll, SoloBlack, SoloBlue, SoloGreen, SoloRed, SoloWhite, TrackOfTheDay) it returns if the person obtained all bronze, silver, gold and author medal of that group. Maybe the solo trophies are calculated by checking if the user already win all the medals from specific group?

## GET /maps/?mapUidList=*mapUidList* (this one is with Uids!!!)

* Use: Get info about a map and be able to download the map with the link included in the response

* Headers: **1 and 2.1**
* Params
  
  * mapUidList=List of map Uids separated by %
* Response
  * Vary: Authorization
  
    ````json
    {"author":"2116b392-d808-4264-923f-2bfcfa60a570","authorScore":53291,"bronzeScore":80000,"collectionName":"Stadium","environment":"Stadium","filename":"Summer 2020 - 24.Map.Gbx","goldScore":56000,"isPlayable":true,"mapId":"c1510106-6be4-4b29-8180-67c27317b0b2","mapUid":"0fJFNOS8ZzfDA6fJQrr5JU0JIom","name":"Summer 2020 - 24","silverScore":64000,"submitter":"2116b392-d808-4264-923f-2bfcfa60a570","timestamp":"2020-06-23T15:58:29+00:00","fileUrl":"https:\/\/prod.trackmania.core.nadeo.online\/storageObjects\/a2e32718-f6fa-423c-a0dd-8bc415cdd48d","thumbnailUrl":"https:\/\/prod.trackmania.core.nadeo.online\/storageObjects\/3c36a826-93f2-4245-b6c3-851f3b0d907c.jpg"}
    ````

## GET /seasons/*seasonid*

* Use: Get info about a season, with all the details, included info about map ids 

* Headers: **1 and 2.1**

* Response

  ````json
  {"creationTimestamp":"2020-06-23T17:08:48+00:00","creatorId":"f4c1d5cd-a018-402e-b69c-152f41ad1684","endTimestamp":"2100-01-01T00:00:00+00:00","gameMode":"TimeAttack","gameModeCustomData":"","isOfficial":true,"name":"Summer 2020 #1","recordScoreType":"Time","seasonId":"3987d489-03ae-4645-9903-8f7679c3a418","seasonMapList":[{"mapId":"20fbc899-920e-471c-a07e-d2bfabcaff06","timestamp":"2020-06-23T17:08:48+00:00"}, .........], "startTimestamp":"2020-06-23T17:08:00+00:00"}
  ````

  * creationTimestamp, creatorId, endTimestamp, gameMode, gameModeCustomData, isOfficial, name, recordScoreType, seasonId, seasonMapList with objects with mapId and timestamp, and startTimestamp

## GET /webidentities/?accountIdList=*accountIdsList*

* Use: Get profile id's based on account ids

* Headers: **1 and 2.1**

* Params

  * accountIdList = list of accountIds separated by %2c

* Response

  * Vary: Authorization

````json
[{"accountId":"*accountId*","provider":"ubiServices","uid":"*profileId*","timestamp":"2020-05-07T21:15:24+00:00"}]
````

  * array of accountId, provider, uid and timestamp 

## HEAD /storageObjects/*someFileName* 

***This Redirects to others servers, probably to load balancing between different servers since is for downloading archives***

* Use: Obtain address of location of the file we want to download

* Headers
  * Accept-Encoding: deflate, gzip
  * User-Agent: ManiaPlanet/3.3.0 (Win64; rv: 2020-07-23_20_22; context: none; distro: UPLAY)
  * Accept-Language: en-US,en
* Response
  * HTTP Code 307 with Location Header having a URL to the file

## GET /encryptedPackages/versions/?checksumList=*checksum*

* Use: **Idk, but this is used when we want to upload a new mapRecord**

* Headers: **1 and 2.1**

* Response

  ````json
  [{"contentChecksum":"*someChecksum*","encryptedPackageId":"*Id*","encryptedPackageVersionId":"*version*","impostorUrl":"*link*","timestamp":"*timestamp*"}]
  ````

  * contentChecksum, encryptedPackageId, encryptedPackageVersionId, impostorUrl, timestamp
  * The Url transfer a Pack File
  * ***Idk where the checksum used in the request URI came from***

## POST /mapRecords

* Use: Upload a new map record

* Headers: **1 and 2.1**
  * Content-Type: multipart/form-data; boundary=Boundary
  * Content-Length: 62772
* Body
  * MultiPart file, one part with json and another with binary content (equivalent to a GBX file representing a Ghost File)
  
    ````json
    {"recordScore" : {"time" : *time*,"score" : 0,"respawnCount" : 4294967295},"medal" : 1,"gameModeCustomData" : "","gameMode" : "TimeAttack","exeVersion" : "Trackmania date=2020-07-23_20_22 Svn=106224 GameVersion=3.3.0","exeChecksum" : *exeChecksum*,"encryptedPackageVersionId" : "*PackageVersionID*","mapId" : "*mapId*"}
    ````
  
  * the encryptedPackageVersionId is referent to the packageVersionId of the GET /encryptedPackages/versions/?checksumList=*checksum*, so they are correlated
  
  * binary content with the ghost file
* Response
  
  * ***Didnt find the response for this one and can't replicate, I will try making another record in a map to get the response***

## GET /servers/*someId*

* Use: Get info about a server

* Headers: **1 and 2.1**
* Response
  * Vary: Authorization
  
    ````json
    {"accountId":"*accountId*","gameMode":"TimeAttack","gameModeCustomData":"","ip":"*ip*","isPrivate":false,"login":"*login*","name":"Summer 2020","playerCount":21,"playerCountMax":75,"port":2368,"timestamp":"*timestamp*","titleId":"Trackmania"}
    ````
  
  * accountId (creator of the server?), gameMode, gameModeCustomData, ip, isPrivate, login, name, playerCount, playerCountMax, port, timestamp, titleId

## GET /accounts/*accountId*/trophies/lastYearSummary

* Use: Get the current trophies from an account

* Headers: **1 and 2.1**

* Response

  ````json
  {"accountId":"*accountId*","points":499,"t1Count":9,"t2Count":19,"t3Count":3,"t4Count":0,"t5Count":0,"t6Count":0,"t7Count":0,"t8Count":0,"t9Count":0,"timestamp":"*timestamp*"}
  ````

  * accountId, points, t1count, t2count, t3count, t4count, t5count, t6count, t7count, t8count, t9count (t* referent to the level of the trophies)



## TODO

* Use this endpoint **GET /api/routes?usage=Client** or **GET /api/routes** to check for the others endpoints
