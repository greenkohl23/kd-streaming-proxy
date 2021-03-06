# KabelDeutschland simple streaming proxy

As all of you KabelDeutschland customers know, there is an existing iOS App that provides full TV-channel streaming if your are a paying customer of both cable internet and tv.
Unfortunatly there is no released Android nor Desktop version of this streaming possibility. KabelDeutschland kept us in the dark, if and when there will be such an option.

That's why i built this script to be able to watch all of the channels on my desktop and also with XBMC/KODI.

Beside this script, there is now an even simpler version. You can download the binary from my page [freshest.me/kd](http://freshest.me/simplified-kabeldeutschland-streaming-proxy/).
This version was build with golang and handles all functions in a simple executable. Mainly the new version was designed for every-day user who do not want to setup their own web-server but simply start the proxy.


## Requirements

### Contract

* KabelDeutschland Cable TV Package (the smallest one for 2,95€ is enough)
* KabelDeutschland Internet via cable

The first package is needed because the KD backend ensure with your credentials that you are a paying customer. The cable internet contract is needed cause the final stream link is available only in their network. So you can't connect and watch from any other ip-address outside of the KD network.

### Software

* webserver with php installed
	* php5_curl (`apt-get install php5-curl)
	
	
## Installation

Just copy the content of this repository to your webserver and configure it with your credentials.

## Configuration

* add your credentials instead of the placeholders. These credentials are the same you use to login into the kd customer-service-center.

## Run

Point your browser to your webserver for example http://localhost:8000/kd.php.
That call provides you with the download of a playlist file. This m3u-file can opened with vlc and contains the redirect links.

```
#EXTM3U
#EXTINF:-1,Das Erste
http://localhost:8000/kd.php?id=386601&link=http%3A%2F%2Fcdn1.iptv.kabel-deutschland.de%2Flive-spts%2Fmedia%2Fdaserste%2Ftransmux%2Fhls.m3u8
#EXTINF:-1,ZDF
http://localhost:8000/kd.php?id=386671&link=http%3A%2F%2Fcdn1.iptv.kabel-deutschland.de%2Flive-spts%2Fmedia%2Fzdf%2Ftransmux%2Fhls.m3u8
#EXTINF:-1,SAT.1
http://localhost:8000/kd.php?id=386646&link=http%3A%2F%2Fcdn1.iptv.kabel-deutschland.de%2Flive-spts%2Fmedia%2Fsat1%2Ftransmux%2Fhls.m3u8
```

You can also add the url http://localhost:8000/kd.php directly to VLC. This will resolve the playlist automatically.

Once imported into your VLC player, the scripts handle the generation of a licensed stream link and forwards the player automatically to this link.

## Debug

There are three steps of debugging included.
The simplest one is to call the script with format=txt to get a the textual output of the playlist.
http://localhost:8000/kd.php?format=txt

The more detailed version works with log_level=debug and writes al lot of data to logs/*.log.
http://localhost:8000/kd.php?format=txt&log_level=debug

# TODOs

 * UDID generation

# Explanation

To learn about how this script works, see [freshest.me](https://freshest.me).