# Forked from the awesome work of Steven Hickson
Forked from the awesome work of Steven Hickson on 4/15/19.  Updated it to work based on current bugs with TTS/missing libraries.
Fixes:
* fix missing LN for boost library
* remove sample rates from flac commands
* new TTS fix script for pico2wave replacement (from: https://github.com/StevenHickson/PiAUISuite/issues/56#issuecomment-205715002)




Includes voicecommand, download, playvideo, and textcommand scripts

This requires:

* boost
* curl
* xterm
* espeak
* some other things

To install the dependencies, run:
```bash
sudo apt-get install -y libboost-dev libboost-regex-dev youtube-dl axel curl xterm libcurl4-gnutls-dev mpg123 flac sox libttspico-utils
```

To install PiAUISuite (Silva Tech Forked Version):
```bash
git clone https://github.com/jtsSTECH/PiAUISuite.git
cd PiAUISuite/Install
./InstallAUISuite.sh
```

It will:
* ask if you want to install the dependencies
* to install each script

## Sample Config File:

This is the default config file that works well for us. Edit and paste this into your .commands.conf to get started.  
When voicecommand is running, you should be able to say: 
"computer"
** wait a second **
"check"

Its like using Alexa/Google assistant, and you should immediately see it trying to ping Google as a test.  The rest of the commands are from Steven Hickson's original file.

!response==Yes Sir?
check==ping google.com
show me==/home/pi/AUI/Imaging/test 2
track me==/home/pi/AUI/Imaging/test 1
download==download ...
play $1 season $2 episode $3==playvideo -s $2 -e $3 $1
download $1 season $2 episode $3==download $1 s$2e$3
play==playvideo -r -f ...
multiple==playvideo -r -m -c 5 ...
download==download ...
YouTube==youtube-search ...
Google==google ...
~music==xterm -e pianobar
~weather==/home/pi/AUI/Misc/sayweather.sh
~made you==tts "I was created by Steven Hickson" 2>/dev/null
~music==xterm -e control-pianobar.sh play
~terminal==xterm &
~Internet==midori &
!continuous==1
!verify==1
!ignore==1
!quiet==0
!filler==0
!thresh==0.7
!keyword==computer

# Testing TTS

1.) Test tts.  Type the following
tts "testing 123"
You should hear that phrase repeated back to you robotically via your sound interface if it is working correctly.


## Different Parts

Name | Purpose | Blogpost
-----|---------|---------
playvideo | finds and plays videos | [Here](http://stevenhickson.blogspot.com/2013/03/playing-videos-intelligently-with.html)
downloader | find and downloads the best torrent | [Here](http://stevenhickson.blogspot.com/2013/03/automatically-downloading-torrents-with.html)
gvapi | checks, sends, and deletes SMS messages | [Here](http://stevenhickson.blogspot.com/2013/05/using-google-voice-c-api.html)
gtextcommand | checks for sms messages every minute and runs commands from them | [Here](http://stevenhickson.blogspot.com/2013/03/controlling-raspberry-pi-via-text.html)
youtube | streams youtube | [In browser](http://stevenhickson.blogspot.com/2013/06/playing-youtube-videos-in-browser-on.html) and [on Pi](http://stevenhickson.blogspot.com/2013/04/using-youtube-on-raspberry-pi-without.html)
youtube-safe | streams other video files | [Hulu and Vimeo](http://stevenhickson.blogspot.com/2013/06/getting-huluvimeo-to-work-on-raspberry.html) and [others](http://stevenhickson.blogspot.com/2013/06/streaming-other-hd-video-sites-on.html)
voicecommand | run voice commands | [Here](http://stevenhickson.blogspot.com/2013/05/voice-command-v20-for-raspberry-pi.html) and [here](http://stevenhickson.blogspot.com/2013/04/voice-control-on-raspberry-pi.html)

Copyright

[GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-(gpl-3))

Jeremy Silva
