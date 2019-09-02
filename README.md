
## Description: 
Companion script for Tautulli to automatically scrobble media to Trakt.tv.

## Dependencies
\- **tautulli**
\- **jq**

## Install 
    wget -O tautulli2trakt.sh https://raw.githubusercontent.com/Generator/tautulli2trakt/master/tautulli2trakt.sh
    chmod +x tautulli2trakt.sh

## Script Setup
Create a new application https://trakt.tv/oauth/applications  
Add the follow settings:

**Name:** `tautulli2trakt`
**Redirect uri:** `urn:ietf:wg:oauth:2.0:oob`
**Permissions:** `/scrobble`


**DO NOT AUTHORIZE YET**

Run script for initial setup and follow instructions  
`tautulli2trakt.sh --setup`


## Tautulli

### Add Script
- Settings > Notification Agents > Add a Notification Agent > Script

## Script Settings

### Configuration
- **Script Folder**
  - \<script path location\>
- **Script File**
  - tautulli2trakt.sh

### Triggers
- Playback Start 
- Playback Stop
- Playback Pause
- Playback Resume
- Watched 

### Arguments
- Playback Start / Playback Resume :  
`-m {media_type} -s "{show_name}" -M "{title}" -y "{year}" -t "{thetvdb_id}" -i "{imdb_id}" -S {season_num} -E {episode_num} -P {progress_percent} -a start`  

- Playback Stop / Watched :  
`-m {media_type} -s "{show_name}" -M "{title}" -y "{year}" -t "{thetvdb_id}" -i "{imdb_id}" -S {season_num} -E {episode_num} -P {progress_percent} -a stop` 

- Playback Pause :   
`-m {media_type} -s "{show_name}" -M "{title}" -y "{year}" -t "{thetvdb_id}" -i "{imdb_id}" -S {season_num} -E {episode_num} -P {progress_percent} -a pause`


## Usage
```
--setup             Setup aplication
--reset             Reset settings and revoke token

-m | --media        Media type (movie, show, episode)
-a | --action       Action (start, pause, stop)
-s | --showname     Name of the TV Series
-M | --Moviename    Name of the Moviename
-y | --year         Year of the movie/TV Show
-S | --season       Season number
-E | --Episode      Episode number
-t | --TVDB         TVDB ID
-i | --IMDB         IMDB ID
-P | --progress     Percentage progress (Ex: 10.0)
-h | --help         This help
```

## FAQ
**Q:** Can i use this script on Docker?
**A:** For now no, it depends on `jq` not available on Docker container, maybe in a future release.

**Q:** What's the difference of this script and the plugin or other Trakt.tv scrobbler?
**A:** The plugin **[Plex-Trakt-Scrobbler](https://github.com/trakt/Plex-Trakt-Scrobbler)** is unmaintained and no longer works on ARM, and soon can stop working on all systems.  
[**Plaxt**](https://plaxt.astandke.com/) (and similar) requires webhooks, only available to Plex Pass users.

**Q:** **tautulli2trakt** is no longer scrobbling/updating my media, how can i check if it's working?
**A:** Make sure `tautulli2trakt.data` (located on script path) is writable by Tautulli. If Tautulli is running with it's own user change the file owner `chmod <tautulli username> tautulli2trakt.data`.

**Q:** How can i check any log messages?
**A:** On Tautulli: View Logs > Notification Logs

### Similar Projects 

\- https://github.com/JvSomeren/tautulli-watched-sync   
\- https://github.com/xanderstrike/goplaxt
