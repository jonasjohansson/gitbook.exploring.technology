# Stream

Setting up a stream can be a daunting task if never done before.  Both [Zoom](https://zoom.us/) \([pricing](https://zoom.us/pricing)\) and [Meet](https://meet.google.com/?authuser=1) \([pricing](https://gsuite.google.com/pricing.html)\) are great for conference calls and online lectures, while [Twitch](https://www.twitch.tv/), [Facebook Live](https://www.facebook.com/facebookmedia/solutions/facebook-live), [Youtube Live](https://studio.youtube.com/) work better for streams that audience can drop in and out of.

### OBS Studio

If your choice is any of the latter, then [OBS Studio](https://obsproject.com/)  will elevate the experience for both host and audience. For a great default setup, do the following:

1. Select Scene under Scenes in the bottom left
2. Add a Video Capture Device under Sources, name it Webcam
3. Add a new scene under Scenes, name it "Screen"
4. Add a Display Capture under Sources
5. In **Settings &gt; Hotkeys** find Scene and Screen and add a hotkey for the "Switch to scene" input. 

Test switching between the two scenes using the hotkey. If this does not work, in **Settings &gt; Advanced**, make sure Hotkey Focus Behavior is set to "Never disable hotkeys".

{% hint style="info" %}
Pay attention to the amount if audio inputs, there should preferably be only 1.
{% endhint %}

![](../.gitbook/assets/obs-studio%20%281%29.png)

Before pressing Start Streaming and Start Recording, in **Settings &gt; Stream** set Service and fill out the Stream Key. If you are using Twitch, this can be found in the [Twitch user account](https://www.twitch.tv/settings/profile) under Channel and Videos.

{% hint style="warning" %}
Remember to test the stream having someone else visit and verify that sound and video behaves accordingly. It is possible to tweak video and audio output settings in OBS Studio.
{% endhint %}

