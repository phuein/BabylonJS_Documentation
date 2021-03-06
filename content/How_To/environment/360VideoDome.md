---
PG_TITLE: How To Use 360 Video
---

# How To 360 Video
360 Video is a simplex mix of specific geometry, textures, and material properties; however, rather than put the burden on you to figure out how to connect them, we've created the VideoDome.

## VideoDome
VideoDomes rely heavily on the [VideoTexture](/classes/VideoTexture) class, check out it's documentation so that some parameters make more sense.
The source video itself should be "Equirectangular", without an equirectangular source the class won't function correctly.

## VideoDome Code
Within the playground you can copy and paste the following into your scene and then adjust the options.

```javascript
videoDome = new BABYLON.VideoDome("testdome", url, {<options>}, scene);
```

All of the settings in the options object are optional, but the object itself is not. Please provide an empty object at minimum.
All the options are based through the corresponding classes, mainly the dome geometry and the VideoTexture:

* resolution=32: Integer, defines the resolution of the sphere used to host the video. Lower resolutions have more artifacts at extreme fovs
* clickToPlay = false: Add a click to play listener to the video, does not prevent autoplay
* autoPlay = true: Automatically attempt to being playing the video
* loop = true: Automatically loop video on end
* size = 1000: Physical radius to create the dome at, defaults to approximately half the far clip plane
* poster: URL of the image displayed during the video loading or until the user interacts with the video
* useDirectMapping = true: Use a direct mapping technique to render the video. You should leave this value on unless you want to use the `fovMultiplier` property

* [Playground Example of a VideoDome](https://www.babylonjs-playground.com/#SQ5UC1#1)

## FOV adjustment
Sometimes 360 Video can feel an uncomfortable distance from the camera, to help with this a material based FOV adjustment is available.
Adjust it between 0.0 and 2.0 with the following code.

```javascript
videoDome.fovMultiplier = newValue;
```

Please note that `fovMultiplier` only works when using `useDirectMapping = false` creation option.

As a warning, the further the value gets from 1 the more distortion will be visible. Higher resolutions on the video dome help reduce, but not eliminate, this.

* [Playground Example of a VideoDome using fovMultiplier](https://www.babylonjs-playground.com/#SQ5UC1#0)

# Further Reading

## Advanced

[VideoTexture](/classes/VideoTexture)
