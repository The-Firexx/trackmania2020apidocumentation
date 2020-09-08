# Routes useast1-public.aws-ubiservices.ubi.com

## POST /v3/profiles/session

### Use:

Login to the ubiservices.ubi.com (the ticket obtained in the endPoint is used in the others of this API)

### Request:

#### Headers (**probably only the authorization and the Ubi-AppId is necessary**)

* User-Agent: UbiServices_SDK_2019.Release.13_PC64_ansi_static_cn
* Accept: \*/\*
* Authorization: uplaypc_v1 t=***Idk where this token came from***
* Content-Type: application/json
* ubi-appbuildid: 202007232022
* Ubi-AppId: 86263886-327a-4328-ac69-527f0d20a237
* Ubi-localeCode: xx-PT
* Ubi-Populations: US_EMPTY_VALUE
* Content-Length: 2

#### Body: {}

### Response:

#### Headers:

* Content-Type: application/json; charset=utf-8
* Expires: -1
* Ubi-Forwarded-By: ue1-p-us-public-nginx-0b4fb579f26ee4405 
* Ubi-TransactionId: cc535306-ca27-4bad-b0d6-394945896335
* Strict-Transport-Security: max-age=63072000
* X-Frame-Options: DENY
* X-Content-Type-Options: nosniff

#### Body:

* ```json
  {"platformType":"uplay","ticket":"*ticket*","twoFactorAuthenticationTicket":null,"profileId":"*profileId/userId*","userId":"","nameOnPlatform":"*username*","environment":"Prod","expiration":"2020-07-24T21:15:48.7337442Z","spaceId":"*spaceId","clientIp":"*ip*","clientIpCountry":"*countrycode*","serverTime":"2020-07-24T18:15:48.7393476Z","sessionId":"*sessionid*","sessionKey":"*sessionKey*","rememberMeTicket":null}
  ```

  * platformType, ticket, twoFactorAuthenticationTicket, profileId, userId, nameOnPlatform, environment, expriation, spaceId, clientIp, clientIpCountry, serverTime, sessionId, sessionKey, rememberMeTicket

## GET /v1/applications/86263886-327a-4328-ac69-527f0d20a237/parameters

*86263886-327a-4328-ac69-527f0d20a237 = Trackmania 2020 AppId*

### Use:

***Idk, but since the URL contains the Trackmania 2020 App Id, it's probably related to endpoints the game should use to work***

### Request:

#### Headers:

* User-Agent: UbiServices_SDK_2019.Release.13_PC64_ansi_static_cn
* Accept: \*/\*
* Authorization: Ubi_v1 t=*ticket value from POST /v3/profiles/session*
* Content-Type: application/json
* ubi-appbuildid: 202007232022
* Ubi-AppId: 86263886-327a-4328-ac69-527f0d20a237
* Ubi-localeCode: xx-PT
* Ubi-Populations: US_EMPTY_VALUE
* Ubi-SessionId: 5090d904-ec68-47bd-9013-db82432ff5dc

#### Params:

* parameterGroups=us-staging,us-sdkClientUrlsPlaceholders,us-sdkClientClub,us-sdkClientFeaturesSwitches,us-sdkClientLogin,us-sdkClientUrls,us-sdkClientChina

### Response:

#### Headers:

* Content-Type: application/json; charset=utf-8
* Expires: -1
* X-AspNet-Version: 4.0.30319
* X-Powered-By: ASP.NET
* Ubi-Forwarded-By: ue1-p-us-public-nginx-0b4fb579f26ee4405 
* Ubi-TransactionId: eb498bf8-ee9a-4b07-90dd-45927fa1459f
* Strict-Transport-Security: max-age=63072000
* X-Frame-Options: DENY
* X-Content-Type-Options: nosniff

#### Body:

* ```json
  {"parameters":{"us-staging":{"fields":{"spaceId":""},"relatedPopulation":null},"us-sdkClientUrlsPlaceholders":{"fields":{"baseurl_aws":{"Standard":"https://{env}public-ubiservices.ubi.com","China":"https://public-ubiservices.ubisoft.cn","China_GAAP":"https://gaap.ubiservices.ubi.com:12000"},"baseurl_msr":{"Standard":"https://msr-{env}public-ubiservices.ubi.com","China":"https://public-ubiservices.ubisoft.cn","China_GAAP":"https://gaap.ubiservices.ubi.com:12000"},"baseurl_ws":{"Standard":"wss://{env}public-ws-ubiservices.ubi.com","China":"wss://gaap.ubiservices.ubi.com:16000","China_GAAP":"wss://gaap.ubiservices.ubi.com:16000"}},"relatedPopulation":null},"us-sdkClientUrls":{"fields":{"populations":"https://{env}public-ubiservices.ubi.com/{version}/profiles/me/populations"},"relatedPopulation":null},"us-sdkClientLogin":{"fields":{"populationHttpRequestOptimizationEnabled":true,"populationHttpRequestOptimizationRetryCount":0,"populationHttpRequestOptimizationRetryTimeoutIntervalMsec":5000,"populationHttpRequestOptimizationRetryTimeoutIncrementMsec":1000},"relatedPopulation":null},"us-sdkClientFeaturesSwitches":{"fields":{"populationsAutomaticUpdate":true},"relatedPopulation":null},"us-sdkClientClub":{"fields":{"dynamicPanelUrl":"https://{env}public-ubiservices.ubi.com/v1/profiles/{profileId}/club/dynamicPanel/MyProfile.png?spaceId={spaceId}&noRedirect=true","ps4ClubWebsite":"https://static8.cdn.ubi.com/u/sites/uplay/index.html","ps4ClubWebsiteArguments":"url=/games/{deepLink}&spaceId={spaceId}&applicationId={applicationId}&context={context}&env={clubEnvName}&genomeid={applicationId}&actioncompleted={actionCompletedList}&ussdkversion={usSdkVersionName}&debug={debug}{geometry}&ticket={ticket}&profileid={profileId}","ps4PsnoLaunchPath":"psno://localhost/?response_type=code&client_id=171ca84a-371e-412b-a807-6531f3f1e454&scope=psn%3As2s&redirect_uri={ps4ClubWebsiteUrlEncoded}&state={ps4ClubWebsiteArgumentsPsnoEncoded}","xoneLaunchPath":"Ms-xbl-55C5EE27://default?url=/games/{deepLink}&context={context}&titleid={gameTitleId}&env={clubEnvName}&genomeid={applicationId}&actioncompleted={actionCompletedList}&debug={debug}&spaceId={spaceId}&applicationId={applicationId}","switchClubWebsiteUrl":"https://static8.cdn.ubi.com/u/sites/UbisoftClub/NintendoSwitch/index.html?url=/games/{deepLink}&ussdkversion={usSdkVersionName}&env={clubEnvName}&actioncompleted={actionCompletedList}&forceLang={forceLang}&profileId={profileId}&ticket={ticket}&context={context}&debug={debug}&spaceId={spaceId}&applicationId={applicationId}","stadiaClubWebsiteUrl":"https://static8.cdn.ubi.com/u/sites/UbisoftClub/Stadia/index.html?url=/games/{deepLink}&spaceId={spaceId}&applicationId={applicationId}&profileId={profileId}&env={env}&displayMode={displayMode}&locale={locale}&actioncompleted={actionCompletedList}&jotunVersion={jotunVersion}&jotunBinaryVersion={jotunBinaryVersion}&ticket={ticket}"},"relatedPopulation":null},"us-sdkClientChina":{"fields":{"tLogApplicationId":"","tLogApplicationKey":"","tLogApplicationName":"","websocketHost":"public-ws-ubiservices.ubi.com"},"relatedPopulation":null}}}
  ```

## PUT /v1/profiles/me/populations/data

### Use:

***Idk***

### Request:

#### Headers:

* User-Agent: UbiServices_SDK_2019.Release.13_PC64_ansi_static_cn
* Accept: \*/\*
* Authorization: Ubi_v1 t=*ticket value from POST /v3/profiles/session*
* Content-Type: application/json
* ubi-appbuildid: 202007232022
* Ubi-AppId: 86263886-327a-4328-ac69-527f0d20a237
* Ubi-localeCode: xx-PT
* Ubi-Populations: US_EMPTY_VALUE
* Ubi-SessionId: 5090d904-ec68-47bd-9013-db82432ff5dc
* Content-Length: 125
* Expect: 100-continue

#### Body:

* ```json
  {"spaceId":"*spaceId/accountId(?)*","data":{"US_SDK_APPLICATION_BUILD_ID":"202007232022","US_SDK_DURABLES":[]}}
  ```

### Response:

#### Headers:

* Content-Type: application/json; charset=utf-8
* Expires: -1
* X-AspNet-Version: 4.0.30319
* X-Powered-By: ASP.NET
* Ubi-Forwarded-By: ue1-p-us-public-nginx-0b4fb579f26ee4405 
* Ubi-TransactionId: bb449328-e7bd-4f1f-ac80-2f3471f2a8f2
* Strict-Transport-Security: max-age=63072000
* X-Frame-Options: DENY
* X-Content-Type-Options: nosniff

#### Body:

* ```json
  {"populations":[]}
  ```

## GET /v1/spaces/*profileId*/parameters

### Use:

***Idk, seems to have endPoints and some configuration returned***

### Request:

#### Headers:

* User-Agent: UbiServices_SDK_2019.Release.13_PC64_ansi_static_cn
* Accept: \*/\*
* Authorization: Ubi_v1 t=*ticket value from POST /v3/profiles/session*
* Content-Type: application/json
* ubi-appbuildid: 202007232022
* Ubi-AppId: 86263886-327a-4328-ac69-527f0d20a237
* Ubi-localeCode: xx-PT
* Ubi-Populations: US_EMPTY_VALUE
* Ubi-SessionId: *sessionId*

#### Params:

* parameterGroups=us-sdkClientFeaturesSwitches,us-sdkClientRemoteLogsGame,us-sdkClientSettings,us-sdkClientSettingsHttpGame,us-sdkClientSettingsHttpInternal,us-sdkClientUrls,us-sdkClientRemoteLogsInternal,us-sdkClientNotificationsGame,us-sdkClientNotificationsInternal,us-sdkClientNotificationsSpaceIds,us-override,us-sdkClientSettingsCacheTTL,us-sdkClientSettingsSecondaryStoreSync,us-sdkClientStorm,us-sdkClientSettingsWebSocketGame,us-sdkClientSettingsWebSocketInternal,NadeoServicesParameters,NadeoServicesParameters_5595,BetaParameters

### Response:

#### Headers:

* Content-Type: application/json; charset=utf-8
* Expires: -1
* X-AspNet-Version: 4.0.30319
* X-Powered-By: ASP.NET
* Ubi-Forwarded-By: ue1-p-us-public-nginx-0b4fb579f26ee4405 
* Ubi-TransactionId: 5dccdf12-2c05-4365-9b3d-d6e8fda003b6
* Strict-Transport-Security: max-age=63072000
* X-Frame-Options: DENY
* X-Content-Type-Options: nosniff

#### Body:

* ```json
  {"parameters":{"NadeoServicesParameters_5595":{"fields":{"masterserver_init_url":"https://prod.trackmania.core.nadeo.online/api/routes"},"relatedPopulation":null},"NadeoServicesParameters":{"fields":{"masterserver_init_url":"https://beta.trackmania.core.nadeo.online/api/routes"},"relatedPopulation":null},"us-sdkClientUrls":{"fields":{"allConnections":"https://{env}public-ubiservices.ubi.com/{version}/profiles/connections","allProfilesApplications":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/applications","allProfilesEntities":"https://{env}public-ubiservices.ubi.com/{version}/profiles/entities","allProfilesStats":"https://{env}public-ubiservices.ubi.com/{version}/profiles/stats","allSpacesEntities":"https://{env}public-ubiservices.ubi.com/{version}/spaces/entities","allSpacesItems":"https://{env}public-ubiservices.ubi.com/{version}/spaces/items","allSpacesOffers":"https://{env}public-ubiservices.ubi.com/{version}/spaces/offers","applications":"https://{env}public-ubiservices.ubi.com/{version}/applications/{applicationId}/configuration","applicationsMetadata":"https://{env}public-ubiservices.ubi.com/{version}/applications","applicationsParameters":"https://{env}public-ubiservices.ubi.com/{version}/applications/{applicationId}/parameters","challenge":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/challenges","challengeProgression":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/challenges/progressions","configsEvents":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/configs/events","connections":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/connections","events":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/events","friends":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/me/friends","gamesPlayed":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/gamesplayed","moderation":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/moderation/{text}","moderationPOST":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/moderation","news":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/me/news","policies":"https://{env}public-ubiservices.ubi.com/{version}/policies","profiles":"https://{env}public-ubiservices.ubi.com/{version}/profiles","profilesActions":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/club/actions","profilesApplications":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/me/applications","profilesChallenges":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/me/club/challenges","profilesEntities":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/entities","profilesExternal":"https://{env}public-ubiservices.ubi.com/{version}/profiles/external","profilesInventory":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/inventory","profilesInventoryExpiredDetails":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/inventory/expiredDetails","profilesInventoryInstances":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/inventory/instances","profilesInventoryInstancesTransactions":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/inventory/instances/transactions","profilesInventoryPrimarystore":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/inventory/primarystore","profilesInventoryTransactions":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/inventory/transactions","profilesLeaderboard":"https://{env}public-ubiservices.ubi.com/{version}/profiles/ranks","profilesMeBattlepassesSeasons":"https://{env}public-ubiservices.ubi.com/{version}/profiles/me/battlepasses/seasons","profilesMeCommunityChallenges":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/me/club/communityChallenges","profilesMeEvents":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/me/events","profilesMeInventoryPrimarystore":"https://{env}public-ubiservices.ubi.com/{version}/profiles/me/inventory/primarystore","profilesMeLeaderboard":"https://{env}public-ubiservices.ubi.com/{version}/profiles/me/ranks","profilesNotifications":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/notifications","profilesNotificationsBatch":"https://{env}public-ubiservices.ubi.com/{version}/profiles/notifications","profilesProfileChallenges":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/me/club/playerchallenges","profilesPreciseMatchmakingClient":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/matches/precise/clientstate","profilesPreciseMatchmakingMatch":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/matches/precise/matchstate","profilesRewards":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/club/rewards","profilesSeasonChallenges":"https://msr-{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/club/seasonchallenges?spaceId={spaceId}","profilesStats":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/stats","profilesStatsCard":"https://{env}public-ubiservices.ubi.com/{version}/profiles/statscard","profilesUgcPhotos":"https://{env}public-ubiservices.ubi.com/{version}/profiles/ugc/photos","profilesUgcPhotosOwn":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/ugc/photos","profilesUgcViews":"https://{env}public-ubiservices.ubi.com/{version}/profiles/ugc/{contentId}/views","profilesUgcFavorites":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/ugc/favorites","profilesUgcRatings":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/ugc/ratings","profilesUgcExternalVideos":"https://{env}public-ubiservices.ubi.com/{version}/profiles/ugc/externalvideos","profilesUgcUpdateFavorite":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/ugc/{contentId}/favorites","profilesUgcUpdateRating":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/ugc/{contentId}/ratings","recommendations":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/recommendations","remoteLogs":"https://{env}public-ubiservices.ubi.com/{version}/profiles/me/remotelog","sandboxes":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/sandboxes","spacesActions":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/actions","spacesBattlepasses":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/battlepasses","spacesBattlepassesSeasons":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/battlepasses/seasons","spacesChallengepools":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/club/challengepools","spacesChallenges":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/club/challenges","spacesCommunityChallenges":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/club/communityChallenges","spacesConfigsPrimarystore":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/configs/primarystore","spacesConfigsSsiAttributes":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/configs/secondarystore/instances/attributes","spacesConfigsSsiListsOfAttributes":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/configs/secondarystore/instances/listsOfAttributes","spacesConfigsSsiRules":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/configs/secondarystore/instances/rules","spacesConfigsUgc":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/configs/ugc","spacesEntities":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/entities","spacesItems":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/items","spacesLeaderboard":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/leaderboards","spacesNews":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/news","spacesOffers":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/offers","spacesParameters":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/parameters","spacesRewards":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/rewards","spacesSeasonChallenges":"https://msr-{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/club/seasonchallenges","spacesStats":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/communitystats","spacesStatsCard":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/communitystatscard","sessions":"https://{env}public-ubiservices.ubi.com/{version}/profiles/sessions","users":"https://{env}public-ubiservices.ubi.com/{version}/users","tLog":"https://tglog.datamore.qq.com/{appId}/report/","voicechatTokenVivox":"https://{env}public-ubiservices.ubi.com/{version}/profiles/{profileId}/voicechattoken/vivox","voicechatConfigVivox":"https://{env}public-ubiservices.ubi.com/{version}/spaces/{spaceId}/configs/voicechat/vivox","websocketNotifications":"wss://{env}public-ws-ubiservices.ubi.com/{version}/websocket","websocketServer":"wss://{env}public-ws-ubiservices.ubi.com"},"relatedPopulation":null},"us-sdkClientStorm":{"fields":{"detectConfig":"EnableDebug=false;ValidateDetect=true","detectProvisioningUrl":"https://ncsa-storm.ubi.com/v1/natdetect","traversalProvisioningUrl":"https://ncsa-storm.ubi.com/v1/nattraversal","routerProvisioningUrl":"https://apac-storm.ubi.com/v1/router;https://emea-storm.ubi.com/v1/router;https://ncsa-storm.ubi.com/v1/router;https://ap-southeast-2-storm.ubi.com/v1/router","matchmakingSandboxName":"SM_PC_LNCH_A","matchmakingSandboxSpaceId":"*matchmakingSandboxSpaceId*"},"relatedPopulation":null},"us-sdkClientSettingsWebSocketInternal":{"fields":{"maxCount":50,"connectionPingIntervalSec":30,"retryIncrementFactorMsec":5000,"retryRandomDelayMsec":5000,"retryInitialDelayMsec":5000,"timeoutInitialDelayMsec":30000,"timeoutIncrementFactorMsec":5000},"relatedPopulation":null},"us-sdkClientSettingsWebSocketGame":{"fields":{"connectionPingIntervalSec":30,"retryIncrementFactorMsec":5000,"retryRandomDelayMsec":5000,"retryInitialDelayMsec":5000,"timeoutInitialDelayMsec":30000,"timeoutIncrementFactorMsec":5000},"relatedPopulation":null},"us-sdkClientSettingsSecondaryStoreSync":{"fields":{"maxCount":10,"retryInitialDelayMsec":5000,"retryIncrementFactorMsec":5000,"retryRandomDelayMsec":5000},"relatedPopulation":null},"us-sdkClientSettingsHttpInternal":{"fields":{"maxCount":3,"retryInitialDelayMsec":5000,"retryIncrementFactorMsec":5000,"retryRandomDelayMsec":5000,"timeoutInitialDelayMsec":30000,"timeoutIncrementFactorMsec":5000},"relatedPopulation":null},"us-sdkClientSettingsHttpGame":{"fields":{"maxCount":3,"retryInitialDelayMsec":5000,"retryIncrementFactorMsec":5000,"retryRandomDelayMsec":5000,"timeoutInitialDelayMsec":30000,"timeoutIncrementFactorMsec":5000},"relatedPopulation":null},"us-sdkClientSettingsCacheTTL":{"fields":{"defaultSec":120,"profilesNewsSec":900,"spacesNewsSec":900,"profilesActionsSec":120,"profilesChallengesSec":120,"profilesRewardsSec":120,"friendsListSec":1800,"ssiAttributesAllSec":86400,"ssiListsOfAttributesAllSec":86400,"ssiRulesAllSec":86400,"profilesChallengesStatusSeasonSec":60,"challengesDefinitionSeasonSec":180,"battlepassSeasonProgressionSec":60},"relatedPopulation":null},"us-sdkClientSettings":{"fields":{"popEventsTimeoutMsec":5000,"primaryStoreSyncDelayMsec":250,"minBackgroundDurationForInventoryInvalidationMsec":5000,"notificationTypesUpdateRandomDelayMsec":3000,"xboxOneResumeFromSuspendedDelayMsec":5000,"createSessionRestPeriodMSec":3000,"createSessionRestRandomMSec":5000,"xboxOneCloseWebsocketOnSuspendingMode":"All","waitRemoteLogCompletionOnDeleteSession":false,"createSessionRestPeriodAfterConcurrentConnectDetectedMSec":60000},"relatedPopulation":null},"us-sdkClientRemoteLogsInternal":{"fields":{"maxTextLength":32768,"applicationUsed":"None","applicationInformation":"None","async":"None","authentication":"None","battlepass":"Warning","challenge":"None","club":"None","configuration":"None","connection":"None","core":"None","coreNotification":"None","entity":"None","event":"None","friend":"None","gamesPlayed":"None","http":"None","httpEngine":"None","job":"None","leaderboard":"None","localization":"None","matchmaking":"None","mobileExtension":"None","moderation":"Warning","news":"None","notification":"None","overlay":"Warning","parameters":"Warning","population":"None","primaryStore":"None","profile":"None","recommendations":"None","remoteLog":"None","scheduler":"None","secondaryStore":"None","stats":"None","task":"None","test":"None","tLog":"Warning","ugc":"Warning","user":"None","userContent":"None","voicechat":"None","websocket":"None"},"relatedPopulation":null},"us-sdkClientRemoteLogsGame":{"fields":{"url":"","maxTextLength":32768,"uncategorized":"None"},"relatedPopulation":null},"us-sdkClientNotificationsSpaceIds":{"fields":{"FriendsService":"*friendServiceId*"},"relatedPopulation":null},"us-sdkClientNotificationsInternal":{"fields":{"BATTLEPASS_TIERS_BANKED":true,"CHALLENGES_PROGRESSION_COMPLETED":true,"CHALLENGES_REWARDS_BANKED":true,"CLUB_REWARD_PURCHASED":true,"CLUB_ACTION_COMPLETED":true,"CLUB_CHALLENGE_THRESHOLD_REACHED":true,"CLUB_CHALLENGE_PARTICIPATION":true,"CLUB_CHALLENGE_BANKED":true,"CLUB_BADGE_ACQUIRED":true,"CLUB_CHALLENGE_COMPLETED":true,"FRIENDS_RELATIONSHIP_UPDATE":true,"SSI_INSTANCES_UPDATE":true,"US_CLIENT_SECONDARY_STORE_UPDATE":true,"US_APP_PARAMS_FULL_UPDATE":true,"US_APP_PARAMS_GROUP_UPDATE":true,"US_NOTIFICATION_MAINTENANCE":true,"US_SPACE_PARAMS_FULL_UPDATE":true,"US_SPACE_PARAMS_GROUP_UPDATE":true},"relatedPopulation":null},"us-sdkClientNotificationsGame":{"fields":{"additionalSpaces":[]},"relatedPopulation":null},"us-sdkClientFeaturesSwitches":{"fields":{"applicationUsed":true,"applicationInformation":true,"battlepass":true,"challenge":false,"clubApplication":true,"clubDynamicPanel":true,"clubService":true,"createSession":true,"entitiesProfile":true,"entitiesSpace":true,"event":true,"extendSession":true,"firstPartyAccessToMultiplayerInformation":true,"friendsLookup":true,"friendsRequest":true,"friendsUplayProfile":false,"gamesPlayed":true,"httpClient":true,"leaderboardMe":true,"leaderboardProfiles":true,"leaderboardSpaces":true,"matchmaking":true,"mobileExtensionProfilesExternal":true,"mobileExtensionUsersManagement":true,"moderation":true,"news":true,"notificationDynamicUpdate":true,"notificationRequestConnections":true,"notificationSend":true,"notificationSendBatch":true,"notificationSendNoBroker":true,"notificationWebsocket":true,"notificationRemoteLogReceivedData":false,"populations":true,"populationsAutomaticUpdate":true,"primaryStoreCatalogGetGameMediaType":false,"primarySecondaryStoreForceSyncAtLogin":true,"primaryStore":true,"primaryStoreAutomaticFetch":true,"primaryStoreSendEvent":true,"profiles":true,"recommendations":true,"secondaryStore":true,"secondaryStoreInstantiation":false,"secondaryStoreTransactions":true,"sessionTicket":true,"stats":true,"syncOnResumeToForegroundForNintendoSwitch":false,"tlog":true,"users":true,"ugc":false,"usersCreateAndLink":true,"usersLegalOptins":true,"voicechat":true,"webSocketClient":true},"relatedPopulation":null}}}
  ```

## GET /v1/spaces/*profileId*/configs/primarystore

### Use:

***Idk***

### Request:

#### Headers:

* User-Agent: UbiServices_SDK_2019.Release.13_PC64_ansi_static_cn
* Accept: \*/\*
* Authorization: Ubi_v1 t=*ticket value from POST /v3/profiles/session*
* Content-Type: application/json
* ubi-appbuildid: 202007232022
* Ubi-AppId: 86263886-327a-4328-ac69-527f0d20a237
* Ubi-localeCode: *localCode*
* Ubi-Populations: US_EMPTY_VALUE
* Ubi-SessionId: *sessionId*

### Response:

#### Headers:

* Ubi-Forwarded-By: ue1-p-us-public-nginx-0b4fb579f26ee4405 
* Ubi-TransactionId: 7f2c7738-1f1c-4bd6-aff8-c0611ea11c69
* Strict-Transport-Security: max-age=63072000
* X-Frame-Options: DENY
* X-Content-Type-Options: nosniff

#### Body:

* ```json
  {"mappings":[]}
  ```

## GET v3/profiles

### Use:

Get more info about the users

### Request:

#### Headers:

* User-Agent: UbiServices_SDK_2019.Release.13_PC64_ansi_static_cn
* Accept: \*/\*
* Authorization: Ubi_v1 t=*ticket value from POST /v3/profiles/session*
* Content-Type: application/json
* ubi-appbuildid: 202007232022
* Ubi-AppId: 86263886-327a-4328-ac69-527f0d20a237
* Ubi-localeCode: *localCode*
* Ubi-Populations: US_EMPTY_VALUE
* Ubi-SessionId: *sessionId*

#### Params:

* profileId=*profileIdsListSeparatedByComma*

### Response:

#### Headers:

* Content-Type: application/json; charset=utf-8
* Expires: -1
* Ubi-Forwarded-By: ue1-p-us-public-nginx-0b4fb579f26ee4405 
* Ubi-TransactionId: 21519912-1041-41c2-9532-1525e532dee6
* Strict-Transport-Security: max-age=63072000
* X-Frame-Options: DENY
* X-Content-Type-Options: nosniff

#### Body:

* ```json
  {"profiles":[{"profileId":"*profileId/userId/idOnPlataform*","userId":"*profileId/userId/idOnPlataform*","platformType":"uplay","idOnPlatform":"*profileId/userId/idOnPlataform*","nameOnPlatform":"*name*"}]}
  ```