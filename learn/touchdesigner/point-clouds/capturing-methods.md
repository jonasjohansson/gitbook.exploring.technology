# Capturing methods

There are many ways to capture point cloud data. Their usage depends on your budget, the scene you're trying to capture. If it's for instance indoors or outdoors, the range you need, the density of your capture etc.

A common way to capture quite good quality point clouds without any special hardware, is through photogrammetry. This method compares a large collection of images taken from slightly different angles in order to interpret the shifts in perspective to calculate distances.

Stereogrammetry is very similar, accept that it is able to do it many times a second, this method works exactly like your eyes. Two camera's are placed at a fixed distance, allowing an algorithm to compare the images to calculate depth through perspective.

The more high end side of things are done using a technique called Time of Flight and LiDAR. Here laser beams are shot at a high speed at an array of angles. These bounce back and the camera is able to detect how long it took them to come back. This delay is then used to calculate the distance of each point.

A last slightly off beat one, is structured light, here a combination of a regular projector and a camera is used. The projector sends out white lines which hit the surface of what you're trying to scan. The camera sees these bars as they are deformed by the objects they hit. This deformation can then be used to calculate the distance.

### Devices

There are many ready to use devices that can capture point clouds, there's a good chance you even have one in your phone \(the iPhone X for instance\). One that to this day is still very popular within the creative coding community is the Microsoft Kinect. The Kinect 2 uses Time of Flight, and also has sophisticated tracking of people's movements using skeleton tracking. Kinect Azure is coming to Europe this year with an even denser point cloud.

Intel has been creating a wide range of capturing devices under its RealSense line, which consist of various types of methods and applications, both big and small. Made to work with VR/AR or autonomous robots, as well as to track people in open spaces.

The ZED uses stereogrammetry and calculates a mesh on the fly.

Then there's Ouster, which is a version of LiDAR and sits on the high end of the market.

The great news is that all of these are supported directly in TouchDesigner. You'll have to do some research depending on your user case to what's right for you. All of them have pro's and con's of some sort.

### File formats

One of the most common formats, and one that TD supports natively is the PLY format. Though if you want to have more information than PLY can store it can also be good to use the EXR format. Using the Point File Select TOP you can then choose which set of channels you'd like to grab.

