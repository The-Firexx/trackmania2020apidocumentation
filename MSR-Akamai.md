# Routes msr-public.aws-ubiservices.ubi.com

## GET /v4/spaces/*profileId*/configs/events

### Use:

Is used to obtain events, I think Uplay(?) wants to track you down like opening the game, entering a server, etc.

### Request:

#### Headers:

* User-Agent: UbiServices_SDK_2019.Release.13_PC64_ansi_static_cn
* Accept: \*/\*
* Authorization: Ubi_v1 t=*ticket value from UbiServices POST /v3/profiles/session*
* Content-Type: application/json
* ubi-appbuildid: 202007232022
* Ubi-AppId: 86263886-327a-4328-ac69-527f0d20a237
* Ubi-localeCode: *localeCode*
* Ubi-Populations: US_EMPTY_VALUE
* Ubi-SessionId: *SessionId*

### Response:

#### Headers:

* X-Powered-By: Express
* ETag: *Etag*
* Vary: Accept-Encoding
* Ubi-Forwarded-By: msr-us-nginx07 
* Ubi-TransactionId: *TransactionId*
* Strict-Transport-Security: max-age=63072000
* X-Frame-Options: DENY
* X-Content-Type-Options: nosniff

#### Body:

* ```json
  {"types":["game.localization","game.start","player.start","player.stats.playtime","context.start.gameMode","context.stop.gameMode","context.start.map","context.stop.map","context.stop.play","context.start.play","custom.newMapCreated","custom.stats.medal","player.progression.medal"],"s2sConfig":{"maxBatchSize":2500,"sendPeriodSeconds":1},"publicConfig":{"sendPeriodSeconds":30,"hmacEnabled":false}}
  ```

## POST /v3/profiles/me/events

***Needs more info cause the game makes a lot of this requests***

### Use:

Updates what the user is doing in the game

### Request:

#### Headers:

* User-Agent: UbiServices_SDK_2019.Release.13_PC64_ansi_static_cn
* Accept: \*/\*
* Authorization: Ubi_v1 t=*ticket value from UbiServices POST /v3/profiles/session*
* Content-Type: application/json
* ubi-appbuildid: 202007232022
* Ubi-AppId: 86263886-327a-4328-ac69-527f0d20a237
* Ubi-localeCode: xx-PT
* Ubi-Populations: US_EMPTY_VALUE
* Ubi-SessionId: 5090d904-ec68-47bd-9013-db82432ff5dc
* Content-Length: 1274
* Expect: 100-continue

#### Body:

* ```json
  {"events":[{"createdDate":"2020-07-24T18:15:35.590Z","obj":{},"typeData":{"machineId":"*machineId*","buildVersion":"202007232022","gameVersion":"Full","gameSku":"PC-WW","usSdkVersion":"2019.Release.13"},"type":"game.start","seqId":0,"contexts":[]},{"createdDate":"2020-07-24T18:15:45.503Z","obj":{"gameVersion":"Full"},"typeData":{"abtesting":{},"platformType":"uplay"},"type":"player.start","absolutePlaytime":*absolutePlayTime*,"relativePlaytime":0,"seqId":1,"contexts":[]},{"createdDate":"2020-07-24T18:15:45.503Z","obj":{"soloPlaytimeAbsolute":*soloPlaytimeAbsolute*,"livePlaytimeAbsolute":*livePlaytimeAbsolute*,"clubPlaytimeAbsolute":*clubPlaytimeAbsolute*,"localPlaytimeAbsolute":*localPlaytimeAbsolute*,"createPlaytimeAbsolute":*createPlaytimeAbsolute*},"typeData":{"playtimeAbsolute":*playtimeAbsolute*,"playtimeRelative":0},"type":"player.stats.playtime","absolutePlaytime":*absolutePlaytime*,"relativePlaytime":0,"seqId":2,"contexts":[]},{"createdDate":"2020-07-24T18:15:49.919Z","obj":{},"typeData":{"menuLanguage":"en-US","audioLanguage":"en-US","platformLanguage":"*plataformLanguage*","areSubtitlesEnabled":false,"subtitlesLanguage":"none"},"type":"game.localization","absolutePlaytime":*absolutePlaytime*,"relativePlaytime":4,"seqId":3,"contexts":[]}],"gameSessionId":"*sessionId*","playerSessionId":"*sessionId*","spaceId":"*spaceId/profileId(?)*" }
  ```

---

# Routes akamai.net (a1944.dscd.akamai.net)

## GET /club/*clubId*/activity/*nameContent* (ex:/club/3118/activity/65804/5f18c059062cf.png?updateTimestamp=1595457628.png)

### Use:

Download stuff like images

### Request:

#### Headers:

* Accept: \*/\*
* User-Agent: ManiaPlanet/3.3.0 (Win64; rv: 2020-07-23_20_22; context: none; distro: UPLAY)
* Accept-Encoding: gzip,deflate
* Accept-Language: en-US,en

### Response:

* The content(an image, etc.)