# Some Relevant Use Cases

## Obtain an username from an AccountID/ProfileID

**Steps: (if you have the ProfileID skip to step 2)**

1. With the AccountID make a request to GET /webidentities/?accountIdList= from ProdTrackmania API and save the ProfileID
2. With the ProfileID make a request to GET v3/profiles?profileId= from the UbiServices API and save the username.

## Download a Record and Play It On Trackmania

*Thanks to [Breeku](https://github.com/breeku/) from showing me how I can play a ghost file on the Trackmania 2020. Check my question [here](https://www.reddit.com/r/TrackMania/comments/htz49s/convert_a_ghost_gbx_to_a_replay_gbx_to_be_able_to/) and his method [here](https://www.reddit.com/r/TrackMania/comments/i51q98/download_and_view_wr_ghosts_in_replay_editor/)*

1. Make a request to GET /mapRecords/?accountIdList= with the accountId, seasonId and mapIdList that you want to get.
2. Grab the URL Link and download the file
3. Change the extension to .gbx (the file will not have any extension when you download)
4. Put on the Replays folder of your Trackmania Folder (normally located on your Documents Folder)
5. Start the Trackmania 2020, go the Create Section -> Editor Replay -> **Select YOUR REPLAY ON THE SAME MAP** -> Edit
6. Bottom Part of the editor with a clock symbol, you can read "Import Ghost", select and open the file you download
7. Done!