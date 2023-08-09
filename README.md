# okayu-api-wiki
## This is wiki of API api.okayu.pw

## All api urls
```
# GET /get_player_count: return total registered & online player counts.
# GET /get_player_info: return info or stats for a given player.
# GET /get_player_status: return a player's current status, if online.
# GET /get_player_scores: return a list of best or recent scores for a given player.
# GET /get_player_most_played: return a list of maps most played by a given player.
# GET /get_map_info: return information about a given beatmap.
# GET /get_map_scores: return the best scores for a given beatmap & mode.
# GET /get_score_info: return information about a given score.
# GET /get_replay: return the file for a given replay (with or without headers).
# (not work) GET /get_match: return information for a given multiplayer match.
# GET /get_leaderboard: return the top players for a given mode & sort condition
# GET /search: returns a list of matching users, based on a passed string, sorted by ascending ID.
```

## Users

### User count

#### Description:<br>
Get total registered users and online user count.<br>
Returns total registered & online player counts.

#### URL
```
/get_player_count
```

#### Parameters
`None` - This endpoint does not require parameters.

#### Response
```json
{
  "status": "success",
  "counts": {
    "online": 1,
    "total": 12
  }
}
```
#### Notes
It does not count the bot as a user.

-----------------------------------------

### User information and stats

#### Description:<br>
Get player account information<br>
Returns info or stats for a given player.

#### URL
```
/get_player_info
```

#### Parameters
* Required id or name<br>
`id` = The users id<br>
`name` = The user's name

* Required scope<br>
`scope` = <all/stats/info>
  * `info` - Returns user info
  * `stats` - Returns user stats
  * `all` - Returns everything

#### Examples:
```md
https://api.../get_player_info?id=3&scope=info
https://api.../get_player_info?name=User&scope=all
```

#### Response (scope: `info`)
```json
{
    "status": "success",
    "player": {
        "info": {
            "id": 3,
            "name": "User",
            "safe_name": "User",
            "priv": 3,
            "clan_id": 1,
            "country": "nl",
            "silence_end": 0,
            "donor_end": 0,
            "preferred_mode": 0
        }
    }
}
```


#### Response (scope: `all`)
```json
{
    "status": "success",
    "player": {
        "info": {
            "id": 3,
            "name": "User",
            "safe_name": "User",
            "priv": 3,
            "clan_id": 1,
            "country": "nl",
            "silence_end": 0,
            "donor_end": 0,
            "preferred_mode": 0
        },
        "stats": {
            "0": {
                "tscore": 697767499,
                "rscore": 129855080,
                "pp": 832,
                "plays": 2111,
                "playtime": 104936,
                "acc": 88.099,
                "max_combo": 972,
                "xh_count": 0,
                "x_count": 1,
                "sh_count": 3,
                "s_count": 1,
                "a_count": 10,
                "rank": 47,
                "country_rank": 4
            },
            "1": {
                "tscore": 912918,
                "rscore": 0,
                "pp": 0,
                "plays": 3,
                "playtime": 332,
                "acc": 0.0,
                "max_combo": 325,
                "xh_count": 0,
                "x_count": 0,
                "sh_count": 0,
                "s_count": 0,
                "a_count": 0,
                "rank": 0,
                "country_rank": 0
            },
            "2": {
                "tscore": 0,
                "rscore": 0,
                "pp": 0,
                "plays": 0,
                "playtime": 0,
                "acc": 0.0,
                "max_combo": 0,
                "xh_count": 0,
                "x_count": 0,
                "sh_count": 0,
                "s_count": 0,
                "a_count": 0,
                "rank": 0,
                "country_rank": 0
            },
            "3": {
                "tscore": 0,
                "rscore": 0,
                "pp": 0,
                "plays": 0,
                "playtime": 0,
                "acc": 0.0,
                "max_combo": 0,
                "xh_count": 0,
                "x_count": 0,
                "sh_count": 0,
                "s_count": 0,
                "a_count": 0,
                "rank": 0,
                "country_rank": 0
            },
            "4": {
                "tscore": 223942543,
                "rscore": 31385852,
                "pp": 6176,
                "plays": 1101,
                "playtime": 54528,
                "acc": 95.199,
                "max_combo": 1883,
                "xh_count": 1,
                "x_count": 1,
                "sh_count": 14,
                "s_count": 2,
                "a_count": 56,
                "rank": 16,
                "country_rank": 3
            },
            "5": {
                "tscore": 793560,
                "rscore": 236250,
                "pp": 97,
                "plays": 15,
                "playtime": 746,
                "acc": 60.465,
                "max_combo": 138,
                "xh_count": 0,
                "x_count": 0,
                "sh_count": 0,
                "s_count": 0,
                "a_count": 0,
                "rank": 5,
                "country_rank": 1
            },
            "6": {
                "tscore": 109640,
                "rscore": 0,
                "pp": 0,
                "plays": 3,
                "playtime": 51,
                "acc": 0.0,
                "max_combo": 0,
                "xh_count": 0,
                "x_count": 0,
                "sh_count": 0,
                "s_count": 0,
                "a_count": 0,
                "rank": 0,
                "country_rank": 0
            },
            "8": {
                "tscore": 18915479,
                "rscore": 10722031,
                "pp": 823,
                "plays": 168,
                "playtime": 9851,
                "acc": 80.184,
                "max_combo": 720,
                "xh_count": 0,
                "x_count": 0,
                "sh_count": 0,
                "s_count": 0,
                "a_count": 3,
                "rank": 0,
                "country_rank": 0
            }
        }
    }
}
```

-----------------------------------------
  
### User status

#### Description:<br>
Get a player's current status.<br>
Returns a player's current status, if online.

#### URL
```
/get_player_status
```

#### Parameters
* Required id or name<br>
`id` = The users id<br>
`name` = The user's name

#### Examples:
```md
https://api.../get_player_status?id=3
https://api.../get_player_status?name=User
```

#### Response (offline example)
```json
{
    "status": "success",
    "player_status": {
        "online": false,
        "last_seen": 1653680340
    }
}
```

#### Response (online idle example)
```json
{
    "status": "success",
    "player_status": {
        "online": true,
        "login_time": 1619577679.8482022,
        "status": {
            "action": 0,
            "info_text": "",
            "mode": 0,
            "mods": 0,
            "beatmap": null
        }
    }
}
```

#### Response (online example spectating/watching)
```json
{
    "status": "success",
    "player_status": {
        "online": true,
        "login_time": 1619577679.8482022,
        "status": {
            "action": 6,
            "info_text": "User 2 play BLANKFIELD - Goodbye [Intense]",
            "mode": 0,
            "mods": 0,
            "beatmap": {
                "md5": "4a4bc3bdb6d951512db592994b08cfc7",
                "id": 1172819,
                "set_id": 553906,
                "artist": "BLANKFIELD",
                "title": "Goodbye",
                "version": "Intense",
                "creator": "Kyubey",
                "last_update": "2017-02-25T12:56:50",
                "total_length": 289,
                "max_combo": 2516,
                "status": 2,
                "plays": 9,
                "passes": 3,
                "mode": 0,
                "bpm": 104.5,
                "cs": 4,
                "od": 10,
                "ar": 10,
                "hp": 4.7,
                "diff": 8.356
            }
        }
    }
}
```
#### Notes
`mods` - Will return only client mods! If status is watching it will not return the spectated user's mods.<br>
`mode` - Will return `4` if `mode` is unknown.<br>
`status` - Will be set only when a user is online.

-----------------------------------------
  
### User scores

#### Description:<br>
Get a list of scores for a given user.<br>
Returns a list of best or recent scores for a given player.

#### URL
```
/get_player_scores
```

#### Parameters
* Required id or name<br>
`id` = The users id<br>
`name` = The user's name

* Required scope<br>
`scope` = <best/recent>
  * `best` - Returns user's best scores
  * `recent` - Returns user's recent scores
* Optional mode<br>
`mode` = <0-8>, default `0`
* Optional limit<br>
`limit` = <1-100>, default: 25

#### Example
```md
https://api.../get_player_scores?id=3&scope=recent&mods=vn&mode=3
```

#### Response
```json
{
    "status": "success",
    "scores": [{
        "id": 47,
        "score": 6803159,
        "pp": 563.218,
        "acc": 96.413,
        "max_combo": 498,
        "mods": 16,
        "n300": 1004,
        "n100": 23,
        "n50": 4,
        "nmiss": 19,
        "ngeki": 211,
        "nkatu": 18,
        "grade": "F",
        "status": 0,
        "mode": 0,
        "play_time": "2020-09-25T00:03:43",
        "time_elapsed": 183642,
        "perfect": 0,
        "beatmap": {
            "md5": "90d717f5aa233d85abdf02acac3f975e",
            "id": 915210,
            "set_id": 423527,
            "artist": "dj TAKA",
            "title": "quaver",
            "version": "Crescendo",
            "creator": "Monstrata",
            "last_update": "2016-09-04T04:18:11",
            "total_length": 0,
            "max_combo": 0,
            "status": 2,
            "plays": 8,
            "passes": 3,
            "mode": 0,
            "bpm": 182,
            "cs": 4,
            "od": 9,
            "ar": 9.6,
            "hp": 5,
            "diff": 7.561
        }
    }, {
        ...
    }],
    "player": {
        "id": 3,
        "name": "User 1",
        "clan": {
            "id": 1,
            "name": "Clan Name",
            "tag": "ClanTag"
        }
    }
}
```
  
-----------------------------------------
  
### User most played maps

#### Description:<br>
Get a list of the most played maps by a user.<br>
Returns a list of maps most played by a given player.

#### URL
```
/get_player_most_played
```

#### Parameters
* Required id or name<br>
`id` = The users id<br>
`name` = The user's name

* Required mode<br>
`mode` = <0-8>
* Optional limit<br>
`limit` = <1-100>, default: 25

#### Example
```md
https://api.../get_player_most_played?id=3&mods=vn&mode=3&limit=6
```

#### Response
```json
{
    "status": "success",
    "maps": [{
        "md5": "51df3da24abe038386e2ebaf14551d14",
        "id": 2679663,
        "set_id": 1290926,
        "status": 2,
        "artist": "Five Hammer",
        "title": "fffff",
        "version": "Forte fortissississimo",
        "creator": "Luscent",
        "plays": 28
    }, {
        ...
    }]
}
```

## Beatmaps

### Beatmap information

#### Description:<br>
Get information about a given beatmap by it's id or md5 hash.<br>
Returns information about a given beatmap.

#### URL
```
/get_map_info
```

#### Parameters
* Required beatmap id or beatmap md5<br>
`id` = The beatmap's id<br>
`md5` = The beatmap's md5 hash

#### Examples:
```md
https://api.../get_map_info?id=1172819
https://api.../get_map_info?md5=4a4bc3bdb6d951512db592994b08cfc7
```

#### Response
```json
{
    "status": "success",
    "map": {
        "md5": "4a4bc3bdb6d951512db592994b08cfc7",
        "id": 1172819,
        "set_id": 553906,
        "artist": "BLANKFIELD",
        "title": "Goodbye",
        "version": "Intense",
        "creator": "Kyubey",
        "last_update": "2017-02-25T12:56:50",
        "total_length": 289,
        "max_combo": 2516,
        "status": 2,
        "plays": 18,
        "passes": 1,
        "mode": 0,
        "bpm": 258,
        "cs": 4,
        "od": 10,
        "ar": 10,
        "hp": 4.7,
        "diff": 8.538
    }
}
```

#### Statuses
```
-1 = NotSubmitted
 0 = Pending
 1 = UpdateAvailable
 2 = Ranked
 3 = Approved
 4 = Qualified
 5 = Loved
```

-----------------------------------------

### Beatmap scores

#### Description:<br>
Get scores for a given beatmap, mode and mods<br>
Returns the best scores for a given beatmap & mode.

#### URL
```
/get_map_scores
```

#### Parameters
* Required beatmap id or beatmap md5<br>
`id` = The beatmap's id<br>
`md5` = The beatmap's md5 hash

* Required scope<br>
`scope` = <best/recent>
  * `best` - Returns beatmap's best scores
  * `recent` - Returns beatmap's recent scores

* Optional mode<br>
`mode` = `(0-8), explained below`

* Optional limit<br>
`limit` = <1-100>, default: 50

#### Modes
```md
0 - Standard
1 - Taiko
2 - Catch
3 - Mania

4 - Relax Standard
5 - Relax Taiko
6 - Relax Catch

7 - Autopilot Standard
```

#### Examples:
```md
https://api.../get_map_scores?id=1172819&scope=recent
https://api.../get_map_scores?id=1172819&scope=best&mode=4
```

#### Response
```json
{
    "status": "success",
    "scores": [{
        "map_md5": "8d9756be1d932eb2f4760664a1497e48",
        "score": 517771,
        "pp": 336.419,
        "acc": 95.115,
        "max_combo": 144,
        "mods": 72,
        "n300": 108,
        "n100": 7,
        "n50": 0,
        "nmiss": 1,
        "ngeki": 41,
        "nkatu": 5,
        "grade": "A",
        "status": 2,
        "mode": 0,
        "play_time": "2021-12-31T05:29:13",
        "time_elapsed": 0,
        "userid": 165,
        "perfect": 0,
        "player_name": "OSU",
        "clan_id": null,
        "clan_name": null,
        "clan_tag": null
    }, {
        ...
    }]
}
```

-----------------------------------------

### Beatmap score info

#### Description:<br>
Get beatmap score information by score id.<br>
Returns information about a given score.

#### URL
```
/get_score_info
```

#### Parameters
* Required score id<br>
`id` = The score's id

#### Example
```md
https://api.../get_score_info?id=1731
```

#### Response
```json
{
    "status": "success",
    "score": {
        "map_md5": "75dabfe11d5f4b3b776d5736fc1dfb70",
        "score": 29168,
        "pp": 10.463,
        "acc": 95.556,
        "max_combo": 48,
        "mods": 0,
        "n300": 14,
        "n100": 1,
        "n50": 0,
        "nmiss": 0,
        "ngeki": 6,
        "nkatu": 1,
        "grade": "F",
        "status": 0,
        "mode": 0,
        "play_time": "2022-03-24T03:33:14",
        "time_elapsed": 13500,
        "perfect": 0
    }
}
```

-----------------------------------------

### Beatmap replay

#### Description:<br>
Get beatmap replay by id.<br>
Returns the file for a given replay (with or without headers).

#### URL
```
/get_replay
```

#### Parameters
* Required score/replay id<br>
`id` = The score/replay's id
* Optionally disable headers
`include_headers` = `true/false, default: true` - Include hits and score headers, dev option.

#### Examples:
```md
https://api.../get_replay?id=1731
https://api.../get_replay?id=1731&include_headers=false
```

#### Response
```brainfuck
Returns the replay file.
Returns the replay file without headers for the hits and score.
```

-----------------------------------------

## Other

### Leaderboard

#### Description:<br>
Return the top players for a given mode & sort condition

#### URL
```
/get_leaderboard
```

#### Parameters
`sort` = tscore, rscore, pp, acc, plays, playtime (default pp)
`mode` = min 0 max 11 (default 0)
`limit` = min 1 max 100 (default 25)
`offset` = min 0 max 2147483647 (default 0)

#### Examples:
```md
https://api.../get_leaderboard?sort=pp&mode=4&limit=3&offset=2
```

#### Response (scope: `info`)
```json
{
  "status": "success",
  "leaderboard": [
    {
      "player_id": 1156,
      "name": "ZuNoRuS",
      "country": "ru",
      "tscore": 70372770,
      "rscore": 14831000,
      "pp": 24706,
      "plays": 1335,
      "playtime": 45179,
      "acc": 94.566,
      "max_combo": 3496,
      "latest_activity": 1674423864,
      "xh_count": 0,
      "x_count": 0,
      "sh_count": 23,
      "s_count": 0,
      "a_count": 48,
      "clan_id": null,
      "clan_name": null,
      "clan_tag": null
    },
    {
      "player_id": 1153,
      "name": "MinerZeta",
      "country": "fr",
      "tscore": 43435830,
      "rscore": 14657340,
      "pp": 24549,
      "plays": 427,
      "playtime": 23031,
      "acc": 96.869,
      "max_combo": 2600,
      "latest_activity": 1673988249,
      "xh_count": 0,
      "x_count": 0,
      "sh_count": 11,
      "s_count": 0,
      "a_count": 56,
      "clan_id": null,
      "clan_name": null,
      "clan_tag": null
    },
    {
      "player_id": 3,
      "name": "OwOuser",
      "country": "af",
      "tscore": 176124560,
      "rscore": 52921270,
      "pp": 24528,
      "plays": 1622,
      "playtime": 103065,
      "acc": 98.576,
      "max_combo": 3688,
      "latest_activity": 1691442832,
      "xh_count": 10,
      "x_count": 14,
      "sh_count": 62,
      "s_count": 70,
      "a_count": 123,
      "clan_id": 3,
      "clan_name": "OwO",
      "clan_tag": "OWO"
    }
  ]
}
```

### Clan

#### Description:<br>
Returns a clan info

#### URL
```
/get_clan
```

#### Parameters
`id` = min=1, max=2_147_483_647

#### Examples:
```md
https://api.../get_clan?id=3
```

#### Response (scope: `info`)
```json
{
  "id": 3,
  "name": "OwO",
  "tag": "OWO",
  "country": "af",
  "members": [
    {
      "id": 3,
      "name": "OwOuser",
      "pp": [
        {
          "pp": 194
        }
      ],
      "country": "af",
      "rank": "Owner"
    },
    {
      "id": 36,
      "name": "hatsune enjoyer",
      "pp": [
        {
          "pp": 194
        }
      ],
      "country": "cc",
      "rank": "Member"
    }
  ],
  "owner": {
    "id": 3,
    "name": "OwOuser",
    "country": "af",
    "rank": "Owner"
  }
}
```

### Mappool

#### Description:<br>
Returns a mappool info

#### URL
```
/get_mappool
```

#### Parameters
`id` = min=1, max=2_147_483_647

#### Examples:
```md
https://api.../get_mappool?id=1
```

#### Response (scope: `info`)
```json
# idk for correct, no mappools created
{
  "id": 1,
  "name": "name",
  "created_at": 6666666,
  "created_by": "OwOuser",
  "maps": {
    "NM1": Map info
    "NM2": Map info
    "DT3": Map info
  },
}
```

### Search

#### Description:<br>
Returns a list of matching users, based on a passed string, sorted by ascending ID.

#### URL
```
/search
```

#### Parameters
`src` = your text

#### Examples:
```md
https://api.../search?src=OwO
```

#### Response (scope: `info`)
```json
{
  "status": "success",
  "results": 6,
  "result": [
    {
      "id": 3,
      "name": "OwOuser"
    },
    {
      "id": 82,
      "name": "OwOuser2"
    },
    {
      "id": 247,
      "name": "OwOuser99"
    },
    {
      "id": 714,
      "name": "Mowosi"
    },
    {
      "id": 1757,
      "name": "jazentowo"
    },
    {
      "id": 2079,
      "name": "Yikowo"
    }
  ]
}
```
