---
published: false
title: Making a scene
---
When you start implementing your driving simulator experiment, the first thing you'll work on probably is the scene. You may want to reuse an existing one from a previous project, maybe modify it, or start from scratch to build something tailored to your needs.

![scene.png]({{site.baseurl}}/images/scene.png)

In this article, we'll explain how we built the scene from the above screenshot, starting from nothing.

# Road network

As we [previously mentioned](/opendrive), the road network is a very important piece of our simulation, for which we need both the 3D representation and its logicial description (i.e. OpenDRIVE). To do that, we use [RoadRunner](https://www.mathworks.com/products/roadrunner.html), which is our favorite tool for that specific work. If you've played any [city-building game](https://en.wikipedia.org/wiki/City-building_game) (e.g. [SimCity](https://en.wikipedia.org/wiki/SimCity), [Cities: Skylines](https://en.wikipedia.org/wiki/Cities:_Skylines)), you know that creating roads and cities can be quite a fun activity if you're given the right tools. It really feels like RoadRunner understands that, and drawing any road network with this software is effortless and can even feel rewarding once you've accomplished your goal in such a short amount of time.

RoadRunner also offers tools to create the scene beyond the road network. This includes vegetation, buildings, etc. However, we're not big fan of those features, as Unreal Engine has both more assets and tools to build your world from the ground up.

![scene_rr.png]({{site.baseurl}}/images/scene_rr.png)

So what you see in the image above is the end product as far as RoadRunner is concerned. Roads, surfaces between them, and that's pretty much it. From that, the import/export to Unreal Engine is also very simple, as RoadRunner offers native support to this engine (as well as Unity, and a wide range of other tools).

# Above the ground

As mentioned, all our "above ground" scene creation is done within Unreal Engine, as it offers tools that are easy to use and ensure optimal performance, since we want our scenes to render at (at least) 60Hz.

Beyond tooling, Unreal Engine's [Marketplace] offers a huge collection of ready-to-use assets, at very attractive prices. Epic Games is even giving away free assets as part of their [Free For The Month] and [Permanently Free Collection](https://www.unrealengine.com/marketplace/en-US/assets?tag=4906). All that allowed us to grow our asset library at very low cost.

It's also worth mentioning that all of [CARLA](http://carla.org/)'s assets are free to use under a permissive licence (CC BY-SA, IIRC), you can find them [here](https://github.com/carla-simulator/carla/blob/master/Util/ContentVersions.txt). They include everything you need to build driving simulation environments, so that's a great way to get started.

## Vegetation

Whatever type of scene you're doing, you'll probably want some sort of vegetation within it. From forests and fields along highway, to plants and trees along sidewalks, vegetation is something that makes your scene feel more realistic. 

![foliage.png]({{site.baseurl}}/images/foliage.png)

Unreal Engine has a great [Foliage Tool](https://docs.unrealengine.com/en-US/BuildingWorlds/Foliage/index.html), which makes it very easy to place large amounts of various kind of vegetation, all the while ensuring optimal performance, so that your framerate won't drop even if you have a wheat field with 3 million blades.

The [Marketplace] has tons of foliage assets, some of them free! The [Project Nature](https://www.unrealengine.com/marketplace/en-US/profile/Project+Nature) is one example of a mutitude of high-quality and free vegetation. Between those and all the assets that went [Free For The Month], I don't think we'll ever need to buy a vegetation asset pack.

## Buildings

Unless you're doing highway scenes, you're going to want some types of buildings. And if you're doing urban scenes, you'll want those buildings to look nice up close, and not be a simple flat texture. 

![buildings.png]({{site.baseurl}}/images/buildings.png)

I went through all of the [Marketplace] and looked at all buildings packages. We've bought a few, and I can recommend those we use most often.

By far, our favorite is [City Downtown](https://www.unrealengine.com/marketplace/en-US/product/city-downtown-pack). It includes a lot of assets, and tools to easily create modular buildings or even fully [procedural buildings](https://www.youtube.com/watch?v=6YjQnI4UdIM), that even though are advertised as "background", are realistic enough for us to use throughout our city.

This package also allows creation of custom buildings types, that can then be generated with its wonderful creation tools. So we've been able to import other assets, such as [European Buildings](https://www.unrealengine.com/marketplace/en-US/product/european-buildings-facades) or some [Quixel](https://quixel.com/megascans/collections?category=environment&category=urban&category=neoclassical-modular-building) façades, which by themselves are too cumbersome to manipulate to create full buildings. Now we can create a full row of Paris-looking buildings in a couple of minutes!

Some other assets we use include [Urban City](https://www.unrealengine.com/marketplace/en-US/item/f60f01b8bbbb45d293c72d4a6a6ad136) or [Suburban Houses](https://www.unrealengine.com/marketplace/en-US/item/29640076ec15451a8e70a29ec629736d). If you're interested, I can give a more thorough list of useful marketplace assets, but feel free to browse youself.

## Props

In the 3D world, props (coming from theater's [property](https://en.wikipedia.org/wiki/Theatrical_property)) are all static small objects that are present in a scene. Those include poles, fences, streetlights, bins and so on. Same as other assets, you'll find plenty of those on the Marketplace.

![props.png]({{site.baseurl}}/images/props.png)

Placing them can be tedious, and also requires some creativity to arrange them in a realistic manner. Assets from the Marketplace often come with demo scene (e.g. [City Asset Pack](https://www.unrealengine.com/marketplace/en-US/item/83dd68e4ce774c18b89f042cb52670e4)), which you can use as reference. To go even further, you can also find complete scenes (e.g. [Downtown West](https://www.unrealengine.com/marketplace/en-US/item/cffe32471e5f442b9aff97b48a235e82), [Construction Site](https://www.unrealengine.com/marketplace/en-US/item/83bf93f36f794cdab4ecfb70aec4a703)), that contain a variety of assets, which you can use individually, or copy as a whole into your own scene.

The Marketplace not only has assets, but also tools. [NVSplineMesh](https://www.unrealengine.com/marketplace/en-US/item/bfeae2f849004189a73a5af98d6f7d8b) is a must-have for any props that you'll want to distribute along a [spline](https://en.wikipedia.org/wiki/Spline_(mathematics)), such as fences or poles.

## Landscapes?

One last thing to mention is the ability to [create](https://docs.unrealengine.com/en-US/BuildingWorlds/Landscape/Creation/index.html) complete landscapes, or buy some from the Marketplace (e.g. [France Fields](https://www.unrealengine.com/marketplace/en-US/product/32a96e6b005344b49d93d888f2e0ec59) [Landscape Smart Material](https://www.unrealengine.com/marketplace/en-US/item/227d99e4b78048ce934ce0afabf523d1)).

[![landscape.jpg]({{site.baseurl}}/images/landscape.jpg)][France Fields]

However, landscapes imply modifying the ground, which is generated from RoadRunner. So if we want to have our roads following the landscape geometry (which we do), we have a problem on our hands. How to alter roads' geometry to fit the landscape?

All our road manipulation tools are within RoadRunner, so we can't simply edit the roads in Unreal Engine. Can we somehow import the landscape in RoadRunner? The answer is yes, but it's not trivial.

Most Unreal Engine's landscapes use [heightmaps](https://www.worldofleveldesign.com/categories/ue4/landscape-heightmap-guide.php), which can be imported in RoadRunner using the [Elevation Map Tool](https://www.mathworks.com/help/roadrunner/ug/Elevation-Map-Tool.html). However, Unreal Engine exports heightmaps to PNG, while RoadRunner can import IMG, DEM, JPG2000 and TIFF. I tried converting from PNG to TIFF using [Pillow](https://pillow.readthedocs.io/en/stable/), but for some reason the generated TIFF file was invalid. I then tried the same conversion using [OpenCV](https://pypi.org/project/opencv-python/), and it worked!
From there, you still need to ensure both softwares use the same scales and coordinates, but once it's done, RoadRunner then has all the [tools](https://www.youtube.com/watch?v=VmoibGgaWJU) to align our roads with the geometry.

![landscape_ue.png]({{site.baseurl}}/images/landscape_ue.png)

![landscape_rr.png]({{site.baseurl}}/images/landscape_rr.png)

Even if you can't perfectly align roads to the landscape from RoadRunner, you can still import them into Unreal, and then [sculpt](https://docs.unrealengine.com/en-US/BuildingWorlds/Landscape/Editing/SculptMode/index.html) the existing landscape to nicely fit along roads.

Of course all of this is quite cumbersome, but we haven't really studied the problem much. We're pretty confident that in the near future, new tools and features will appear, making this process much easier (like RoadRunner's [Scene Builder](https://www.mathworks.com/products/roadrunner-scene-builder.html)).

Credits to Estelle De Baere, [Lucie Lévêque](https://lulvk.github.io/) and Jean-Charles Bornard for making the scene discussed in this post. None of them had any experience in 3D or scene building, making their work even more incredible.

[Marketplace]: https://www.unrealengine.com/marketplace/en-US/store
[Free For The Month]: https://www.unrealengine.com/marketplace/en-US/assets?count=20&sortBy=effectiveDate&sortDir=DESC&start=0&tag=4910
[France Fields]: https://www.unrealengine.com/marketplace/en-US/product/32a96e6b005344b49d93d888f2e0ec59
