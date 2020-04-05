# Button

Lets see how we can drive this with something interactive. Hit `TAB` and click on the COMP section. We haven't handled COMPs yet, this section is a bit of of a catch all term for several things. Including some UI elements, things needed for 3D rendering, and Containers and Base elements which allow you to put things into them, a bit like folders.

We'll be dealing a lot more with COMP elements in the future, but for now you can type or select Button.

![](../../.gitbook/assets/image%20%2829%29.png)

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

