---
description: Written by Jonas Johansson
---

# Browser Point Clouds

A point cloud is a collection of points in 3D space. A point can be understood best compared to a pixel in an image, where the pixel has four channels for color RGBA and the point has three channels for position XYZ.

### Install

Download [Metashape](https://www.agisoft.com/) and [CloudCompare](https://cloudcompare.org/). Alternatively use [Display Land](https://apps.apple.com/us/app/display-land-3d-model-scanner/id1436223202).

### Import

#### Video

Go to `File > Import > Import Video…` and select the video file. When asked, create a folder for the extracted frames.

#### Image

Go to `Workflow > Add Folder…` or `Workflow > Add Images…`

### Workflow

The following steps will process the images and create a textured mesh.

1. Go to `Workflow > Align Photos…` and choose Medium accuracy to save time.
2. Once loaded, go to `Workflow > Align Photos…`and choose Medium quality.
3. `Workflow > Build Dense Cloud…`
4. `Workflow > Build Mesh…`
5. `Workflow > Build Texture…`
6. `File > Export > Export model…`
7. Import the model in CloudCompare and `Edit > Mesh > Sample Points` to generate a point cloud.
8. Select the sampled mesh and save as PLY \(binary\)

## Examples

* [https://browser-point-clouds.glitch.me/three-ply.html](https://browser-point-clouds.glitch.me/three-ply.html)
* [https://browser-point-clouds.glitch.me/aframe-ply.html](https://browser-point-clouds.glitch.me/aframe-ply.html)
* [https://browser-point-clouds.glitch.me/three-img-ply.html](https://browser-point-clouds.glitch.me/three-img-ply.html)
* [https://browser-point-clouds.glitch.me/three-img-ply-interactive.html](https://browser-point-clouds.glitch.me/three-img-ply-interactive.html)

