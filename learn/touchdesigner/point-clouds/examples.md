# Examples

You've probably spend a moment looking at the colorful image at the start of this article. It is a screenshot of a VR experience done by a collective from London called Marshmallow Laser Feast. Within the VR headset, you get to see nature through the perspective of different animals, turning into a wild and wondrous virtual journey, passing by 3D scanned landscapes.

{% embed url="https://vimeo.com/140057053" %}

The way they made this experience, is by using special camera techniques called LiDAR. This is a very quickly rotating laser which scans the area and measures the distance with each beam it sends out. Resulting in a 3D image of millions of points.

After preparing the scene into a real time environment \(in their case VVVV\). They work very hard on shaping this landscape using a computer language called GLSL \(OpenGL Shading Language\). This language is designed to work on your graphics card \(GPU\), and is incredibly fast and good at handling all these millions of points. This is an important part to realize about point clouds, they can be quite heavy to run and manipulate in real time, meaning that depending on the number of points, you'll need a fast graphics card. GLSL runs at the core of most enviroments these days that are handling computer graphics, such is also the case with TouchDesigner and many others, what they all share is a heavy and clever use of GLSL.

The real magic which makes a project like the one from MLF so vivid and impressive, is the way they are able to manipulate the points. By calculating simulated physics, they can add forces such as gravity and magnetism or even behavior you might know from fluids, which influences the points and makes them move and react in a way which gives them character.

![Remains by Quayola](../../../.gitbook/assets/image%20%2846%29.png)

[https://quayola.com/work/series/remains-series.php](https://quayola.com/work/series/remains-series.php)

Point clouds don't always have to be shown in real time, or even in movement, to convey an artistic image. Quayola here takes advantage of the still-image format, by sampling an extremely high density point cloud. Which afterwards isn't shown by rendering basic points, but by placing those points into a 3D environment which renders with correct lighting and shadow. Resulting into these ghostly and beautiful images.

