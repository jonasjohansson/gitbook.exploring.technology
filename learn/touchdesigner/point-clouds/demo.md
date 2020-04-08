# Demo

During this workshop we'll be exploring two ways of making a point cloud. One is using a depth camera called a Kinect, and using a technique called photogrammetry.

![](../../../.gitbook/assets/image%20%2840%29.png)

{% embed url="https://docs.derivative.ca/Kinect" %}

The Kinect gives us a depthmap, which is a pointcloud, but one which only shoots points from one direction. Therefore creating gaps in the capture. This can be merged by using several capture devices from different angles, but in the end delivers an image that's more suitable for tracking movement than having fine detail.

