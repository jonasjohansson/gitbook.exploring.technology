# Performance

### GPU  and CPU

One of the reasons why we can have these dense point clouds, is because of our graphics card \(GPU\). Anyone handling large amounts of this type of data will need to have a capable graphics card. One of the things to look out for when designing with point clouds, is to make sure that all operations you're doing on the points themselves, stays on the GPU side of your computer. In the case of TouchDesigner that means that you're only moving things through TOP's and Geo operators, as soon as you're converting them to CHOPs or SOP data, you'll lose this advantage and create a bottleneck in your performance.

### Gotchas

As you might have guessed, point clouds can be very demanding on your computer, make sure you are using an adequate tool for the job if you intend on creating visuals that require a lot of computing power.

The free version of TouchDesigner supports textures up to 1280x1280 pixels. This is enough for some things, but if you have a pointcloud with more than 1.638.400 points, you'll need to have a different licence.

Positions aren't the whole part of the story, depending on what you'd like to do with your point cloud, you'll need additional information such as normals, UV maps, color information or other things. Some of these you can generate or bake into the point cloud yourself.





