---
layout: post
title: Building apps & games for Xbox One using UWP - Build once and target many
date: '2016-11-13 11:43:04'
tags:
- events
- futuredecoded
- monogame
- tutorials-resources
- unity-3d-tutorials
- unity3d
- uwp
- windows-10
---

 

[![image](/Images/wordpress/2016/11/image_thumb.png "image")](/Images/wordpress/2016/11/image.png)

 

For my sins, I was asked back to [FutureDecoded](http://futuredecoded.com/) again this year to give a talk on the Microsoft UWP platform, specifically about bringing games to the XboxOne using UWP.  By all accounts the session went well (especially as there was standing room only by the time the talk started). With it being just two days in the London ExCeL exhibition center, not everyone who wanted to make it could, in fact even some people were contacting me on the day saying they were in other sessions at that time but wanted more info.

So for everyone who could not make it on the day or missed the session (or for those wanting a recap), I have recorded the session at home and published it on my â[Darkside of MonoGame](http://bit.ly/darksideofmonogame)â Youtube channel. (I just have to hope my [MonoGame](http://www.monogame.rocks/) friends will forgive me for featuring Unity on there for a bit ![Open-mouthed smile](/Images/wordpress/2016/11/wlEmoticon-openmouthedsmile.png)

<iframe loading="lazy" title="Building apps &amp; games for Xbox One using UWP - Build once and target many - FutureDecoded2016" width="660" height="371" src="https://www.youtube.com/embed/AAMToCwPy8s?feature=oembed" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**You might also ask âWhy all the Fuss?â.** Well the answer is simple, Microsoft just opened up the XboxOne to UWP developers, allowing any retail XboxOne to become a development machine and test / deploy and publish UWP projects to the XboxOne Store.  It is like Christmas has come again for those of us who remember the Xbox Live Indie Game platform and the thrill of writing your own games and running them on your home Xbox.

* * *

# Just what is UWP? (The Universal Windows Platform)

[![image](/Images/wordpress/2016/11/image_thumb-1.png "image")](/Images/wordpress/2016/11/image-1.png)

I have posted a few times about the UWP platform, but to recap, UWP is Microsoftâs latest endeavor to make it even easier for developers to be able to publish on Windows platforms. So much so, that now you only need one project to be able to deploy on to all of their Windows 10 platforms, this includes:

- Windows 10 desktop
- Windows 10 Mobile
- Xbox
- (supported) IoT devices
- Surface Hub
- HoloLens

Plus, any other devices that Microsoft decides to roll out on to from now on.

It pretty much sounds like a multi-platform dream, and it certainly is.  But how does UWP handle all the different variations on its platform? Each device is different and has its own unique characteristics. The answer in this case is âExtensionsâ:

[![image](/Images/wordpress/2016/11/image_thumb-2.png "image")](/Images/wordpress/2016/11/image-2.png)

As you might expect, Windows 10 has a single âcoreâ which runs on all devices, in exactly the same way.  Then for those little extraâs, the UWP platform provides an âExtensionâ component that is specific to each platform.  However, these extensions are also expressed on all the other platforms, so your code does not break and you write the same code as if you were writing for them all.  Where a device does not support a certain feature (say the Holographic API on an Xbox), then the code simply does nothing, it does not error, it does not crash, your code still works but nothing actually happens. For those platforms with that feature, lights start shining, the bells ring and the choir sings out with joyful praise.

Also as part of this âExtensionâ framework, Microsoft gives you the ability to test if a feature is available or not, allowing you to write different code depending on whether the feature is active, like if you want to use a devices accelerometer if it has one, or use a virtual joystick on a desktop with a touch screen, or fall back to keyboard if hat is not available.  Sure, there is a bit of thought to go in to building for âAnyâ device but that is the trade-off for building one solution.

* * *

# But what about the Games?

[![image](/Images/wordpress/2016/11/image_thumb-3.png "image")](/Images/wordpress/2016/11/image-3.png)

When we start looking at building games under UWP, there is a lot of support (that is constantly growing) from third parties. As you can see most of the major engines and frameworks already support the Universal platform out of the box, making it even easier to publish your game as a UWP app.

Still not see any engine or feature you like, then there is always the ultimate fallback:

[![image](/Images/wordpress/2016/11/image_thumb-4.png "image")](/Images/wordpress/2016/11/image-4.png)

Under the hood, UWP Games are just a DirectX surface and you can write games using native DirectX in either C# or C++, there are even Visual Studio Templates âout of the boxâ for UWP as well.

* * *

# Getting started with UWP on Xbox

[![image](/Images/wordpress/2016/11/image_thumb-5.png "image")](/Images/wordpress/2016/11/image-5.png)

Now that UWP apps can be deployed / tested and run by anyone with a Retail Xbox, we can go wild and try out our own games to see how they run on the big screen.  Once you lick all the bugs and get it just right, you can publish that game âas isâ to the Xbox Store. Well, once you have your project accepted by the [ID@Xbox](http://xbox.com/id) team (which is even easier for UWP developers now)

So long as you have a Windows 10 PC and a retail Xbox, your good to go as everything else is free, the tools, the software, even the ability to switch your retail XboxOne over to a UWP dev kit. All from the comfort of your own home (or hotel room with free wifi)

> There is one other caveat, that you need to also have a Windows Store developer account.  This normally costs about Â£19 for an individual, a little more for a company account.  You can either get this yourself, or when you are accepted by ID, you will get this account plus a load of other software completely FREE. Up to you.
> 
> P.S. If you have an MSDN account, you also get a code for FREE, check your benefits.

* * *

# Setting up your development environment

[![image](/Images/wordpress/2016/11/image_thumb-6.png "image")](/Images/wordpress/2016/11/image-6.png)

Once you have everything ready, getting started could not be simpler and there are only a few short steps. As the slide above shows, you can get up and running with your first project deployed in just 5 Minutes. (if your using Unity, it might take a little longer ![Smile with tongue out](/Images/wordpress/2016/11/wlEmoticon-smilewithtongueout.png))

In short, what you need to do is:

| 

1:  Install the âDev Mode Activationâ app on to your Xbox from the Xbox Store

 | [![image](/Images/wordpress/2016/11/image_thumb-7.png "image")](/Images/wordpress/2016/11/image-7.png) |
| [![image](/Images/wordpress/2016/11/image_thumb-8.png "image")](/Images/wordpress/2016/11/image-8.png) | 

2: Launch the âDev Mode Activationâ app. You will be presented with a code and a URL. Navigate to the URL on your PC, sign in with your Windows Account (same one used with your Xbox Live Gamertag) and enter the code to register the Xbox to your Microsoft Account

 |
| 

3: Once complete, your Xbox will automatically refresh and then ask you to restart.

This will now boot your Xbox in to UWP developer mode with a completely separate sandbox inside your Xbox.

Your Retail settings / apps are still safe on your Xbox, you just ca not access them from developer mode.  You can return to Retail mode at any time.

 | [![image](/Images/wordpress/2016/11/image_thumb-9.png "image")](/Images/wordpress/2016/11/image-9.png) |
| [![image](/Images/wordpress/2016/11/image_thumb-10.png "image")](/Images/wordpress/2016/11/image-10.png) | 

4: Once you have signed in to your Xbox using your Microsoft account, you can launch the Developer Portal app on the Xbox.  
This shows you all the apps / games installed plus a ton of other developer details.

Take note of the Tools IP in case Visual Studio does not automatically detect it.

 |
| 

5: The first time you connect to your Xbox from Visual Studio (selecting the deployment as remote and selecting the Xbox, as shown here) you will be asked for a code to pair the Xbox.

You get this code from the Developer Portal on the Xbox in the âPair with Visual Studioâ section.

Visual Studio and the Xbox must be signed in using the same Microsoft account you activated with.

 | [![image](/Images/wordpress/2016/11/image_thumb-11.png "image")](/Images/wordpress/2016/11/image-11.png) |
| [![image](/Images/wordpress/2016/11/image_thumb-12.png "image")](/Images/wordpress/2016/11/image-12.png) | 

6: Done.  You should now be able to deploy and run games from Visual Studio on your Xbox.

You can also see debugging information from your Xbox (providing your local network supports it) while the game is running.

Just make sure you Run in âReleaseâ or âMasterâ mode when looking at performance issues as the debugger has an impact.

 |

And that is it. You are up and running.  The security of the setup ensures that you (and only you) can connect to your Xbox in dev mode and deploy apps, so long as you use the same Microsoft account for everything.  You can still sign in other gamers, using their GamerTags for local multi-player (although you ca not grant gamerscore ![Open-mouthed smile](/Images/wordpress/2016/11/wlEmoticon-openmouthedsmile.png)).   If you also are a member of ID and have access to to the Live SDK and services, you can also test networked multi-player and all the other Live services.

* * *

# Checking out the demos

For the demoâs, you are going to need to watch the video but here are some handy links to the start of each demo:

| [![image](/Images/wordpress/2016/11/image-13.png "image")](https://youtu.be/AAMToCwPy8s?t=13m4s) | [![image](/Images/wordpress/2016/11/image-14.png "image")](https://youtu.be/AAMToCwPy8s?t=20m8s) |

_\*Click on images to view the demos_

 

* * *

# What is Next?

[![image](/Images/wordpress/2016/11/image_thumb-13.png "image")](/Images/wordpress/2016/11/image-15.png)

 

Right, so you have your project ready, plans are afoot and you know what you either want to build or have a tech-demo (or even a full project) ready.  To get ready to be published on the Xbox and Windows Store (for games) you need to be registered with the awesome [ID@Xbox](http://xbox.com/id) program. in the past some developers have been a bit disillusioned with the responses to the program **but Times have changed**. The team has evolved (especially with UWP deploy now coming to light) and it is now even more streamlined to get access to the program.

Once registered and signed up, the ID team are fully behind you, giving you:

- Free software and a Windows Store account
- Access to all major gaming events
- Support through the MS Game Developer network
- Enablement to Xbox Live for access to achievements, networking, leader boards and much more.

My recommendation (especially if you have a mobile game already or the beginnings of a desktop app) is to apply just for Windows 10 first, get your project out there in the hands of players and then either publish it as a UWP to Xbox or then also apply for the Xbox tier to build a native game (although check the next section for more detail on that).  Windows 10 has much easier access but has all the same rewards for all ID developers, it also has fewer requirements and certifications to get published (you ca not ship a game that randomly crashes for instance!).

The key here is that you are getting your game out as early as possible, getting it in to the hands of players and gaining presence.  I state this in the video but you must be prepared for the amount of footwork you need to put in to promoting your game with the general public.  ID will be behind you every step of the way to take your content further (many ID games are now even getting in front of Major Nelson these days, thanks to ID). I will stress though, expect a lot of work, ID wo not do it for you and you need to be ready to produce high quality videos, marketing material and make yourself available. At least 80% of the effort in your game will come from the last 20% (as they say).

> **If you want your game to be successful, you need to be out there building presence and touting your game! Only you can promote your game the best way. (But ID will help with guidance and weight)**

 

* * *

# Key Differences between UWP & Native

[![image](/Images/wordpress/2016/11/image_thumb-14.png "image")](/Images/wordpress/2016/11/image-16.png)

To round this session up and to allay some of the concerns and comments I have either heard or been asked about UWP on Xbox, I will walk through some of the key differences between publishing UWP on Xbox and going native.

## <u>UWP projects</u>

in short, UWP is simply easier. It is a friendlier platform and the key benefit is that the single project you build, is also directly shippable on all of Microsoftâs other Windows 10 platforms.

[![Future_Decoded_Banner](/Images/wordpress/2016/11/Future_Decoded_Banner_thumb.png "Future\_Decoded\_Banner")](/Images/wordpress/2016/11/Future_Decoded_Banner.png)

While at [FutureDecoded](https://futuredecoded.microsoft.com/), the [VISR-VR](http://www.visr-vr.com/blog/futue-decoded-2016/) team showcased an awesome VR project called **Botanika**  aimed at helping children and adults who struggle to cope with the effects of Autism.  (it is also a fun game for anyone btw ![Open-mouthed smile](/Images/wordpress/2016/11/wlEmoticon-openmouthedsmile.png)).  This game was written in Unity, running as a UWP using the Vive VR setup.  To make it even more amazing, the lead developer spent 10 minutes converting the project over the HoloLens (the night before the event no less) and had it running perfectly. Granted it was not the full scope of the project but all the key elements were there, all now using HoloLensâs gestures to control the game instead of the Vive Controllers.

> **Getting Botanika up and running in about 10 minutes on a HoloLens in Unity was an awesome effort Louis!**

When publishing UWP games to the Xbox, there are slightly fewer resources to native games (about 70% of resources are available) but there are also fewer certification requirements, meaning less headaches trying to figure out why a controller keeps getting disconnected.  As the demoâs show, there is a **LOT** you can get done with that 70% (remembering, it is 70% of a very powerful beast, do not be fooled in to thinking it is not much)

## <u>Native development</u>

If you get invited in to the Xbox Native group, which is a tougher crowd and you need your project to shine, you will be given 2 developer enabled Xboxâs and a couple of years to get your project âfinishedâ.

> A great number of developers are also taking up Microsoftâs offer of getting a â **Preview** â version of their title out even earlier to consumers. Something not offered on other platforms.  Yes, it is more work but it means you get to build more presence and get feedback direct from your players while building.

I cannot stress more, just how much extra effort is needed to get a native Xbox game out, apart from the stricter certification requirements (which with some engines, you can run into trouble if it is the engine causing the issue). Most certification builds take months of testing and validation to get ready.  There are also stricter controls placed on console projects from a ratings perspective (and in some cases, quite costly), IARC has not reached Xbox native yet (like with the Windows Store) but hopefully it will be coming soon.

There is also the fact that in a lot of cases, you will need C++ skills (or contract them) to work on the interconnectedness of things, or if you need the utmost performance on the platform.  Although, I have known a fair few devs who have not had to go down this route but there are always compromises.

* * *

# Summing up

[![image](/Images/wordpress/2016/11/image_thumb-15.png "image")](/Images/wordpress/2016/11/image-17.png)

The world just got that little bit bigger and if you are already working on a project for Windows 10, the reach of your title has now opened up even more and for very little effort.  If you want to then use the success of your game to then build the âEvolvedâ edition and build that native later, then you already have a foot in the door and it also becomes easier (although harder from an effort perspective ![Surprised smile](/Images/wordpress/2016/11/wlEmoticon-surprisedsmile.png))

So, if you want to build one game and ship it on to several platforms at once, then UWP is the answer (yes I know mobile share is small at present but MS is still committed to it ![Open-mouthed smile](/Images/wordpress/2016/11/wlEmoticon-openmouthedsmile.png)).  Youâll still be able to take it to other platforms later as most engines and frameworks also support more than UWP, so if you architect your project right, the world is your oyster.

> **If you are making games these days, NEVER restrict or limit your dream to one platform. Go BIG, go WILD and get out there!**

