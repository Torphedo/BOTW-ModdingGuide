Requirements:

-[Cemu](http://cemu.info/index.html#download)

-[Cemuhook](https://cemuhook.sshnuke.net/)

-Wii U

-Physical or Digital copy of BOTW for Wii U

-[Python 3.8.10](https://www.python.org/ftp/python/3.8.10/python-3.8.10-amd64.exe) (3.9 doesn't work)
	
# Basic Cemu Setup
	
-Download [Cemu](http://cemu.info/index.html#download). Unzip, then download [Cemuhook](https://cemuhook.sshnuke.net/) and extract it into Cemu's folder.
	
-Run Cemu. Don't fill in the optional filepaths, just press `Download latest community graphics packs`. Press `Next`, then `Close`. If Cemuhook was installed right, there will be a bar on the bottom of the Cemu window asking you to download shared fonts. Click download.
	
# Controller Setup
	
-For this guide, I'll be using a Pro Controller, since it works the best, with the simplest setup. PS4 controllers can be used with [DS4Windows](https://ryochan7.github.io/ds4windows-site/) to get full motion and button control support. Dual JoyCons should work mostly the same as the Pro Controller, with some slight differences. Other controllers will generally work, but usually don't support motion control.
	
-Connect your controller to your PC with a wire or Bluetooth. On Switch controllers, this is done by holding down the sync buttons until the lights come on, then pairing with the controller in your Bluetooth settings.
	
-Go to `Options > Inut settings`. Set the emulated controller to the Wii U GamePad. For Pro Controllers (and probably dual JoyCons), set the controller API to SDL. Otherwise, set it to XInput. Select the Pro Controller in the list (SDL), or the first one that appears (Xinput). Now click on the box for the A button, and press the corresponding buttons on your controllers to bind buttons. Click in the `<profile name>` box, enter a controller profile name, then hit Save and close the input configuration.
	
-If you have Cemuhook installed, motion controls on Pro Controllers (and probably dual JoyCons) should just work out of the box. For [DS4Windows](https://ryochan7.github.io/ds4windows-site/) or [BetterJoy](https://github.com/Davidobot/BetterJoy), hover over `Options > GamePad motion source > DSU1`, then set it to `By Slot`.
Note: You may need to turn on the motion server in BetterJoy/DS4Windows to enable motion control.
	
# Vanilla BOTW Setup

-Depending on if you have a physical or digital copy of BOTW, this install process will be a bit different. If you have a physical copy, you'll need to follow the regular [Cemu dumping guide](https://cemu.cfw.guide/dumping-games), then install them as seen in the [game installation guide](https://cemu.cfw.guide/installing-games#games-updates-and-dlc).

-If you bought BOTW on the eShop, follow Cemu's [online play guide](https://cemu.cfw.guide/online-play) to get Cemu working on Nintendo's official servers. Once this is done, go to `Tools > Download Manager`. Hit the connect button next to your account. After a little bit, you should see a list of every Wii U game you own on that account. You can download any of them by right clicking and pressing download.
	
-At the time of writing (July 22 2021), Cemu is unable to download DLC. Until it's supported, you'll have to dump it from your console. For this, refer back to the [game dumping guide](https://cemu.cfw.guide/dumping-games). Once dumped, you can install the DLC by following the steps in the [title installation guide](https://cemu.cfw.guide/installing-games#games-updates-and-dlc). If for whatever reason you can't download your digital copy through Cemu, you can just dump it normally (as you would a physical copy).

-Note: Even if you don't own BOTW on your Wii U, you can still dump your online files and buy it using the eShop directly in Cemu. You can also buy any other Wii U game right in Cemu. (Although until Cemu supports DLC downloads, you'll still need to install it on your Wii U to dump and obtain the DLC)

# Optimization and quick setup for vanilla BOTW
	
-Go into the graphics settings `(Options > General settings > Graphics)`, and tick the `Async shader compile` box. This will dramatically decrease stuttering, especially when first starting the game.
	
-At this point, double click Breath of the Wild to run it. As soon as Link wakes up, save and return to the title screen (Performance will be bad at this stage of setup). In the bottom right, it should say `Ver. 1.5.0`, and `DLC Ver. 3.0`. If it does, that means that all of the game files have been correctly installed!
	
-Now for some quick optimizations. In the graphics packs menu `(Options > Graphics packs)`, there will be 3 dropdown menus, and 2 options labelled `Enhancements` and `Graphics`. For each option, you can click on the name to change its settings on the right side of the window, and click the box to enable/disable it. Enable the "Graphics" option, then change the settings in it to your liking. Now, expand the "Mods" dropdown. The most important option here is FPS++. Usually, you'll never need to turn this off. It gives a massive performance boost, and lets you play the game mostly without issue at up to 60 FPS. The game can be run at higher framerates, but physics issues grow more common the higher you go.
	
-Play for a bit, and see how it performs. During the first few minutes, there'll be some pop-in and/or lag, which will become less and less common as you play through the game.
	
# [BCML](https://github.com/NiceneNerd/BCML) Setup

-BCML requires Python [3.8.10](https://www.python.org/ftp/python/3.8.10/python-3.8.10-amd64.exe) and the [x64 Visual C++ redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads#section-2). When you open the Python 3.8 installer, there will be a checkbox that says `Add Python to PATH`. You MUST check this box, or else BCML can't be installed. From here, continue as normal, and install the x64 Visual C++ redistributable.

-Open a command prompt anywhere (if you don't know how, just type `cmd` into Windows Search). Run `pip install bcml` (in normal cmd, NOT the python console). You should see a bunch of progress bars, and then a success message.

-Next, we'll create a shortcut for BCML. Search Python in Windows search, then right click and hit `Open file location` on `IDLE (Python 3.8 64-bit)`. Right click the shortcut it opens to, and click `Open file location` again. This should bring you to `pythonw.exe`. Right click the exe and hit `Create Shortcut`. Right click the shortcut you created, hit `Properties`, and add `-m bcml` to the end of the text in the first box. Rename the shortcut to `BCML`, then drag it onto the taskbar to pin it. Now, you can just click on this shortcut to launch BCML.

-Before I go over the final steps in BCML setup, it's a good time to cover some common misconception about BCML. BCML isn't doing the actual loading of mod files, Cemu handles that. BCML merges the mod files of multiple mods, then sends them to Cemu to load. This means that you can close it as long as it's not remerging or changing your mod list in some way. In order to merge multiple mods, it uses the game files you got from your console and edits them as dictated by a mod. **This does NOT edit your original game files, you can uninstall mods whenever you want.**

-
