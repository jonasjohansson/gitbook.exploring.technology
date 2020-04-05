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

![First time opening TouchDesigner](../../.gitbook/assets/image%20%2818%29.png)

Don't worry, we'll go through each of these, and we'll only be using some of them, so no need to memorize everything. Before going through the interface elements, lets look at basic navigation first.

![](../../.gitbook/assets/image%20%2815%29.png)

TouchDesigner works in a very similar way as the folder system on your computer. It has folders \(called OP's or operators\) and inside them you can have even more folders. The address bar on the top shows you at all times where you currently are in the path structure of your project. This path structure will become relevant as soon as we start referring to parameters or data between operators.

Although you often can achieve the same thing in various ways, TouchDesigner really starts to shine if you use it with a mouse with clickable scrollwheel. 

* Use the left mouse button in an empty area to drag the editor across the canvas.
* Hold and drag the middle mouse button to zoom in and out. \(hold the alt key and right mouse button if you don't have a middle mouse key\)
* You can also use the scroll button to zoom in and out, this can also be used to up a level or down into a component \(node\), the same can be achieved by going up with **`U`** and down with **`I`** or **`Enter`**.
* Use left mouse button to drag a select box to select multiple operators at the same time.
* If you get lost and quickly want to regain an overview, type **`H`**.



![Playback bar](../../.gitbook/assets/image%20%287%29.png)

TouchDesigner works with interactive environments but also allows for scripting on the timeline, similar to what you might know from Cinema4D or After Effects. What is important to know at this point is that your project can be paused using the playback buttons here. This can be toggled using the spacebar, always keep in mind to check the playback state from your project if something isn't working, it might just be that you accidentally hit pause.

Another key component you see here on the far left is your framerate, indicated as FPS. This is currently set to 60, meaning TouchDesigner tries to refresh your entire system 60 times per second. If you have a lot of things happening in your project this framerate might be lower, the actual framerate you can find in the Menu bar, also indicated with FPS. The Realtime checkbox next to it lets you choose to render every frame, to allow for skipping frames, by default it is set to skip frames.

![Menu bar](../../.gitbook/assets/image%20%2817%29.png)

Lastly we have the Palette browser on the left, and the Parameter window on the right. We'll dive into the Parameter window in a moment. The Palette browser is a place where you can drag very handy pre-build TouchDesigner components into your project, for now you can close this window. To bring it back take a look at the **Dialogs** dropdown menu.



### Operators

Operators can be seen as tiny programs that can be chained together to build all sorts of things. There are a lot of them, and they come in various types as well. Most operators work in a way that you put some type of data in the left and retrieve the manipulated data on the right.

To add an operator you can right click and in the menu select add operator, or to be much quicker, hit `TAB`.  This brings up the OP Create Dialog. Here you see the various types on the top, and you can hover over each OP to get a small description on the bottom. Hitting `TAB` again will take you to the overview of the next operator type.

![](../../.gitbook/assets/image%20%2829%29.png)

The four main ones you will likely work with are TOP's, CHOP's, SOP's and DAT's. Lets briefly go into the difference between these types.

![](../../.gitbook/assets/image%20%2812%29.png)

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

![](../../.gitbook/assets/image%20%284%29.png)

Now that we have two different colored operators, lets see how we can use them in a network setup. 

![](../../.gitbook/assets/image%20%286%29.png)

If you look closely at these operators, you can see that they have a small opening on either side. Some operators will only have one, most of them have two, it depends on its functionality. In the case of the constant and switch, they can receive a texture from another TOP and manipulate or add onto it.

Hover over the output of either constant and drag with your left mouse key to the input of the switch operator. As you can see, the switch operator is able to have multiple inputs, the constant can only have one. Right clicking on a wire allows you to delete the connection. 

![](../../.gitbook/assets/image%20%285%29.png)

With the switch selected, you can see in the parameter window \(hit `P` to bring this up when hidden\) that it has a slider for Index and a toggle to blend between inputs.

At the bottom of the switch you see the operators which are connected to the switch, hitting the up arrow allows you to change the order in which they are connect.

Now drag the slider from left to right, you see it has a range from 0 to 1, and that when sliding the color on the slider changes between the two constant operators. You've just made your first switch! Now think about this for a second, this opens up a whole lot of possibilities, just by having this switch that allows us to change what we see between multiple inputs.

### Button

Lets see how we can drive this with something interactive. Hit `TAB` and click on the COMP section. We haven't handled COMPs yet, this section is a bit of of a catch all term for several things. Including some UI elements, things needed for 3D rendering, and Containers and Base elements which allow you to put things into them, a bit like folders.

We'll be dealing a lot more with COMP elements in the future, but for now you can type or select Button.

![](../../.gitbook/assets/image%20%2827%29.png)

Select the button, and in the parameter window under the Button section change the button type to Momentary. Now right click on the green opening on the side, this is a shortcut to select an operator that will be instantly wired to the button's output. Type or select a null.

You find Null's in all of the four main operator types, they don't actively do anything, but they serve as a way to preview what they pass on and help you to keep your project tidy. It is good practice to add a null in parts of your program where you have achieved a certain goal and want to be able to easily derive from that point. Double click on the name on the bottom of the null and rename it to `button_output.` 

Now, at this point we can take a look and see if our button works as expected. But how are we going to do this if we can only drag the button? Clicking doesn't seem to do anything. This is because at the moment the preview we see of our button isn't active. Click on the tiny + symbol on the lower right corner. Your button should now look like the one in the picture. Remember that if you want to be able to move the button, you'll need to deactivate it again.

What you should have been able to see when clicking on the active button, is the null next to it jumping between 0 and 1. This gives us the state of the button as a CHOP stream. Lets use this to drive the state of our switch. Make the null active using the + symbol, and then select the switch. What you can then do is drag the contents of the null to the number box behind the Index parameter of the switch. As you hover over the box, your cursor should turn into a white arrow pointing to the right with a small + symbol.

Letting go gives you three options. "Export CHOP", "CHOP Reference" and "Current CHOP Value". We'll want to have the "CHOP Reference". This basically drops in a Python expression pointing to our Null and getting the data stream we selected \(you can undo this later by opening up the Index parameter dropdown and selecting the grey box, removing the referenced value\).

Upon doing this we get to see a small dotted arrow pointing between the null and the switch. Indicating there is a symbolic link between these operators.

Our switch is now interactive and changes input when we press the button. Very cool, but it would be even cooler if it would be one of those slow fades. We can do this by adding  a bit of lag into our CHOP data. Add a Lag operator between the button and the null \(right click on the wire to directly add an operator in between\).  Our Lag operator is currently set to 0.2 lag on all settings. This is a bit too fast for my taste, hold the middle mouse button onto the Lag parameter and a small widget appears showing various increments. The .1 increment in the middle works fine, go ahead and drag to the right until the parameter are both set to 1.

Now lastly we'll need to toggle "Enable blend mode" on our switch and we get to see a smooth fading effect when clicking our button.

{% hint style="info" %}
Pro tip. Are you unsure what a certain components does or how you should use it?   
Try right clicking on it and see if it gives you the option "Operator snippets". These are small examples that you can even copy paste.
{% endhint %}

### Flying TOPs!

Time to make something!

We'll be creating a little object that moves along with our mouse, and we'll add some special effects on top. 

To start, right click on an empty spot in the editor, and select Add Operator. Now select COMP and click on Container. As said, a container is an object we can use to add structure and hierarchy to our projects. In our case, lets rename the container to `Exercise_1_FeedbackTOP`. Click on the Layout section in the parameter window and set the width and height to 1280 by 1280. Lets also do some groundwork here and under the Look section, type `./final` in the Background TOP parameter. Later this will tell the container to look at the operator called final inside itself to show us a preview.

Since our visual will be driven by changing around TOP parameters only, we will need an empty looking TOP to start with. Go ahead and add a Constant OP and set its Alpha to zero.

By default the Constant OP is set to 256 by 256 pixels. This is quite small, lets make it the same size as our parent Container. You can do this by going to the Common section and under Resolution, remove the first parameter and type `parent().width`, then in the next one you type `parent().height`.  Another method would be to select the dropdown of Output Resolution, and select Parent panel size.

![](../../.gitbook/assets/image%20%2821%29.png)

An easy way to check if it really is the right size, is by middle mouse clicking on any operator. This will give you some of its key features.

Now we are ready to pick out our little object. In my case I'd like to start with a circle OP. If you look under the Circle section in the parameters, you can see there are a lot of options. You can do all sorts of things here! Lets go down to the Polygon toggle and set it to On and make sure Sides is set to three.

![](../../.gitbook/assets/image%20%2824%29.png)

{% hint style="info" %}
Feeling adventurous? See if you can try to create a different shape here, using some of the other operators like Rectangle or a combination of OPs. You could even use a Movie File In OP to load in an image.
{% endhint %}

### Composite

To place our object onto the Constant operator texture. We can use a Composite OP. This is an extremely powerful operator that you'll use on a regular basis. Think of it a bit as the Layer composite options in Photoshop, but in real-time!

Set the Operation to Add, and move over to the Transform section. For our triangle to show up correctly, we'll have to set the Fixed Layer to Input 1, and Pre-fit Overlay to Native Resolution. Your triangle should now show up as a small object in the middle.





