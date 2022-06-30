This tutorial will describe my preferred workflow for developing mods in BCML.
  

# Basics

  
[BCML](https://github.com/NiceneNerd/BCML) uses the vanilla (unmodded) game files, and merges them with the incomplete files provided by mod developers. The BNP files it produces are 7zip archives at the Ultra compression setting, which always contain an `info.json`, and `content` / `logs` / `patches` folder(s).  
  
The first thing you need to know is how to load a specific edited file using BCML. First, you need to start a new project. The easiest way I've found is to install this [blank mod](https://cdn.discordapp.com/attachments/754471358553129082/888661075753578506/ValidMod.bnp), then build on top of it. Let's say for instance that you want to edit `[update folder]\content\Actor\Pack\Weapon_Sword_024.sbactorpack`. Create these same folders in the BCML mod folder (in this case, a folder in `content` named `Actor`, and one inside that named `Pack`). Then, copy the original file into this folder, so that the folder structure resembles that of the original game. Once you make your edits, save the file and press the `Remerge` button in BCML to test your changes.
  

Types of Logs
-------------

  

### RSTB  

The RSTB, or `ResourceSizeTable.product.srsizetable`, tells the game how many bytes of memory to dedicate to each decompressed asset. If the RSTB value is too low to properly load an asset (eg your model/texture is larger than the vanilla one), it will fail to load (model would be invisible). Unlike the earlier days of modding, you won't have to manually calculate new values and edit the file, since BCML can do all of that for you when building the `rstb.json` log. I'll go over how to build the logs after reviewing the most common types of logs.  
  

### Deepmerge

BotW uses "actorpack" files to store almost all data about any given item, enemy, or object (known collectively as actors). Actorpacks contain information like what animations to play for what actions, what model to use, how much damage to do, what AI to use, etc. In BCML, your changes to actorpacks are stored as a `deepmerge.aamp` log, rather than publishing the entire edited actorpack. This saves space and makes mods break each other less.  
  

### Packs

The `packs.json` log determines what `*.pack` files BCML merges. Unless you're doing lots of manual log tampering, you probably don't need to worry about it.  
  

### ActorInfo

The `actorinfo.yml` log stores changes made to `ActorInfo.product.sbyml`. ActorInfo is checked before actorpacks, usually for things like what number to display on armors, and which particle effects to use.  
  

### Text

Exactly what it sounds like, the `texts.json` log stores changes to the game's texts.  
  

### Other Logs

There are many other logs (~10), but these cover the most common. The next most common logs are probably map, shop, and mainstatic.  
  

Building BNPs (and logs)
------------------------

Copy the filepath where `info.json` is located, then paste it into the `Dev Tools` tab of BCML. Name your mod whatever you want, then hit Create BNP and save it at the same filepath you gave to the BNP builder. Now, because BNPs are just 7z files, you can just open it and extract the logs folder next to the content folder. If you have something that might be entirely replaced by logs (like actorpack edits), I'd recommend deleting content\\ and then extracting both the content and logs folder from the BNP. Now, remerge to push your changes to Cemu, and test them out!  
  

Intermediate
============

Working around BCML  

----------------------

As I got better at modding, I started to encounter more issues with BCML, and had to find workarounds. Mainly, BCML would incorrectly generate a changelog, and I would keep having to manually fix it. I'm not entirely sure how common this experience is, but I figure it's a good idea to teach people how to bypass elements of BCML that give you trouble.  
One of the simplest ways to get around BCML log errors is to build your BNPs using 7zip, unless you need to build changelogs. This method gives you complete control over what logs you want to remake, allowing for an easier workflow.  
  

Modular BNPs!
-------------

This is one of the most useful BCML features to master. Modular BNPs allow you to package a mod with many potential options that might not be universally liked, like in Hyrule Rebalance. There's even a mod based entirely around modular BNPs, Class Maker.  
  
To make an option, first make an `options` folder next to your `logs` folder. Inside the options folder, make another folder with any name. This folder is essentially another BNP packaged within yours (but without an `info.json`) Put whatever optional mod files you want in here, then open the BNP builder. Next to the `Create BNP` button, there's an `Options` button.  
  
The multiple choice tab is the simplest type of option. You can add multiple toggle-able options, each mapped to a folder. Select the folder you made earlier from the dropdown, and enter a name and description for it. Remember to hit Add Option before exiting the menu! After creating the BNP and installing it, it'll pop up with a selection menu.  
  
The Single Select tab is a bit more complex, but still pretty simple. Use this to let the user adjust a value of some sort from preset selections. The options are laid out like a multiple choice test question. The group is like the question, and each option is laid out like an answer would be. Create a group, then make an option like you would in the other tab. Remember to select a group for the option to belong to, and hit `Add Option`. All options are managed by the `info.json`, so that's the only thing you need from the new BNP.  
  
On the user end: when the user selects an option, the files inside the corresponding folder are merged as if they were in the main BNP.
