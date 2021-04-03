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

## Song Request Channel Points ID
```javascript
var channelPointsIDS = {
    'SongRequest': '3f50bc54-2f03-491d-a635-c5de58ad2731'
}
```

Follow below on how to get your Channel Points ID.
Song request will just make your bot say !sr message-from-user-here. So make sure you have song request set to Moderators only and Mod your bot.

## Bind the wheel to a Channel Points Reward
```javascript
// Modular Wheel config.
var wheelConfig = {
// Start of wheel config
    '49429337-fd15-41ac-a2ae-5848690a13ae': {    // Change this to your Channel Points ID
        'outerRadius'     : 212,        // Set outer radius so wheel fits inside the background.
        'innerRadius'     : 75,         // Make wheel hollow so segments don't go all way to center.
        'textFontSize'    : 24,         // Set default font size for the segments.
        'textOrientation' : 'vertical', // Make text vertial so goes down from the outside of wheel.
        'textAlignment'   : 'outer',    // Align text to outside of wheel.
        'numSegments'     : 24,         // Specify number of segments.
        'segments'        :             // Define segments including colour and text.
        [                               // font size and test colour overridden on backrupt segments.
            {'fillStyle' : '#ee1c24', 'text' : '300'},
            {'fillStyle' : '#3cb878', 'text' : '450'},
            {'fillStyle' : '#f6989d', 'text' : '600'},
            {'fillStyle' : '#00aef0', 'text' : '750'},
            {'fillStyle' : '#f26522', 'text' : '500'},
            {'fillStyle' : '#000000', 'text' : 'BANKRUPT', 'textFontSize' : 16, 'textFillStyle' : '#ffffff'},
            {'fillStyle' : '#e70697', 'text' : '3000'},
            {'fillStyle' : '#fff200', 'text' : '600'},
            {'fillStyle' : '#f6989d', 'text' : '700'},
            {'fillStyle' : '#ee1c24', 'text' : '350'},
            {'fillStyle' : '#3cb878', 'text' : '500'},
            {'fillStyle' : '#f26522', 'text' : '800'},
            {'fillStyle' : '#a186be', 'text' : '300'},
            {'fillStyle' : '#fff200', 'text' : '400'},
            {'fillStyle' : '#00aef0', 'text' : '650'},
            {'fillStyle' : '#ee1c24', 'text' : '1000'},
            {'fillStyle' : '#f6989d', 'text' : '500'},
            {'fillStyle' : '#f26522', 'text' : '400'},
            {'fillStyle' : '#3cb878', 'text' : '900'},
            {'fillStyle' : '#000000', 'text' : 'BANKRUPT', 'textFontSize' : 16, 'textFillStyle' : '#ffffff'},
            {'fillStyle' : '#a186be', 'text' : '600'},
            {'fillStyle' : '#fff200', 'text' : '700'},
            {'fillStyle' : '#00aef0', 'text' : '800'},
            {'fillStyle' : '#ffffff', 'text' : 'LOOSE TURN', 'textFontSize' : 12}
        ],
        'animation' :           // Specify the animation to use.
        {
            'type'     : 'spinToStop',
            'duration' : 10,    // Duration in seconds.
            'spins'    : 3     // Default number of complete spins.
        },
        'pins' :
        {
            'number'     : 24,
            'fillStyle'  : 'silver',
            'outerRadius': 4
        }
    
    }

    ,'3e1eabeb-24d6-4404-870d-0c14489c1156': {    // Change this to your Channel Points ID
            //Wheel Config here. Like above
    }

    ,'Place-Holder-For-Another-Wheel': {    // Change this to your Channel Points ID
            //Wheel Config here. Like above
    }

// End of wheel config
}
```

The Channel Points ID can be found with this url: https://www.instafluff.tv/TwitchCustomRewardID/?channel=YOUR-TWITCH-USERNAME-HERE 
- Replace `YOUR-TWITCH-USERNAME-HERE` with... you guessed it! Your twitch username.
- Go back to your channel and redeem a channel points reward, make sure you have `Require Viewer to Enter Text` enabled.
- That website will return the ID for that reward, use that as the key for a wheel config like in the example above.

Where you see the Channel Points ID above in wheelConfig is where you will need to paste the ID for the wheel to be activated for that certain CP reward.

I've made it so you can create as many different wheel configurations as you want. You simple copy a completed wheel configuration above and alter the Channel Points ID.

Finally the actual wheel settings, which can be found here: https://github.com/zarocknz/javascript-winwheel or just work it out from the example.

If you want to disable any, just leave the key as 'disabled' or add the Channel Points ID and control the enabling/disabling directly from Twitch.

The text a user can enter in the Channel Points reward relates to the power of spin:
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


