# Making a switch

Lets try to make a basic network to understand how we can exchange information between these operators. Hit `CTRL + A` and `BACKSPACE` to remove the operators from the example file. Hit `TAB` and type the words **Constant**.  You'll see that as you type TD sorts out the OPs which match your criteria. Hit Enter and the Constant OP is sitting in your network. Repeat the process so we have two Constant OPs and one Switch OP.

You might have noticed, that each time when we select a different operator, the window on the right side of our editor changes. This is called the Parameter window, and it contains the settings of that given operator. Here we can change these settings, or create a direct link between a parameter, and a piece of data coming from somewhere else. Select one of the Constant operators and click on the color thumbnail to give it a different color.

![](../.gitbook/assets/image%20%284%29.png)

Now that we have two different colored operators, lets see how we can use them in a network setup. 

![](../.gitbook/assets/image%20%286%29.png)

If you look closely at these operators, you can see that they have a small opening on either side. Some operators will only have one, most of them have two, it depends on its functionality. In the case of the constant and switch, they can receive a texture from another TOP and manipulate or add onto it.

Hover over the output of either constant and drag with your left mouse key to the input of the switch operator. As you can see, the switch operator is able to have multiple inputs, the constant can only have one. Right clicking on a wire allows you to delete the connection. 

![](../.gitbook/assets/image%20%285%29.png)

With the switch selected, you can see in the parameter window \(hit `P` to bring this up when hidden\) that it has a slider for Index and a toggle to blend between inputs.

At the bottom of the switch you see the operators which are connected to the switch, hitting the up arrow allows you to change the order in which they are connect.

Now drag the slider from left to right, you see it has a range from 0 to 1, and that when sliding the color on the slider changes between the two constant operators. You've just made your first switch! Now think about this for a second, this opens up a whole lot of possibilities, just by having this switch that allows us to change what we see between multiple inputs.

