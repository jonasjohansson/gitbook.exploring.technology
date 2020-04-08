# Point clouds

### What are Point Clouds?

![In The Eyes of The Animal by Marshmallow Laser Feast](../../../.gitbook/assets/image%20%282%29.png)

Point clouds are essentially files that contain a bunch of points in 3D space. That's basically at the core. You can think of these points in a similar way as pixels in an image file. Just as a pixel in an image usually has 3 or four channels \(RGBA\). A point cloud file has three channels for each axis. \(XYZ\). Now, a point can also contain additional information, such as a color, a radius, a normal direction or some other type of information, for instance a label telling what this point represents, such as the location of a satellite or a star.

There are several formats that can be used to store this information. Just like with images or video you have different formats. Depending where you get your point cloud from, it can be set to a specific file format. TouchDesigner is capable of handling most common ones, such as PLY and OBJ. 

A common way to store point clouds for instance, is by storing them in the color values of an image. In this case RGB colors actually represent XYZ space. This method also helps to keep performance high \(we'll get to that in the GPU/CPU section\).



### Gotchas

* Resolution limit on free version



### GPU  and CPU





