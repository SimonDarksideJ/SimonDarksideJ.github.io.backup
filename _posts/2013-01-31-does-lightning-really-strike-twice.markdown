---
layout: post
title: Does lightning really strike twice?
date: '2013-01-31 22:15:56'
tags:
- '68'
- '72'
- lightning
- monogame
- ramblings
- tutorials-resources
- xna
- xna-related
---

![src=]()

It all started one sunny morning when [Michael Hoffman](http://gamedev.tutsplus.com/author/michael-hoffman/) who wrote a shocking article on some fantastic lighting effects all done with XNA, I read this and was immediately impressed just how simple his solution was.

![src=]()

Not long after this a guy down under called [Jose Fajardo](http://advertboy.wordpress.com) was so impressed he went and got the same framework running on Windows 8 /Windows RT using Sharp DX combined with XAML.

Both demos really show the power and ease of building projects using XNA, I was tempted to follow up like Jose following Michael’s article but was busy with other projects,&nbsp; With Jose’s article I felt freshly invigorated in light of my XNA futures series to show both how easy it is to use this solution but to also to go further, e.g. BEYOND!!! ![Open-mouthed smile](/Images/wordpress/2013/01/wlEmoticon-openmouthedsmile2.png)

&nbsp;

<font size="4">Source for the series can be found </font>[<font size="4">here on codeplex</font>](http://lightningdemo.codeplex.com/)<font size="4"> as well as the code drop for </font>[<font size="4">this stage here</font>](http://lightningdemo.codeplex.com/releases/view/101308)

* * *

# Going portable with MonoGame

[![ src=]()](http://monogame.net/)

As you would expect, porting Michaels solution over to [MonoGame](http://monogame.net/) is very simple since MonoGame is just a direct replacement for XNA at present.&nbsp; not all plain sailing as especially with the Windows version, not all graphical capabilities are available, usually because they did not make sense (a bridge too far) or where further work is still required either in SharpDX (the graphical underlay of MonoGame) or the current implementation.

First off you had better swing over to the new MonoGame website and grab the latest MonoGame installer, they updated it in January and added a host of new features and supported platforms.

[![image](/Images/wordpress/2013/01/image.png "image")](http://monogame.net)

(Pretty Ai not it ![Open-mouthed smile](/Images/wordpress/2013/01/wlEmoticon-openmouthedsmile2.png),I especially like the rotating images of popular MonoGame projects)

With the new version installed you will be presented with the new project templates when starting a new project:

[![image](/Images/wordpress/2013/01/image_thumb.png "image")](/Images/wordpress/2013/01/image1.png)

As expected the Android and Linux builds are still there, there is a new player to the party with the Ouya (be sure to check on the requirements as Ouya deployment will also need a Xamarin Android license to deploy), two features to existing users that will catch your eye is that the Windows Project has now been renamed to OpenGL (unknown as yet whether there will be a DX variant or if this is a permanent shift?), the other thing of note is that there has been significant work on the Content building side (also now supported in VS 2012 but more on that later).&nbsp; After much criticism the content project has been simplified and updated to support more traditional content plus the addition of content building for the new platforms.

After you have started your new Windows project just add an additional project for the Content to the solution and you should have a clean setup as below:

[![image](/Images/wordpress/2013/01/image_thumb1.png "image")](/Images/wordpress/2013/01/image2.png)

> \*\*Note, at the time of writing there is an issue in the new “Windows OpenGL” project template which incorrectly references the SDL.DLL, The MonoGame team are aware of the issue and no doubt it will be resolved shortly.&nbsp; For now you can simply remove the SD.dll.

As with any simple conversion project like this with MonoGame, getting started is easy, just copy over all the class files to your new project (except for the Game class, always best to port that manually,, just in case), then copy over all the content from the original project in to the Content Project solution and you should have something now looking like this:

[![image](/Images/wordpress/2013/01/image_thumb2.png "image")](/Images/wordpress/2013/01/image3.png)

(\*Note do not forget to update the namespace in the copied files)

All that is left is to copy over all the Game Class code:

> ![align=](http://www.dotnetscraps.com/samples/bullets/033.gif)&nbsp;&nbsp;&nbsp; Class properties  
> ![align=](http://www.dotnetscraps.com/samples/bullets/033.gif)&nbsp;&nbsp;&nbsp; Constructor code  
> ![align=](http://www.dotnetscraps.com/samples/bullets/033.gif)&nbsp;&nbsp;&nbsp; Content loading in “LoadContent”  
> ![align=](http://www.dotnetscraps.com/samples/bullets/033.gif)&nbsp;&nbsp;&nbsp; Game Update method  
> ![align=](http://www.dotnetscraps.com/samples/bullets/033.gif)&nbsp;&nbsp;&nbsp; Game Draw method  
> ![align=](http://www.dotnetscraps.com/samples/bullets/033.gif)&nbsp;&nbsp;&nbsp; And any additional helper classes / functions

All in all it took me all of 3 minutes to get it copied across to the new solution, all that is left is to build and link the content files and your ready to go, well almost.

* * *

# Final Steps

To finish things off you just need to link the content to your project and sort out any incompatibilities, likely both are only minor tweaks.

For Content I prefer to just “Link” the compiled filed from the content project but of course you can just copy the content files over to the build directory or setup a Build time task to copy them across, all methods have been mentioned before when I went through MonoGame, if you need to [look back check here](http://darkgenesis.zenithmoon.com/xna-to-monogame-and-beyond/)

For now just right click on the folder named “Content” and select “Add –\> Existing Item”, browse to the build folder for the content project (note the Builder Project not the content project itself) but instead of just clicking on “Add”, hit the down arrow next to the button and select “Link Files”.

Once you have linked the files make sure you also

> ![align=](http://www.dotnetscraps.com/samples/bullets/033.gif)&nbsp;&nbsp;&nbsp; Change the “Build Action” of the .XNB files to “Content”  
> ![align=](http://www.dotnetscraps.com/samples/bullets/033.gif)&nbsp;&nbsp;&nbsp; And the “Copy to Output Directory” option to “Copy if newer”

[![image](/Images/wordpress/2013/02/image_thumb.png "image")](/Images/wordpress/2013/02/image.png)

> TIPS
> 
> If you cannot see the build files ensure you have:
> 
> > ![align=](http://www.dotnetscraps.com/samples/bullets/024.gif)&nbsp;&nbsp;&nbsp; Clicked on the Content or Content builder project and selected the correct&nbsp; “Solution Configuration”&nbsp; in the&nbsp; drop down, in this case “Windows”  
> > ![align=](http://www.dotnetscraps.com/samples/bullets/024.gif)&nbsp;&nbsp;&nbsp; Build the content project builder project by right clicking on it and selection “Build”  
> > ![align=](http://www.dotnetscraps.com/samples/bullets/024.gif)&nbsp;&nbsp;&nbsp; Selected “All Files” in the file browser, else you will see nothing ![Open-mouthed smile](/Images/wordpress/2013/01/wlEmoticon-openmouthedsmile2.png)

As for fixes in this case I found only one in the Windows project which was to do with the RenderTargets used for the Lightning Text renderer use a mode that is not implemented in MonoGame for Windows (Strangely enough the mode is supported in Windows 8, odd, but more on that later), to fix this just change the following lines from:

    lastFrame = new RenderTarget2D(GraphicsDevice, screenSize.X, screenSize.Y, false, SurfaceFormat.HdrBlendable, DepthFormat.None); currentFrame = new RenderTarget2D(GraphicsDevice, screenSize.X, screenSize.Y, false, SurfaceFormat.HdrBlendable, DepthFormat.None);

And replace it with:

    lastFrame = new RenderTarget2D(GraphicsDevice, screenSize.X, screenSize.Y, false, SurfaceFormat.Color, DepthFormat.None); currentFrame = new RenderTarget2D(GraphicsDevice, screenSize.X, screenSize.Y, false, SurfaceFormat.Color, DepthFormat.None);

Al that has changed is the “SurfaceFormat” used to prepare the render target for use from “HdrRenderable” (a High def format) with “Color” (A more basic variant)

Now fire it up and you will get the same experience as you saw in the previous demos but now running smoothly in MonoGame:

[![image](/Images/wordpress/2013/02/image_thumb1.png "image")](/Images/wordpress/2013/02/image1.png)

* * *

# To Be Continued

So that is the first stage of many, sure it is working in MonoGame but we can do better than that, first lets add a bit more and then go fully Multi-Platform

Laters…

&nbsp;

<font size="4">Source for the series can be found </font>[<font size="4">here on codeplex</font>](http://lightningdemo.codeplex.com/)<font size="4"> as well as the code drop for </font>[<font size="4">this stage here</font>](http://lightningdemo.codeplex.com/releases/view/101308)

[![kick it on DotNetKicks.com](http://www.dotnetkicks.com/Services/Images/KickItImageGenerator.ashx?url=http://darkgenesis.zenithmoon.com/does-lightning-really-strike-twice/&bgcolor=6600FF)](http://www.dotnetkicks.com/kick/?url=http://darkgenesis.zenithmoon.com/does-lightning-really-strike-twice/) [![Shout it](http://dotnetshoutout.com/image.axd?url=http://darkgenesis.zenithmoon.com/does-lightning-really-strike-twice/)](http://dotnetshoutout.com/Submit?url=http://darkgenesis.zenithmoon.com/does-lightning-really-strike-twice/) <script type="text/javascript">var dzone_url = 'http://darkgenesis.zenithmoon.com/does-lightning-really-strike-twice/';</script>  
<script type="text/javascript">var dzone_title = 'Does lightning really strike twice?';</script>  
<script type="text/javascript">var dzone_blurb = 'Does lightning really strike twice?';</script>  
<script type="text/javascript">var dzone_style = '2';</script>  
<script language="javascript" src="http://widgets.dzone.com/links/widgets/zoneit.js"></script><script type="text/javascript">var addthis_pub="runxc1";</script>[![Bookmark and Share](http://s7.addthis.com/static/btn/lg-share-en.gif)](http://www.addthis.com/bookmark.php?v=20) &nbsp; <script type="text/javascript" src="http://s7.addthis.com/js/200/addthis_widget.js"></script> [CodeProject](http://www.codeproject.com/script/Articles/BlogFeedList.aspx?amid=9502591) 
