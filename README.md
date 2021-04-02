## twitch-cp-wheel-of-fortune
Twitch channel points wheel of fortune and Song Request

## Description
Using the Winwheel.js and ComfyJS, the wheel is activated by certain channel point redemptions.

Added functionality for song request too.

Find information on how to configure the Winwheel.js settings found in config.js here: https://github.com/zarocknz/javascript-winwheel

# How to use

 - Clone the repo
 - Rename config.js.placeholder to config.js and edit accordingly.
 
 
## Twitch Config Example
```javascript
var twitchConfig = {
    TWITCHUSER: "Hoviis",
    OAUTH: "oauth:your-oauth-token-here"
}
```

You can get your oauth token here: https://twitchapps.com/tmi/ 
This oauth token can be your main account or more preferably a bot account e.g HoviisChannelPointsBot.
This is what will be announcing the result in the chat.

## Spin volume Example
```javascript
var audioVolume = 0.1;
```

This can vary from 0-1; configure to your liking.

## Channel Points IDs Example
```javascript
var channelPointsIDS = {
    'TF2' : '49429337-fd15-41ac-a2ae-5848690a13ae',
    'StreamWide': '3e1eabeb-24d6-4404-870d-0c14489c1156',
    'SongRequest': '3f50bc54-2f03-491d-a635-c5de58ad2731'
}
```

The Channel Points ID can be found with this url: https://www.instafluff.tv/TwitchCustomRewardID/?channel=YOUR-TWITCH-USERNAME-HERE 
- Replace `YOUR-TWITCH-USERNAME-HERE` with... you guessed it! Your twitch username.
- Go back to your channel and redeem a channel points reward, make sure you have `Require Viewer to Enter Text` enabled.
- That website will return the ID for that reward, paste that into one of the above keys, TF2, StreamWide or SongRequest.

Song request will just make your bot say !sr message-from-user-here. So make sure you have song request set to Moderators only and Mod your bot.

Finally the wheel settings, which can be found here: https://github.com/zarocknz/javascript-winwheel

If you want to disable any, just leave the key as '' or add the channel points id and control the enabling/disabling directly from twitch.

The text a user can enter in the channel points reward relates to the power of spin:
- Low
- Medium
- High
- Anything they want: This will pick randomly out of the 3 above.

## Example Channel Points description

```
Choose the spin power by typing in Low, Medium or High. If you type anything other than that it will randomly pick a power for you.
```

OBS Settings:
- Add a Browser source
- Tick local file and navigate to the index.html
- Change the width and height to your usual resolution. e.g 1920x1080
- Set the CSS to the below

```CSS
body { background: none; margin: 0px auto; overflow: hidden; }
```

- Tick both Shutdown source when not visible and Refresh browser when scene becomes active.


