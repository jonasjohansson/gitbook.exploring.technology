# Capture

In order to make our own point cloud, we'll need a solid object with ideally a smooth surface and not too many thin surfaces or details. This technique also works for larger things such as buildings, but to keep things simple I'm going to assume you have an object along the lines of a teakettle or a flower pot. 

We'll be using a piece of software called Metashape to do the photogrammetry. Go ahead and download and install the 30 day trial version.

{% embed url="https://www.agisoft.com/" %}

With the trial version setup, lets try to get an understanding of photogrammetry and what steps we need to take.

Photogrammetry works, by having an algorithm look at the same spot from many different angles. By slightly changing the perspective of each photo, the software compares these and tries to make a best guess on how the images overlap. With each perspective shift, the parts of the photo that can be aligned with overlapping pixels, allow the software to calculate the distance of that point. You are doing this all the time, it's the reason we have two eyes, and that they are slightly apart from each other. Your brain compares the two images, and uses it to help you see depth.

Fun fact, did you ever notice how pidgeons move their heads like they're doing some kind of crazy funk walk? That's not the bird seed.. They have eyes which are too close together to see distance if their perspective doesn't change enough. By moving their heads around it helps them to see how far away things are, the \(admit-tingly weird and slightly awkward\) wonders of nature!

Ok, now that you have an idea about what the computer will try to do, lets take a look at how we can go about this. Photogrammetry is great in theory, but in practice, it can be quite finicky, so it requires clean and consistent images to work well. Try to keep the following in mind when shooting your photos.

* Make sure your object is easy to track, ie. not too weird and fuzzy materials shapes and surfaces, be careful with certain detail.
* Place your object in a clear environment without any distracting things in the back or foreground
* Start moving clockwise around the object and begin taking photos.
* Take a lot of images, basically as much as your computer can handle in an ok amount of time. Mine was 300 images, but also took 3 hours to generate at high density.
* Try to get as many angles as possible.
* Make sure to get consistent lighting all around the object, you want to have equally bright colors from all sides.

![200 images of my test trashcn](../../../.gitbook/assets/image%20%2831%29.png)

After you've loaded the photos over to your computer, you can select all of them and drag them into Metashape.

Once its loaded you can click on the Workflow dropdown menu, and select Align Photos. Keep the settings as they are and hit OK. After some moments you should see something like the following screenshot.

![High resolution of our mesh](../../../.gitbook/assets/image%20%285%29.png)

Now, you'll see that a lot of the points we got, are from places we're not really interested in. To make sure we're not calculating all those for our high density point cloud, we can change the bounding region using the following tool. Set it to the area you are interested in. 

![](../../../.gitbook/assets/image%20%2815%29.png)

After you're happy with your bounding region we can calculate the high density version of our point cloud. Click Workflow again, and select Build Dense Cloud. If you're unsure about the strength of your computer, its best to select a lower setting here.

Calculating the dense cloud can take a very long time. It really depends on your use case.

Once it's done you'll see a lot more points on the screen, depending on how it went, it might look very fuzzy, filled with gaps, or way too dense in some areas.

What we're going to do, is rather than directly use the point cloud from MetaShape, is converting this point cloud to a mesh, and then prepping a point cloud based on this mesh in another program.

Go ahead and click Workflow and then Generate Mesh.

The result will look a lot better.

![](../../../.gitbook/assets/image%20%2818%29.png)

Once you're happy with the mesh you see, lets go to File and hit Export Model \(OBJ\).



Further resources: [https://styly.cc/tips/photogrammetry\_discont\_metashape/](https://styly.cc/tips/photogrammetry_discont_metashape/)

