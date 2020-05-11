# Tips & Trix

## Streaming

Setting up a stream can be a daunting task if never done before, both on the software and hardware side. Let's look at the services available, and some hardware and software!

### Services

| Name | Video conference | Live stream |
| :--- | :--- | :--- |
| [Zoom](https://zoom.us/) \([pricing](https://zoom.us/pricing)\) | Yes | No |
| [Meet](https://meet.google.com/?authuser=1) \([pricing](https://gsuite.google.com/pricing.html)\) | Yes | No |
| [Jitsi](https://jitsi.org/) | Yes | No |
| [Twitch](https://www.twitch.tv/) | No | Yes |
| Instagram Live | No  | Yes |
| [Facebook Live](https://www.facebook.com/facebookmedia/solutions/facebook-live) | No | Yes |
| [Youtube Live](https://studio.youtube.com/) | No | Yes |

Zoom/Meet/Jitsi work well for conference calls and online lectures where video quality and frame rate is not focus, while the rest are better for streams where audience can drop in and out of. Zoom can absolutely be used for live streams \(read [21 things we learned from hosting our first online party](https://tedcooke.blog/2020/04/13/21-things-we-learned-from-hosting-our-first-online-party/)\) but it it is obvious that it is made for co-creation rather than a traditional stream of content.

### Hardware

| Name | Category |
| :--- | :--- |
| [Blue Yeti-X](https://www.bluedesigns.com/products/yeti-x) | Microphone |
| [Razer Seiren X](https://www.razer.com/gaming-audio/razer-seiren-x) | Microphone |
| [Rode NT-USB](http://rode.com/microphones/nt-usb) | Microphone |
| [Rode NT-USB Mini](http://rode.com/microphones/nt-usb_mini) | Microphone |
| [Logitech C920](https://www.logitech.com/en-us/product/hd-pro-webcam-c920?crid=34) | Webcam |
| [Logitech C930E](https://www.logitech.com/en-us/product/c930e-webcam) | Webcam |
| [Logitech StreamCam](https://www.logitech.com/en-us/product/streamcam) | Webcam |
| [Razer Kiyo](https://www.razer.com/gaming-broadcaster/razer-kiyo) | Webcam + light |
| [Elgato HD60 S](https://www.elgato.com/en/gaming/game-capture-hd60-s) | Capture card |
| [Elgato Key Light](https://www.elgato.com/en/gaming/key-light) | Lighting |
| [Philips Hue Go](https://www2.meethue.com/sv-se/p/hue-white-och-color-ambiance-go-barbar-lampa-%28senaste-modell%29/7602031P7) | Lighting |
| [Philips Hue Color Ambiance](https://www2.meethue.com/sv-se/p/hue-white-och-color-ambiance-2-pack-e27/8718699673284) | Lighting |

The capture card is used for when connecting external video sources \(eg. a DSLR camera\) to the computer.

### Software

For when you want to have full control of the stream input and output, use [OBS Studio](https://obsproject.com/), as it will elevate the experience for both host and audience. For a great default setup, do the following:

1. Select Scene under Scenes in the bottom left
2. Add a Video Capture Device under Sources, name it Webcam
3. Add a new scene under Scenes, name it "Screen"
4. Add a Display Capture under Sources
5. In **Settings &gt; Hotkeys** find Scene and Screen and add a hotkey for the "Switch to scene" input. 

Test switching between the two scenes using the hotkey. If this does not work, in **Settings &gt; Advanced**, make sure Hotkey Focus Behavior is set to "Never disable hotkeys".

{% hint style="info" %}
Pay attention to the amount if audio inputs, there should preferably be only one, otherwise a feedback loop can occur.
{% endhint %}

![](.gitbook/assets/obs-studio%20%281%29.png)

Before pressing Start Streaming and Start Recording, in **Settings &gt; Stream** set Service and fill out the Stream Key. If you are using Twitch, this can be found in the [Twitch user account](https://www.twitch.tv/settings/profile) under Channel and Videos.

{% hint style="warning" %}
Remember to test the stream having someone else visit and verify that sound and video behaves accordingly. It is possible to tweak video and audio output settings in OBS Studio.
{% endhint %}

## Screen recording

### On Mac

1. Open Quicktime
2. Go to File &gt; New Screen Recording
3. Press the red "Record" button
4. Click the screen to record the entire area or click-and-drag around the area you want to record
5. You can record your computer's microphone audio
6. When finished, press the "Stop" button on the taskbar
7. Trim the video if needed with **⌘T** and export in the desired format.

{% hint style="info" %}
You can also download plugins like [Soundflower](https://rogueamoeba.com/freebies/soundflower/) or [Loopback](https://rogueamoeba.com/loopback/). This will allow you to record your computer's audio as well. You'll need to switch your Sound Output settings and select the right audio setting in Quicktime.
{% endhint %}

### On Iphone

1. Open Settings
2. Open Control Center
3. Open Customise Controls
4. Add Screen Recording

The Control Center \(accessed when you swipe to get menu on Iphone\) now has a white circle icon which will record your screen when clicked.

{% hint style="info" %}
If you want to import your device media to a Mac connect your device and open the builtin Image Capture app. 
{% endhint %}

## Upload to Instagram

### Image

Transfer the image to your phone, or open Chrome and go to **View &gt; Developer &gt; Developer Tools** and then click **⌘ + Shift +  M** to toggle the Mobile mode \(you can also click the mobile icon in the top left corner\). Refresh the page and it should now look like on mobile.

### Video

Transfer the video to your phone and upload using the Instagram app.

## QR codes

Having a QR code can greatly enhance the user experience as it simplifies the process of getting a digital device to find its new home, here's how to make one:

1. Visit the [QR Code Generator](https://www.the-qrcode-generator.com/) or [QR Code Monkey](https://www.qrcode-monkey.com/)
2. Choose URL and add your website address
3. Choose Save and SVG or PNG
4. Use the QR code in your design!

## CORS Anywhere

Trying to fetch a remote file but getting an error message? This API enables cross-origin requests to anywhere! Simply add `https://cors-anywhere.herokuapp.com/` before the URL and voilà!

