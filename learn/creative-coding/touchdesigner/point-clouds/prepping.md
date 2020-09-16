# Prepping

Now that we have our point cloud, or at least, a mesh generated from our point cloud. There are a few things we can do or could have done. If you weren't quite happy with the mesh, it would have been an option to export the raw point cloud and take it into another software like Cinema 4D, Houdini or MeshLab. Here you can do all sorts of operations to clean up your point cloud. Such as removing stray points, or generating new points.

In our case I was quite happy with the mesh version of the model, and want to take it into CloudCompare to sample an equally distributed point cloud based on our mesh.

{% embed url="http://cloudcompare.org/" %}

When we import our mesh into CloudCompare, we simply select the geometry in the sidebar and click on the icon in the top bar which says Sample points on a mesh.

![](../../../../.gitbook/assets/image%20%2844%29.png)

We are then asked how many points we'd like to have, default worked fine for me.

![](../../../../.gitbook/assets/image%20%2851%29.png)

Now our point cloud is equally distributed. Go ahead and export it to PLY.

{% embed url="https://youtu.be/1OFE\_2sUdrQ?t=265" %}

If you'd like to see this step as a video check it here.



