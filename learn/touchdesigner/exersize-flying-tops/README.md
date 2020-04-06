# Exercize - Flying TOPs



Time to make something!

We'll be creating a little object that moves along with our mouse, and we'll add some special effects on top. 

![The mouse goes, wheee!](../../../.gitbook/assets/flying_tops.gif)

### Example file

If you prefer to follow along using a working example, please use this file.

{% embed url="https://drive.google.com/file/d/1Amb2DAPgNhhP9aqLHYnm\_IlvVkDy99V9/view?usp=sharing" %}

### An empty constant

To start, right click on an empty spot in the editor, and select Add Operator. 

Now select COMP and click on Container. As said, a container is an object we can use to add structure and hierarchy to our projects. In our case, lets rename the container to `Exercise_1_FeedbackTOP`. 

Click on the Layout section in the parameter window and set the width and height to 1280 by 1280. Lets also do some groundwork here and under the Look section, type `./final` in the Background TOP parameter. Later this will tell the container to look at the operator called final inside itself to show us a preview.

Since our visual will be driven by changing around TOP parameters only, we will need an empty looking TOP to start with. Go ahead and add a Constant OP and set its Alpha to zero.

By default the Constant OP is set to 256 by 256 pixels. This is quite small, lets make it the same size as our parent Container. You can do this by going to the Common section and under Resolution, remove the first parameter and type `parent().width`, then in the next field you type `parent().height`.  Another method would be to select the dropdown of Output Resolution, and select Parent panel size.

![](../../../.gitbook/assets/image%20%2823%29.png)

An easy way to check if it really is the right size, is by middle mouse clicking on any operator. This will give you some of its key features.

### Circle OP

Now we are ready to pick out our little object. In my case I'd like to start with a circle OP. If you look under the Circle section in its parameters, you can see there are a lot of options. You can do all sorts of things here! 

Lets go down to the Polygon toggle and set it to On and make sure Sides is set to three.

{% hint style="info" %}
Feeling adventurous? See if you can try to create a different shape here, using some of the other operators like Rectangle or a combination of OPs. You could even use a Movie File In OP to load in an image.
{% endhint %}

