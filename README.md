## twitch-cp-bot
Twitch channel points wheel of fortune and Song Request

## Description
Using the Winwheel.js and ComfyJS, the wheel is activated by certain channel point redemptions.

Added functionality for song request too.

Find information on how to configure the Winwheel.js settings found in config.js here: https://github.com/zarocknz/javascript-winwheel

# How to use

 - Clone the repo
 - Rename config.js.placeholder to config.js and edit accordingly.

 ## Get Channel Points Reward ID
 The Channel Points ID can be found with this url: https://www.instafluff.tv/TwitchCustomRewardID/?channel=YOUR-TWITCH-USERNAME-HERE 
- Replace `YOUR-TWITCH-USERNAME-HERE` with... you guessed it! Your twitch username.
- Go back to your channel and redeem a channel points reward, make sure you have `Require Viewer to Enter Text` enabled.
- That website will return the ID for that reward, use that as the key for a config like in the examples below.
 
 
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
// Song Request Channel Points ID
var srConfig = {
    '6b5bc459-5668-4395-a79a-4c9416dfd072' : {
        'enabled' : true // This doesn't actually do anything, just something to fill the object.
    }
    ,'PLACE-HOLDER-FOR-ANOTHER-REWARD' : {
        'enabled' : true // This doesn't actually do anything, just something to fill the object.
    }
}
```

Follow below on how to get your Channel Points ID.
Song request will just make your bot say !sr message-from-user-here. So make sure you have song request set to Moderators only and Mod your bot.
I've made it so you can make as many as you want, follow the template above or/and in the config.js.placeholder

## Random Sound Config

```javascript
var randomSoundConfig = {
    'b231f2cd-fa22-42f6-8aa2-c852728b51aa' : {
        'soundsLocation': 'H:/location-to/twitch-bot-wheeloffortune/sounds/coolsounds/', //Location to the sounds, make sure you have the last /
        'maxAmount': 3, // This is the max amount of sounds in that directory. The sounds need to be named from 1-You max amount.
        'audioVolume': 0.1 // Volume for the sounds to be played at.
    }
    ,'PLACE-HOLDER-FOR-ANOTHER-REWARD' : {
        'soundsLocation': 'H:/location-to/twitch-bot-wheeloffortune/sounds/morecoolsounds/',
        'maxAmount': 3,
        'audioVolume': 0.1
    }
}
```
The random sound player will randomly pick a number from 1 to your set maxAmount, e.g 1-100. 

Keys:
- Main object key is your Channel Points Reward ID.
- soundsLocation: This is where all your mp3s will be found.
- maxAmount: The max amount of sounds in the directory you've stated. They are also all named from 1-maxAmount + .mp3
- audioVolume: The volume you want the sounds to play at.

Rules:
- All files must be named from 1 - Your maxAmount.
- They NEED to be mp3, the bot only reads .mp3 file extensions.
- I've made it so you can make as many as you want, follow the template above or/and in the config.js.placeholder

## Bind the wheel to a Channel Points Reward
```javascript
// Modular Wheel config.
var wheelConfig = {
// Start of wheel config
    '49429337-fd15-41ac-a2ae-5848690a13ae': {    // Change this to your Channel Points ID
        'audioVolume'     : 0.1,        // Volume
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

Where you see the Channel Points ID above in wheelConfig is where you will need to paste the ID for the wheel to be activated for that certain CP reward.

I've made it so you can create as many different wheel configurations as you want. You simple copy a completed wheel configuration above and alter the Channel Points ID.

Finally the actual wheel settings, which can be found here: https://github.com/zarocknz/javascript-winwheel or just work it out from the example.

If you want to disable any, just leave the key as 'disabled' or add the Channel Points ID and control the enabling/disabling directly from Twitch.

The text a user can enter in the Channel Points reward relates to the power of spin:
- Low
- Medium
- High
- Anything they want: This will pick randomly out of the 3 above.

## OBS Setup

- Add a Browser source
- Tick local file and navigate to the index.html
- Change the width and height to a resolution of your liking. I use this; width: 650, height: 1080.
- Set the CSS to the below

```CSS
body { background: none; margin: 0px auto; overflow: hidden; }
```

- Tick both Shutdown source when not visible and Refresh browser when scene becomes active.


