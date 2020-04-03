# Basics

### Installing

To download TouchDesigner, go to [Downloads  
](https://derivative.ca/download)While downloading, [create an account](https://www.derivative.ca/Login/RegisterForm.asp) so you can get a key after installation.  
[Install ](https://derivative.ca/UserGuide/Install_TouchDesigner)and start TouchDesigner.

{% hint style="info" %}
TouchDesigner works on Mac and PC. Keep in mind that on Mac there are a few restrictions related to the graphics card. For us this doesn't matter at this point.
{% endhint %}

On your first time opening TouchDesigner you'll see a lot of things happening. First you'll be asked to log in with the account you've created on the Derivate website. After doing this you will be able to use one out of the five free licence keys that come with your account. Activate one and you'll be greeted with your first TouchDesigner project.

If you want to return to the Key manager, you can find it on the top left under **Dialogs** and then **Key Manager**. 

### Navigating

Now we're ready to start exploring. One of the first things you might notice is that TouchDesigner has quite a lot happening in its interface.

![First time opening TouchDesigner](../.gitbook/assets/image%20%2815%29.png)

Don't worry, we'll go through each of these, and we'll only be using some of them, so no need to memorize everything. Before going through the interface elements, lets look at basic navigation first.

![](../.gitbook/assets/image%20%2812%29.png)

TouchDesigner works in a very similar way as the folder system on your computer. It has folders \(called OP's or operators\) and inside them you can have even more folders. The address bar on the top shows you at all times where you currently are in the path structure of your project. This path structure will become relevant as soon as we start referring to parameters or data between operators.

Although you often can achieve the same thing in various ways, TouchDesigner really starts to shine if you use it with a mouse with clickable scrollwheel. 

* Use the left mouse button in an empty area to drag the editor across the canvas.
* Hold and drag the middle mouse button to zoom in and out. \(hold the alt key and right mouse button if you don't have a middle mouse key\)
* You can also use the scroll button to zoom in and out, this can also be used to up a level or down into a component \(node\), the same can be achieved by going up with **`U`** and down with **`I`** or **`Enter`**.
* Use left mouse button to drag a select box to select multiple operators at the same time.
* If you get lost and quickly want to regain an overview, type **`H`**.



![Playback bar](../.gitbook/assets/image%20%285%29.png)

TouchDesigner works with interactive environments but also allows for scripting on the timeline, similar to what you might know from Cinema4D or After Effects. What is important to know at this point is that your project can be paused using the playback buttons here. This can be toggled using the spacebar, always keep in mind to check the playback state from your project if something isn't working, it might just be that you accidentally hit pause.

Another key component you see here on the far left is your framerate, indicated as FPS. This is currently set to 60, meaning TouchDesigner tries to refresh your entire system 60 times per second. If you have a lot of things happening in your project this framerate might be lower, the actual framerate you can find in the Menu bar, also indicated with FPS. The Realtime checkbox next to it lets you choose to render every frame, to allow for skipping frames, by default it is set to skip frames.

![Menu bar](../.gitbook/assets/image%20%2814%29.png)

Lastly we have the Palette browser on the left, and the Parameter window on the right. We'll dive into the Parameter window in a moment. The Palette browser is a place where you can drag very handy pre-build TouchDesigner components into your project, for now you can close this window. To bring it back take a look at the **Dialogs** dropdown menu.



### Operators

Operators can be seen as tiny programs that can be chained together to build all sorts of things. There are a lot of them, and they come in various types as well. Most operators work in a way that you put some type of data in the left and retrieve the manipulated data on the right.

To add an operator you can right click and in the menu select add operator, or to be much quicker, hit `TAB`.  This brings up the OP Create Dialog. Here you see the various types on the top, and you can hover over each OP to get a small description on the bottom. Hitting `TAB` again will take you to the overview of the next operator type.

![](../.gitbook/assets/image%20%2821%29.png)

The four main ones you will likely work with are TOP's, CHOP's, SOP's and DAT's. Lets briefly go into the difference between these types.

![](../.gitbook/assets/image%20%289%29.png)

**TOP**

Texture operators are **purple** and handle anything related to pixel data. These are the fastest and most powerful components TouchDesigner has. You will end up using them a lot. They can be used to do all sorts of things, from composing various images streams together, blurring, detecting edges, handling external devices like Kinects and camera's to pointclouds.

**CHOP**

Channel operators are **green** and they are mostly made to do math and logic operations. This way you can program all sorts of behavior which can in turn be placed onto parameters of other operators to automatically control them. 

**SOP**

Surface operators are **blue** and relate to shapes happening in 3D space. Here you can find basic shapes and ways to manipulate their geometry.

**DAT**

Data operators are **violet-red** and can be used to store spreadsheets, as well as do things that are more text and scripting related. DATs often go hand in hand with Python scripting. This won't be essential to start using TouchDesigner, but Python is certainly one of the things that will greatly enhance what you can do in Touch.

### Interacting with OPs

Lets try to make a basic network to understand how we can exchange information between these operators. Hit `CTRL + A` and `BACKSPACE` to remove the operators from the example file. Hit `TAB` and type the words **Constant**.  You'll see that as you type TD sorts out the OPs which match your criteria. Hit Enter and the Constant OP is sitting in your network. Repeat the process so we have two Constant OPs and one Switch OP.

You might have noticed, that each time when we select a different operator, the window on the right side of our editor changes. This is called the Parameter window, and it contains the settings of that given operator. Here we can change these settings, or create a direct link between a parameter, and a piece of data coming from somewhere else. Select one of the Constant operators and click on the color thumbnail to give it a different color.

![](../.gitbook/assets/image%20%283%29.png)

Now that we have two different colored operators, lets see how we can use them in a network setup. 

![](../.gitbook/assets/image%20%284%29.png)







