Requirements:

-Cemu

-Cemuhook

-Wii U

-Physical or Digital copy of BOTW for Wii U

-Python 3.8.10 (3.9 doesn't work)
	
# Basic Cemu Setup
	
-Download [Cemu](http://cemu.info/index.html#download). Unzip, then download Cemuhook (https://cemuhook.sshnuke.net/) and extract it into Cemu's folder.
	
-Run Cemu. Don't fill in the custom mlc or games folder, just hit "Download latest community graphics packs". Press "Next", then "Close". If Cemuhook was installed right, there will be a bar on the bottom of the window asking you to download shared fonts. Click download.
	
# Controller Setup
	
-For this guide, I'll be using a Pro Controller, since it works the best, with the simplest setup. PS4 controllers can be used with DS4Windows to get full motion and button control support. Dual JoyCons should work mostly the same as the Pro Controller, with some slight differences. Other controllers will generally work, but usually don't support motion control.
	
-Connect your controller to your PC with a wire or Bluetooth. On Switch controllers, this is done by holding down the sync buttons until the lights come on, then pairing with the device in your Bluetooth settings.
	
-Go to "Options > Inut settings". Set the emulated controller to the Wii U GamePad. For Pro Controllers (and probably dual JoyCons), set the controller API to SDL. Otherwise, set it to XInput. Select the Pro Controller in the list (SDL), or the first one that appears (Xinput). Now click on the box for the A button, and press the corresponding buttons on your controllers to bind buttons. Click in the "<profile name>" box, enter a controller profile name, then hit Save and close the input configuration.
	
-If you have Cemuhook installed, motion controls on Pro Controllers (and probably dual JoyCons) should just work out of the box. For DS4Windows or BetterJoy, hover over "Options > GamePad motion source > DSU1", then set it to "By Slot".
	
# Vanilla BOTW Setup

-Depending on if you have a physical or digital copy of BOTW, this install process will be a bit different. If you have a physical copy, you'll need to follow the regular Cemu dumping guide (https://cemu.cfw.guide/dumping-games), then install them as seen in the game installation guide (https://cemu.cfw.guide/installing-games#games-updates-and-dlc). If you have a digital copy, you can fast-track the process a little.
	
-For digital copy owners, follow Cemu's online play guide (https://cemu.cfw.guide/online-play) to get Cemu working on Nintendo's official servers. Once this is done, go to "Tools > Download Manager". Hit the connect button next to your account. After a little bit, you should see a list of every Wii U game you own on that account. You can download any of them by right clicking and pressing download.
	
-Note: Even if you don't own BOTW on your Wii U, you can still dump your online files and buy it using the eShop directly in Cemu. You can also buy any other Wii U game right in Cemu. (Although until Cemu supports DLC downloads, you'll still need to install it on your Wii U to dump and obtain the DLC)
	
-At the time of writing (July 22 2021), Cemu is unable to download DLC. For this, refer back to the game dumping guide (https://cemu.cfw.guide/dumping-games). Once dumped, you can install the DLC by following the steps in the title installation guide (https://cemu.cfw.guide/installing-games#games-updates-and-dlc). If for whatever reason you can't download your digital copy through Cemu, you can just dump it normally (as detailed in the dumping guide).

# Optimization and quick setup for vanilla BOTW
	
-Go into the graphics settings (Options > General settings > Graphics), and tick the "Async shader compile" box. This will dramatically decrease stuttering, especially when first starting the game.
	
-At this stage, double click Breath of the Wild to run it, and just confirm that everything seems to be working. As soon as Link wakes up, save and return to the title screen. Don't worry if performance is bad right now. In the bottom right, it should say "Ver. 1.5.0", and "DLC Ver.3.0".
	
-Now for some quick optimizations. In the graphics packs menu (Options > Graphics packs), there will be 3 dropdown menus, and 2 options labelled "Enhancements" and "Graphics". For each option, you can click on the name to change its settings on the right side of the window, and click the box to enable/disable it. Enable the "Graphics" option, then change the settings in it to your liking. Now, expand the "Mods" dropdown. The most important option here is FPS++. For the most part, there's no good reason to ever turn this off. It gives a massive performance boost, and lets you play the game mostly without issue at up to 60 FPS. The game can be run at higher framerates, but physics issues grow more common the higher you go.
	
-Play for a bit and see how it performs. During the first few minutes of play, there'll be some pop-in and/or lag, which will become less and less common as you play through the game.
	
# BCML Setup

-Create BCML shortcut. Search Python in Windows search, right click and hit Open file location on "IDLE (Python 3.8 64-bit)". Right click and hit open file location on this shortcut, should bring you to "pythonw.exe". Right click the exe and hit "Create Shortcut". Right click the shortcut, hit properties, and add "-m bcml" to the end of the string in the "Target" field. Rename the shortcut to "BCML", then drag it onto the taskbar to pin it.
