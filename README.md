<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/Generator/tautulli2trakt">
    <img src="logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Tautulli 2 Trakt</h3>

</p>

<!-- TABLE OF CONTENTS -->
## Table of Contents

* [Description](#description)
* [Installation](#installation)
   * [Script Setup](#script-setup)
   * [Tautulli](#tautulli)
   * [Script Settings](#script-settings)
* [Usage](#usage)
* [License](#license)
* [Similar Projects](#similar-projects)

## Description: 
Companion script for Tautulli to automatically scrobble media to Trakt.tv.

# Getting Started

## Installation 
    wget -O tautulli2trakt.sh https://raw.githubusercontent.com/Generator/tautulli2trakt/master/tautulli2trakt.sh
    chmod +x tautulli2trakt.sh

### Script Setup
Create a new application https://trakt.tv/oauth/applications  
Add the follow settings:

**Name:** `tautulli2trakt`  
**Redirect uri:** `urn:ietf:wg:oauth:2.0:oob`  
**Permissions:** `/scrobble`


**DO NOT AUTHORIZE YET**

Run script for initial setup and follow instructions  
`tautulli2trakt.sh --setup`


### Tautulli

#### Add Script
- `Settings` > `Notification Agents` > `Add a Notification Agent` > `Script`

### Script Settings

#### Configuration
- **Script Folder**
  - `<script path location>`
- **Script File**
  - `tautulli2trakt.sh`

#### Triggers
- Playback Start 
- Playback Stop
- Playback Pause
- Playback Resume
- Watched 

#### Arguments
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

## FAQ & Troubleshooting
* [Frequently Asked Questions](https://github.com/Generator/tautulli2trakt/wiki/Frequently-Asked-Questions)  
* [Troubleshooting](https://github.com/Generator/tautulli2trakt/wiki/Troubleshooting)

## License
Distributed under the GPL License.

## Similar Projects 

- https://github.com/JvSomeren/tautulli-watched-sync   
- https://github.com/xanderstrike/goplaxt  
- https://github.com/gazpachoking/trex  
- https://github.com/dabiggm0e/plextrakt  
- https://github.com/trakt/Plex-Trakt-Scrobbler
