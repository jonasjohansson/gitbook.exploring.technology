# Movement with parameters

Lets get interactive. 

The plan is to have our object move along with the mouse position, we're going to make this happen using CHOPs and then connect that CHOP data to some of the parameters of the Composite OP.

Hit `TAB` to open up the operator create menu, then hit `TAB` again to move over to the CHOP section. 

Type and select the Mouse In CHOP. Place it somewhere below our TOP setup.

Move your mouse around and you will see there is already a tx and ty channel set up that changes when you move the mouse. 

### Remapping the values

Depending on your screen setup, tx ranges from -1 to 1, and ty from -0.5 to 0.5.

The parameter we are going to connect these values to is the in the Transform section of our Composite TOP. It expects a value between -0.5 and 0.5 on both the X and Y axis to have something move from the middle to the edge of the texture, this means we will have to remap the range on our tx channel to make it work for us.

Create a Select CHOP and connect it to the Mouse In CHOP.

Inside the Select CHOP, replace the \* at Channel Names with tx.

Copy and paste the Select CHOP you've just created and keep it connected to Mouse In.

Select the new copy and replace the tx value with ty.

Since the range of tx and ty are not the same, we have to select either channel separately so we can change the range of only the tx channel.

Create a Math CHOP and connect it to the Select CHOP which filters the tx channel.

The Math CHOP is something you will end up using a lot, it is incredibly handy for all sorts of things, like combining various channels and doing mathematical operations on them.

In our case we need to move over to the Range section on the Parameter window and set the values the same as the screenshot below.

![Parameters for our tx channel inside the Math OP](../../../.gitbook/assets/image%20%2833%29.png)

Now to tie it all together, lets use a Merge CHOP and connect our tx and ty channels back together.

![](../../../.gitbook/assets/image%20%2825%29.png)

To keep things tidy, lets add a Null CHOP at the end and call it `position`.

{% hint style="info" %}
If you have TD open on a second monitor the Mouse In values might look different, in that case look at the highest and lowest values when moving your mouse around to determine how it should be remapped.
{% endhint %}

### Connecting our values to the Compose TOP

Ok now, just as we've used CHOP data to control our switch, we're going to use the mouse data to control the position of our triangle.

Activate the `position`Null CHOP by clicking on the lower right plus symbol.

Select the Composite TOP and highlight the Transform section.

Here we see two values for Translate. Go ahead and drag the tx channel onto the first value. As you let go select CHOP Reference in the dropdown.

Now repeat the process for ty.

There we go! Our triangle is moving along with our mouse! If you want to have a better look you can right click on the Composite TOP and select View.

