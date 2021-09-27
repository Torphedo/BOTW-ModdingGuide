Requirements:

-64-bit PC

-[Cemu](http://cemu.info/index.html#download)

-[Cemuhook](https://cemuhook.sshnuke.net/#Downloads)

-Wii U console

-Physical or Digital copy of BOTW for Wii U

-[Python 3.8.10](https://www.python.org/ftp/python/3.8.10/python-3.8.10-amd64.exe) or [3.7.9](https://www.python.org/ftp/python/3.7.9/python-3.7.9-amd64.exe) (3.9 doesn't work)
	
# Basic Cemu Setup

-Run [this](https://github.com/Torphedo/BOTW-ModdingGuide/releases/download/2.0/AIO-Installer.bat) batch script, and select option 1. This will automatically install Cemu and Cemuhook, plus BCML and its requirements for later.
	
# Controller Setup
	
-For this guide, I'll be using a Pro Controller, since it works the best, with the simplest setup. PS4 controllers can be used with [DS4Windows](https://ryochan7.github.io/ds4windows-site/) to get full motion and button control support. Dual JoyCons should work mostly the same as the Pro Controller, with some slight differences. Other controllers will generally work, but usually don't support motion control.
	
-Connect your controller to your PC with a wire or Bluetooth. On Switch controllers, this is done by holding down the sync buttons until the lights come on, then pairing with the controller in your Bluetooth settings.
	
-Go to `Options > Input settings`. Set the emulated controller to the Wii U GamePad. For Pro Controllers (and probably dual JoyCons), set the controller API to SDL. Otherwise, set it to XInput. Select the Pro Controller in the list (SDL), or the first one that appears (Xinput). Now click on the box for the A button, and press the corresponding buttons on your controllers to bind buttons. Click in the `<profile name>` box, enter a controller profile name, then hit Save and close the input configuration.
	
-Motion controls on Pro Controllers (and probably dual JoyCons) should just work out of the box. For [DS4Windows](https://ryochan7.github.io/ds4windows-site/) or [BetterJoy](https://github.com/Davidobot/BetterJoy), hover over `Options > GamePad motion source > DSU1`, then set it to `By Slot`.
Note: You may need to turn on the motion server in BetterJoy/DS4Windows to enable motion control.
	
# Vanilla BOTW Setup

-Depending on if you have a physical or digital copy of BOTW, this install process will be a bit different. If you have a physical copy, you'll need to follow the regular [Cemu dumping guide](https://cemu.cfw.guide/dumping-games), then install them as seen in the [game installation guide](https://cemu.cfw.guide/installing-games#games-updates-and-dlc).

-If you bought BOTW on the eShop, follow Cemu's [online play guide](https://cemu.cfw.guide/online-play) to get Cemu working on Nintendo's official servers. Once this is done, go to `Tools > Download Manager`. Hit the connect button next to your account. After a little bit, you should see a list of every Wii U game you own on that account. You can download any of them by right clicking and pressing download.
	
-At the time of writing (July 22 2021), Cemu is unable to download DLC. Until it's supported, you'll have to dump it from your console. For this, refer back to the [game dumping guide](https://cemu.cfw.guide/dumping-games). Once dumped, you can install the DLC by following the steps in the [title installation guide](https://cemu.cfw.guide/installing-games#games-updates-and-dlc). If for whatever reason you can't download your digital copy through Cemu, you can just follow the [dumping guide](https://cemu.cfw.guide/dumping-games) (as you would a physical copy).

-Note: Even if you don't own BOTW on your Wii U, you can still dump your online files and buy it using the eShop directly in Cemu. You can also buy any other Wii U game right in Cemu. (Although until Cemu supports DLC downloads, you'll still need to install it on your Wii U to dump and obtain the DLC)

# Optimization and quick setup for vanilla BOTW
	
-Go into the graphics settings `(Options > General settings > Graphics)`, and tick the `Async shader compile` box. This will dramatically decrease stuttering, especially when first starting the game.
	
-At this point, double click Breath of the Wild to run it. As soon as Link wakes up, save and return to the title screen (Performance will be bad at this stage of setup). In the bottom right, it should say `Ver. 1.5.0`, and `DLC Ver. 3.0`. If it does, that means that all of the game files have been correctly installed!
	
-Now for some quick optimizations. In the graphics packs menu `(Options > Graphics packs)`, there will be 3 dropdown menus, and 2 options labelled `Enhancements` and `Graphics`. For each option, you can click on the name to change its settings on the right side of the window, and click the box to enable/disable it. Enable the "Graphics" option, then change the settings in it to your liking. Now, expand the "Mods" dropdown. The most important option here is `FPS++`. There's essentially no need to ever turn this off. It gives a massive performance boost, and lets you play the game mostly without issue at up to 60 FPS. The game can be run at higher framerates, but physics issues grow more common the higher you go.
	
-Play for a bit, and see how it performs. During the first few minutes, there'll be some pop-in and/or lag, which will become less and less common as you play through the game.
	
# [BCML](https://github.com/NiceneNerd/BCML) Setup

-If you chose not to use the [batch script](https://github.com/Torphedo/BOTW-ModdingGuide/releases/download/2.0/AIO-Installer.bat) in the beginning of the guide or already had Cemu installed, run it now and select option 2. For manual install, see [this](https://github.com/Torphedo/BOTW-ModdingGuide/wiki/Manual-BCML-Install) guide. Once installed, you can run BCML with the shortcut generated by the script, or by running `bcml` in cmd.

-Before I go over the final steps in BCML setup, it's a good time to cover some common misconceptions about BCML. BCML isn't actually loading the mods into the game, it's creating a pack of mods then sending them to Cemu to load. This means that you can close BCML as long as it's not in the middle of remerging or changing your mod list in any way. In order to merge multiple mods, it uses the game files you got from your console and edits copies of them as dictated by a mod. **This does NOT edit your original game files, you can uninstall mods whenever you want.**

-First, BCML needs your Cemu path (the folder where Cemu.exe is located). Next, BCML needs the filepaths for BOTW's base game, update, and DLC folders. The easiest way to find these is to right click BOTW in Cemu, then click `Game directory`, `Update directory`, or `DLC directory`. For the base game, you have to go up 1 folder, then into the `content\` folder. Paste this filepath into BCML. For the update and DLC, it'll send you to `101c9400\` instead of `101c9400\code\`. In the case of the update, just go into the `content\` folder. For the DLC, go into `content\0010\` instead of `content\`. At this point, your filepaths should look something like this:

![](https://user-images.githubusercontent.com/73564623/126426446-d7b9b54f-cf95-4721-b9e1-9bb56c7d9554.png)

Now just set the language to whatever language your game will be in, and BCML's setup should be complete! When you boot the game, go into `Options > Graphics packs` and enable the pack named `BCML` (in the `Mods` dropdown). If you don't enable this, none of the mods installed in BCML will take effect.
Note: If you don't see a BCML graphics pack, check to see if the launch game button (the triforce) works. If it does, your Cemu path is correct. Now try closing Cemu and rebooting BCML, and pressing the Remerge button (looks like a reload button). This *should* fix it.

# Getting to know BCML

Now that BCML is set up, you can install some mods. All mods for BOTW are posted on [Gamebanana](https://gamebanana.com/games/5866). Any mods in the `.bnp`
(or `.zip`) format will have an option for `1-Click Install`. When you click it, it'll download the mod right into BCML and then bring up a prompt to install it. The only problem is that there's no download progress bar, and some mods can be massive. There's also an integrated Gamebanana tab in BCML, although it can be slow. Personally, I'd recommend using the download button and saving the mod file. Install the mod file by pressing the `+` in the bottom right of BCML, then press `Browse` and select the mod you downloaded. Assuming everything is set up correctly, it should be applied the next time you boot up the game. If you need any more info, refer to the BCML help.

If you're here from the Second Wind discord, the 2 BNP files you want can be found [here](https://github.com/CEObrainz/Second-Wind/releases). Since it's a big mod, things can break pretty easily. Usually, other mods should go above SW in the mod list.
