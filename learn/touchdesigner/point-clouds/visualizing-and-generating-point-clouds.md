# Visualizing and generating point clouds

{% embed url="https://vimeo.com/38874664" %}

At the core of visualizing point clouds, lies a technique called instancing. What this does, is sending the geometry of a simple object to the graphics card, along with all  the points of our point cloud. This way, rather than storing information for all those locations, we just draw a copy of the same object over and over. Creating a very efficient pipeline.

Instancing enables most of what you see happening with crazy point cloud effects these days. Any drawing of points and objects and their motion is entirely done on the GPU using GLSL \(shaders\).

We'll be looking at getting a point cloud running in TouchDesigner, how it can be drawn, and have some fun interacting with a point cloud that's set up to be affected by fluid dynamics.

Go ahead and download this example file.

{% embed url="https://drive.google.com/file/d/1CVHEsy4S\_zzk1r\_nK5QQwZc9heWqj4mT/view?usp=sharing" %}

### Re-meshing

{% embed url="https://vimeo.com/274494520/379ec22165" %}

Here is a project I worked on some years back, where you can see how the meshes of photogrammetry can be very helpful too. They could be the scene of a video game or a movie.   
And these days taken into places like TD to create realtime experiences.





