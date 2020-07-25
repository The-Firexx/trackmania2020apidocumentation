# Routes live-services.trackmania.nadeo.live

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
* Accept: application/json
* Content-Type: application/json

#### 2

Authorization: nadeo_v1 t=

#### 2.1

accessToken from Level 1

#### 2.2

accessToken from Level 2 - NadeoLiveServices

#### 2.3

accessToken from Level 2 - NadeoClubServices

## GET /api/token/campaign/official?offset=0&length=1

* Use: Obtain all the seasons, including seasonsIds, groupIds, mapIds, etc.

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"campaignList":[{"id":130,"seasonUid":"3987d489-03ae-4645-9903-8f7679c3a418","name":"Summer 2020","color":"","useCase":0,"clubId":null,"leaderboardGroupUid":"3987d489-03ae-4645-9903-8f7679c3a418","publicationTimestamp":1592932080,"publishedDate":1592932080,"year":-1,"week":-1,"day":-1,"monthYear":-1,"month":-1,"monthDay":-1,"published":true,"playlist":[{"id":1028,"position":0,"mapUid":"XJ_JEjWGoAexDWe8qfaOjEcq5l8"}, ......], "latestSeasons":[{"uid":"3987d489-03ae-4645-9903-8f7679c3a418","name":"Summer 2020 #1","startTimestamp":1592932080,"startDate":1592932080,"endTimestamp":null,"endDate":null,"relativeStart":-2682526,"relativeEnd":null,"campaignId":130,"active":true}], ,"categories":[{"position":0,"length":1,"name":"0"},{"position":1,"length":1,"name":"1"},{"position":2,"length":1,"name":"2"},{"position":3,"length":1,"name":"3"},{"position":4,"length":1,"name":"4"}],"media":{"buttonBackgroundUrl":"","buttonForegroundUrl":"","popUpBackgroundUrl":"","popUpImageUrl":"","liveButtonBackgroundUrl":""}}],"itemCount":1}
    ```

  * campaignList, with each object representing a campaing with a id, seasonUid, name, color, useCase, clubId, leaderboardGroupUid, publicationTimestamp, publishedDate, year, week, day, monthYear, month, monthDay, published, playlist that contains the maps, each one with an Id, position and mapUid, and then latestSeason with Uid, name, startTimeStamp, startSate, endTimeStamp, endDate, relativeStart, relativeEnd, campaignId, active(boolean), and then categories with objects containing position, length, name, and then media with buttonBackgroundUrl, buttonForegroundUrl, popUpBackgroundUrl, popUpImageUrl, liveButtonBackgroundUrl, and then finally with a itemCount

## GET /api/token/campaign/month?offset=0&length=1

* Obtain all the track of the days, with their respective mapUid and seasonUid

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"monthList":[{"year":2020,"month":7,"lastDay":31,"days":[{"campaignId":173,"mapUid":"g7l2eO_x9z4HWGGYj8dVBCDSTEg","day":2,"monthDay":1,"seasonUid":"33181f18-1b3d-4ed4-94b3-92e4c809e1e9","relativeStart":-2002606,"relativeEnd":-1905406,"leaderboardGroup":null}, ......], "media":{"buttonBackgroundUrl":"","buttonForegroundUrl":"","popUpBackgroundUrl":"","popUpImageUrl":"","liveButtonBackgroundUrl":""}}],"itemCount":1}
    ```

  * monthlist, each object inside this array represents a month of track of the day, each one with a array representing the maps, each one with campaignId, mapUid, day (day of the week), monthDay, seasonUid(each track have his own season), relativeStart, relativeEnd (to check how many time the track started and how many time his left to be end, in this case both are negative, so the track is already closed), leaderboardGroup. Then, after the array of maps comes the media object with buttonBackgroundUrl, buttonForegroundUrl, popUpBackgroundUrl, popUpImageUrl, liveButtonBackgroundUrl. Then, after this all, the last value is itemCount, maybe representing the number of months that are in the JSON

## GET /api/token/club/campaign?offset=0&length=75&sort=popularity&order=DESC

* Use: List clubs campaigns (used when we are in Solo Screen and looking for Club Campaigns)

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"clubCampaignList":[{"clubId":10,"clubIconUrl":"http:\/\/trackmania-prod-nls-file-store-s3.mdc.akamaized.net\/club\/10\/logo\/5eda9e8eba5af.png?updateTimestamp=1591385745.png","clubDecalUrl":"","campaignId":25,"publicationTimestamp":1591434456,"publishedOn":1591434456,"creationTimestamp":1591434449,"activityId":51,"mediaUrl":"http:\/\/trackmania-prod-nls-file-store-s3.mdc.akamaized.net\/club\/10\/activity\/51\/5edb5cd1ed2e1.png?updateTimestamp=1591434454.png","name":"MrLag\u0027s Collection","campaign":{"id":25,"seasonUid":"NLS-mKwyfRyFgiEMJk7Z4d4J7M4VGQ0rRgSOgrk","name":"MrLag\u0027s Collection","color":"","useCase":2,"clubId":10,"leaderboardGroupUid":"NLS-mKwyfRyFgiEMJk7Z4d4J7M4VGQ0rRgSOgrk","publicationTimestamp":1591434456,"publishedDate":1591434456,"year":-1,"week":-1,"day":-1,"monthYear":-1,"month":-1,"monthDay":-1,"published":true,"playlist":[{"id":313,"position":0,"mapUid":"TC7VeIu0YlBPL28pQEVCIB4U3U7"},{"id":314,"position":1,"mapUid":"cauJGEKRavl8OCFq4Bn7zSR6s_f"},{"id":328,"position":2,"mapUid":"XHQXucIBMhpEtF5vzsfuZAC46bg"},{"id":331,"position":3,"mapUid":"g7l2eO_x9z4HWGGYj8dVBCDSTEg"},{"id":409,"position":4,"mapUid":"klhcYiu6u7fHh1mVbniODsNsE5k"},{"id":628,"position":5,"mapUid":"oL9m6YV0WvBJxrXaxS5CGsmYaO9"},{"id":783,"position":6,"mapUid":"zfanSjNNWvSsBUktpFL5VdEMOYh"},{"id":785,"position":7,"mapUid":"aFQ5VqxIzVF0cvvpyVm0NcDn6H3"},{"id":819,"position":8,"mapUid":"n0Sk7NEXWpImPRJj01sAQ_DJO0c"},{"id":832,"position":9,"mapUid":"QAIa5QzuymQu2Bm0ivsHnLq2150"},{"id":1055,"position":10,"mapUid":"YoMVhGI13Q1TeAsPAqkzbi20tn9"},{"id":1161,"position":11,"mapUid":"DR9ERWb19R9QEwb10GrHCtmj0il"},{"id":1162,"position":12,"mapUid":"ExPmQDTImDYrHypihjmN7JhvBV5"},{"id":1163,"position":13,"mapUid":"19EACHLJwIpqxv1l7EneRG4BLJl"},{"id":1330,"position":14,"mapUid":"OhpuXkzfkjChnc35TJRG5AZEMCm"},{"id":5124,"position":15,"mapUid":"gasy2RLKMS7l8BzvZorvWGBXm34"},{"id":7847,"position":16,"mapUid":"tX5RQBdmiVvlinPp9BJ62cpV7P4"}],"latestSeasons":[{"uid":"NLS-mKwyfRyFgiEMJk7Z4d4J7M4VGQ0rRgSOgrk","name":"MrLag\u0027s Collection #1","startTimestamp":1595599135,"startDate":1595599135,"endTimestamp":null,"endDate":null,"relativeStart":-15446,"relativeEnd":null,"campaignId":25,"active":true}],"categories":[{"position":0,"length":5,"name":"MrLag\u0027s Collection"}],"media":{"buttonBackgroundUrl":"","buttonForegroundUrl":"","popUpBackgroundUrl":"","popUpImageUrl":"","liveButtonBackgroundUrl":""}},"popularityLevel":3}, ......], "maxPage":15, "itemCount":1098
    ```

  * clubCampaignList, with each object having a clubId, clubIconUrl, clubDecalUrl, campaignId, publicationTimeStamp, publishedOn, creationTimestamp, activityId, mediaUrl, name, campaign with a id, seasonUid, name, color, useCase, clubId, leaderboardGroupUid, publicationTimestamp, publishedDate, year, week, day, monthYear, month, monthDay, published, playlist that contains the maps, each one with an Id, position and mapUid, and then latestSeason with Uid, name, startTimeStamp, startSate, endTimeStamp, endDate, relativeStart, relativeEnd, campaignId, active(boolean), and then categories with objects containing position, length, name, and then media with buttonBackgroundUrl, buttonForegroundUrl, popUpBackgroundUrl, popUpImageUrl, liveButtonBackgroundUrl, and then popularityLevel. After all the objects of the clubs, we have a maxPage and a itemCount

## GET /api/token/leaderboard/group/*groupId*/map?scores%*mapId*=*your record*

* Use: Obtain your position in the leaderboard for a specific group and a list of map

* Headers: **1 and 2.2**

* Params

  * scores%*mapId*=*your time record (ex: 00:19:254 is 19254)*  **AND THIS IS A LIST**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"0fJFNOS8ZzfDA6fJQrr5JU0JIom":{"groupUid":"3987d489-03ae-4645-9903-8f7679c3a418","mapUid":"0fJFNOS8ZzfDA6fJQrr5JU0JIom","score":48745,"zones":[{"zoneId":"301e1b69-7e13-11e8-8060-e284abfd2bc4","zoneName":"World","ranking":{"position":1995,"length":0}},{"zoneId":"301e2106-7e13-11e8-8060-e284abfd2bc4","zoneName":"Europe","ranking":{"position":1811,"length":0}}, ***...***}
    ```

  * An JSON object, with each atribute inside him representing a mapUid that contains the groupUid, mapUid, score (our record, and the one passed by query parameter), and then zones array with objects having zoneId, zoneName, position and length

## GET /api/token/leaderboard/group/*groupId*/map

* Use: Returns your record in everymap of that group, and your position in each zone

* Headers: **1 and 2.2**

* Response:

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"5w5yGqmOIKOpUGxAEhonlGP04W4":{"groupUid":"NLS-jVyu9CVZvWCVNxudXYvwS92FRdOEcOPysOK","mapUid":"5w5yGqmOIKOpUGxAEhonlGP04W4","score":57223,"zones":[{"zoneId":"301e1b69-7e13-11e8-8060-e284abfd2bc4","zoneName":"World","ranking":{"position":1201,"length":0}},{"zoneId":"301e2106-7e13-11e8-8060-e284abfd2bc4","zoneName":"Europe","ranking":{"position":1093,"length":0}}, ......]}, ......}
    ```

  * JSON object with each attribute representing the mapId of each track on that group, and each object have a groupUid, mapUid, score (your score), zones array with each object having zoneId, zoneName, ranking having position and length

## GET /api/token/leaderboard/group/*groupId*/

* Use: Get your position in a group (ex: overall ranking on Summer Season 2020 in world, country, etc.)

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked
  * Vary: Authorization

  ```json
  {"groupUid":"3987d489-03ae-4645-9903-8f7679c3a418","sp":"17284","zones":[{"zoneId":"301e1b69-7e13-11e8-8060-e284abfd2bc4","zoneName":"World","ranking":{"position":1553,"length":0}}, ......}
  ```

  * groupUid, sp, array of zones with zoneId, zoneName, ranking having position and length

## GET /api/token/leaderboard/group/*groupId*/top

* Use: Get the top leaders on a group (ex: top rankings on Summer Season 2020 in world, country, etc.)

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"groupUid":"3987d489-03ae-4645-9903-8f7679c3a418","tops":[{"zoneId":"301e1b69-7e13-11e8-8060-e284abfd2bc4","zoneName":"World","top":[{"accountId":"*accountId*","zoneId":"30207cd0-7e13-11e8-8060-e284abfd2bc4","zoneName":"Japan","position":1,"sp":"356215"}, ***...***], ***...***]}
    ```

  * groupUid, tops array with objects having zoneId, zoneName and top array containing objects having accountId, zoneId, zoneName, position and sp

## GET /api/token/leaderboard/group/*groupId*/map/*mapId*/top?score=*your record*

* Use: Obtain the top leaders on a specific map (i dont think the query param score is being used, although they used that way...)

* Headers: **1 and 2.2**

* Params:

  * score=*your time record (ex: 00:19:254 is 19254)*

* Response

  ```json
  {"groupUid":"3987d489-03ae-4645-9903-8f7679c3a418","mapUid":"XJ_JEjWGoAexDWe8qfaOjEcq5l8","tops":[{"zoneId":"301e1b69-7e13-11e8-8060-e284abfd2bc4","zoneName":"World","top":[{"accountId":"*accountId*","zoneId":"30229617-7e13-11e8-8060-e284abfd2bc4","zoneName":"Vaud","position":1,"score":19454}, ***...***], ***...***]}
  ```

  * An JSON object with groupUid, mapUid and tops, containing objects for each zone of yours with zoneId, zoneName and top array with objects having accountId, zoneId, zoneName, position and score

## GET /api/token/leaderboard/group/Personal_Best/map/*mapId*/top

* Use: Get the top leaders of a map, with no restriction of a group like the others endpoints

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"groupUid":"Personal_Best","mapUid":"XJ_JEjWGoAexDWe8qfaOjEcq5l8","tops":[{"zoneId":"301e1b69-7e13-11e8-8060-e284abfd2bc4","zoneName":"World","top":[{"accountId":"*accountId*","zoneId":"30229617-7e13-11e8-8060-e284abfd2bc4","zoneName":"Vaud","position":1,"score":19454}, ***...***], ***...***]}
    ```

  * An JSON object with groupUid, mapUid and tops, containing objects for each zone of yours with zoneId, zoneName and top array with objects having accountId, zoneId, zoneName, position and score

## GET /api/token/leaderboard/group/Personal_Best/map/*mapId*/surround/1/1

* Use: Get the surrounding leaders around your score on a map, with no restriction of a group like the others endpoints (this one is used in that little leaderboard in game)

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"groupUid":"Personal_Best","mapUid":"XJ_JEjWGoAexDWe8qfaOjEcq5l8","tops":[{"zoneId":"301e1b69-7e13-11e8-8060-e284abfd2bc4","zoneName":"World","top":[{"accountId":"*accountId*","zoneId":"301fa93b-7e13-11e8-8060-e284abfd2bc4","zoneName":"Nord","position":1162,"score":19928}
    ```

  * An JSON object with groupUid, mapUid and tops, containing objects for each zone of yours with zoneId, zoneName and top array with objects having accountId, zoneId, zoneName, position and score

## GET /api/token/club/follower/map/*mapId*?seasonId=*seasonUid*

* Use: ***Idk***

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"accountIdList":[]}
    ```

## GET /api/token/club/player-vip/map/*mapId*?seasonId=*seasonUid*

* Use: ***Idk***

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"accountIdList":[]}
    ```

## GET /api/token/leaderboard/group/*groupId*/map/*mapId*/level?score=*your record*

* Use: This one seems specific to some zone, I'm not 100% sure where is being used

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"groupUid":"3987d489-03ae-4645-9903-8f7679c3a418","mapUid":"XJ_JEjWGoAexDWe8qfaOjEcq5l8","levels":[{"zoneId":"*zoneId*","zoneName":"*zoneName*","level":[{"accountId":"*accountId*","zoneId":"*zoneId*","zoneName":"*zoneName*","position":14,"score":19908}, ***...***], ***...***]}
    ```

## POST /api/token/leaderboard/trophy/player

* Use: I think is to obtain the trophys and their position from a list of players passed on the body of the request

* Headers: **1 and 2.2**

  * Accept: application/json
  * Content-Type: application/json
  * Content-Length: 

* Body

  ```json
  {"listPlayer":[{"accountId":"*accountId*"}]}
  ```

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"rankings":[{"countPoint":75638,"accountId":"*accountId*","echelon":5,"zones":[{"zoneId":"301e1b69-7e13-11e8-8060-e284abfd2bc4","zoneName":"World","ranking":{"position":4122,"length":0}}, ***...***]}], "length": 0}
    ```

  * ranking with countPoint, acountId, echelon and zones array with each object having zoneId, zoneName and ranking having position and length

## GET /api/token/club/room?offset=0&length=75&sort=popularity&order=DESC

* Use: This is used to obtain the clubs in the Live section of the game

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"clubRoomList":[{"id":283,"clubId":97,"nadeo":true,"roomId":50,"campaignId":null,"playerServerLogin":null,"activityId":283,"mediaUrl":"http:\/\/trackmania-prod-nls-file-store-s3.mdc.akamaized.net\/club\/97\/activity\/283\/5f0866a0545bf.png?updateTimestamp=1594386082.png","name":"Tona\u0027s maps","room":{"id":50,"name":"Tona\u0027s maps","region":null,"serverAccountId":"","maxPlayers":60,"playerCount":393,"maps":["sIYZ2whAcmFytSVRZWPJkByjPP8","gL7NrGjG0GC91nJazHyGwPb_Iok","hg__4dAM5CN1sUxajb9L95olDG1","sZLy_bJbge06NkOTslD9x3Jfq90","HA1BTE5m4y8bsE4T_b0tYcWEwTd","rtzP7y8EgR8jY4MJ0LpK13nALR2","rbWSXxqnEhLecjctuUd_Ebw8G7m","tXQ4XA1DTe7HF5o571sC0oZJ8Ti","6I9T69k86vRcWr4ih4sqSvjQFb3","oBqrQ2BmIMOgrNmbrQSwKdCwBL3"],"script":"TrackMania\/TM_TimeAttack_Online.Script.txt","scriptSettings":{"S_ForceLapsNb":{"key":"S_ForceLapsNb","value":"-1","type":"integer"},"S_DecoImageUrl_Screen16x9":{"key":"S_DecoImageUrl_Screen16x9","value":"http:\/\/trackmania-prod-nls-file-store-s3.mdc.akamaized.net\/club\/97\/screen_16x9\/5efdfb06b545d.dds?updateTimestamp=1593703174.dds","type":"text"}}},"popularityLevel":3,"creationTimestamp":1592242462}, ***...***], "maxPage":86, "itemCount":6397}
    ```

  * clubRoomList with objects having id, clubId, nadeo, roomId, plaerServerLogin, activityId, mediaUrl, name, room having id, name, region, serverAccountId, maxPlayers, playerCount, maps array with strings of mapUids, script, scriptSettings having a S_ForceLapsNb object with key, value and type, and S_DecoImageUrl_Screen16x9 with key, value and type. Then have a popularityLevel and creationTimestamp

## GET /api/token/channel/officialhard

* Use: I think this is specific for the arcade button, where he obtains the information about the current room and the next room

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"uid":"officialhard","name":"Official","playerCount":737,"currentTimeSlot":{"startTimestamp":1595613600,"endTimestamp":1595617200,"name":"Summer 2020","maps":["XJ_JEjWGoAexDWe8qfaOjEcq5l8","zFK9sy3nRLa6FGSpuk_gw0cHLv7","xfRvyL9ByoJoPhlAvcNzbc4xD88","8rWFH6JI2N1UuHeaS9dmMkTojS","eWR2OWAaiqQOISa_0roXlpsnQLl","NlKBKke_lk9hwhoEMb6rBQrsWC5","OG0yFZ4bA1iiybF7n4gaZkFO6m9","iWUvrk1X45PaUmKv6HUDak4W6V2","5weePaThiuxiK4mSHOCokBV6bTg","oTGP3jwCiubHBM6KtuR_aCtGWZi","gMsrsG59cdouiAoahyk7wOaPPC3","EY3IfWHWGUtreJzWmAWp00ZT6z2","1MPMjPNGKW_U2Aa1RGyfPDnJVhd","uQrUHGT16AptHdxkUKL3MWuh0Gm","159XBIpjid7Wh4mjIRQ6wazyme4","8JfhDBlUSjG2qf9hqssAJupE0rc","4dRIXY5T5CMh6LPcL88l0gEpBkl","oSqyiU8CN8A4KnYRsqgcIOshYl2","VjBmIAFe_vihp4dA6gXyxauMh_1","bTxEqrds5pszV3PZTdK57AnYWfd","tHdTCbauyKWB_ft2NVRznkCE4rk","dAUOBz9H2iKzyo8HURb3Ce3cwT9","FcNO1D7hn9nLuCrjqSA5_7slkR1","0fJFNOS8ZzfDA6fJQrr5JU0JIom","2katsDjZmPOeQYE94jkbnSoJA64"],"currentMap":"iWUvrk1X45PaUmKv6HUDak4W6V2","relativeStart":-1235,"relativeEnd":2365,"mediaUrl":""},"nextTimeSlot":{"startTimestamp":1595617200,"endTimestamp":1595620800,"name":"Summer 2020","maps":["XJ_JEjWGoAexDWe8qfaOjEcq5l8","zFK9sy3nRLa6FGSpuk_gw0cHLv7","xfRvyL9ByoJoPhlAvcNzbc4xD88","8rWFH6JI2N1UuHeaS9dmMkTojS","eWR2OWAaiqQOISa_0roXlpsnQLl","NlKBKke_lk9hwhoEMb6rBQrsWC5","OG0yFZ4bA1iiybF7n4gaZkFO6m9","iWUvrk1X45PaUmKv6HUDak4W6V2","5weePaThiuxiK4mSHOCokBV6bTg","oTGP3jwCiubHBM6KtuR_aCtGWZi","gMsrsG59cdouiAoahyk7wOaPPC3","EY3IfWHWGUtreJzWmAWp00ZT6z2","1MPMjPNGKW_U2Aa1RGyfPDnJVhd","uQrUHGT16AptHdxkUKL3MWuh0Gm","159XBIpjid7Wh4mjIRQ6wazyme4","8JfhDBlUSjG2qf9hqssAJupE0rc","4dRIXY5T5CMh6LPcL88l0gEpBkl","oSqyiU8CN8A4KnYRsqgcIOshYl2","VjBmIAFe_vihp4dA6gXyxauMh_1","bTxEqrds5pszV3PZTdK57AnYWfd","tHdTCbauyKWB_ft2NVRznkCE4rk","dAUOBz9H2iKzyo8HURb3Ce3cwT9","FcNO1D7hn9nLuCrjqSA5_7slkR1","0fJFNOS8ZzfDA6fJQrr5JU0JIom","2katsDjZmPOeQYE94jkbnSoJA64"],"currentMap":"iWUvrk1X45PaUmKv6HUDak4W6V2","relativeStart":2365,"relativeEnd":5965,"mediaUrl":""}}
    ```

  * JSON having uid, name, playerCount, currentTimeSlot with startTimestamp, endTimestamp, name, array of mapsUids, currentMap, relativeStart, relativeEnd, mediaUrl, and then nextTimeSlot with same sctructure as currentTimeSlot 

## POST /api/token/channel/officialhard/join

* Use: Obtain the address the game uses internally to open a connection to a server, this one specific for the arcade button (i think)

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"joinLink":"#qjoin=ev747VaUQhyVop_S9krD2A"}
    ```

  * JoinLink for the game to execute

## GET /api/token/club/mine?offset=0&length=90

* Use: List all the clubs in the club section

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"clubList":[],"maxPage":0,"clubCount":0}
    ```

  * clubList, and maxPage and clubCount (probably empty cause I dont have club access, **TODO**)

## GET /api/token/club/*clubId*/member/*accountId*

* Use: I think this is used to obtain specific information about a member (the accontId not necessary have to be in the club, is just a request to know, I say this because he send a request with my ID, but I dont have club access so...)

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"accountId":"*accountId*","clubId":54,"role":"","creationTimestamp":1595614972,"creationDate":1595614972,"vip":false}
    ```

  * accountId, clubId, role, creationTimestamp, creationDate, vip

## GET /api/token/club/*clubId*/activity?offset=0&length=75&active=1

* Use: ***Idk what is activity of a club, maybe is everything about a club (skins, servers, campagins, etc.)?***

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"activityList":[{"id":41928,"name":"Trackmania Cup 2020","activityType":"competition","activityId":41928,"targetActivityId":41928,"campaignId":0,"position":10,"public":true,"active":true,"mediaUrl":"","externalId":1}, ***...***], "maxPage":1, "itemCount":10}
    ```

  * activityList array with objects having id, name, activityType, targetActivityId, campaignId, position, public, active, mediaUrl, externalId, and then maxPage and itemCount

## GET /api/token/club/*clubId*/member?offset=0&length=27

* Use: Obtain all the information about the members of a club

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"clubMemberList":[{"accountId":"*accountId*","role":"Creator","creationTimestamp":1592054772,"creationDate":1592054772,"vip":true}, ***...***], "maxPage":595, "itemCount":16055}
    ```

  * clubMemberList array with objects having accountId, role(Creator, Admin or Member), creationTimeStamp, creationDate, vip(boolean), and then maxPage and itemCount

## GET /api/token/club/*clubId*/member/request?offset=0&length=27

* Use: A request to check if this user (with the token) can enter the club **I dont have club access so the response is almost empty**

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"clubMemberList":[],"maxPage":0,"itemCount":0}
    ```

## GET /api/token/club/*clubId*/room/*activityId(?)*

* Use: ***Idk, I'm not even sure if the id after the room is the activityId or the roomId***

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"id":766,"clubId":41,"nadeo":false,"roomId":null,"campaignId":null,"playerServerLogin":"evofsb","activityId":766,"mediaUrl":"http:\/\/trackmania-prod-nls-file-store-s3.mdc.akamaized.net\/club\/41\/activity\/766\/5efc7da3105a9.png?updateTimestamp=1593605542.png","name":"$sEvo $07AFullspeed Beg","room":{"id":null,"name":"","region":null,"serverAccountId":"bc251924-d267-4702-b526-9ed4b950d729","maxPlayers":0,"playerCount":87,"maps":[],"script":"","scriptSettings":[],"serverInfo":null},"popularityLevel":1,"creationTimestamp":1592917178}
    ```

  * id (activityId?), clubId, nadeo, roomId, campaignId, playerServerLogin, acitivityId, mediaUrl, name, room with id, name, region, serverAccountId, maxPlayers, playersCount, maps array, script, scriptSettings, serverInfo, and then popularityLevel, creationTimestamp

## GET /api/token/club/bucket/skin-upload/all?offset=0&length=75&sort=popularity&order=DESC

* Use: Not 100% sure but I think is related to see the skins uploaded by the clubs

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"clubBucketList":[{"type":"skin-upload","bucketItemList":[],"bucketItemCount":2,"popularityLevel":3,"popularityValue":16055,"mediaUrl":"http:\/\/trackmania-prod-nls-file-store-s3.mdc.akamaized.net\/club\/54\/activity\/77\/5eddfd4a27fdf.png?updateTimestamp=1591606604.png","id":77,"clubId":54,"name":"zT Official Skin","creationTimestamp":1591606601}, ......], "maxPage":11, "itemCount":769}
    ```

  * clubBucketList array with objects having type(skin-upload), bucketItemList (always empty?), bucketItemCount, popularityLevel, popularityValue, mediaUrl, id, clubId, name and creationTimestamp, and then maxPage and itemCount

## GET /api/token/map-review/waiting-time

* Use: Check the waiting time of the Map Review 

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"seconds":360}
    ```

## GET /api/token/map-review/connect

* Use: Used to get the URL the game uses internally to connect to a server that have maps to review

* Headers: **1 and 2.2**

* Response

  * Transfer-Encoding: chunked

  * Vary: Authorization

    ```json
    {"joinLink":"#qjoin=ZQKOM8ZaRa2EhZeUBWcoMw"}
    ```