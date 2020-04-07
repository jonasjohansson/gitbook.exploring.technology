# Feedback

Now that we have movement happening in our TOP section, lets try and add some funk to this 🌈⚡

Behind our Composite, add and connect another Composite and set its operation to Add.

Make about enough space for five more operators in between these two.

Add a Feedback TOP and connect it to our first Composite TOP. Connect the other end into the second Composite.

Feedback TOPs are very powerful and allow for all sorts of experimentation and weirdness. We'll be using one to add a trail to our object.

![Here I&apos;m using Feedback TOPs to create a slit-scan effect](../../../.gitbook/assets/53231518_2554482231248275_8074991588285087744_n.png)

The feedback TOP works by pointing its Target TOP parameter to a TOP which shares the same texture as the one the Feedback TOP is receiving on its input.

Select the Feedback TOP and drag the second Composite TOP onto its Target TOP parameter.

Now at this point not much exciting things are happening, we need to create a change first.

Behind the Feedback TOP add a Transform TOP. Set its scale on both axis to 1.1.

There you go, we're getting trails! The color is still a bit boring though, lets add an HSV ADJ TOP behind the transform and set its Hue Offset to 7.

For good measure, lets add a Blur TOP behind that.

It's getting a bit too stroboscope'ey for my taste, lets add a Level TOP as the last operation. 

The Level TOP is very handy and can do a lot of the things you normally would do in Photoshop. In our case we need to dial down the opacity a bit so our effect fades out as it repeats.

In the Level TOP, under the Post section, set the Opacity to 0.95.

![](../../../.gitbook/assets/image%20%2838%29.png)

At this point your TOP network should look like this. Lets add a Null at the end and call it `final`.

