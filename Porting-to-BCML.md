Many mods for BOTW are very old, and don't work with BCML. Before BCML, most mods were using graphics packs, and before that, directly
replacing original game files. In this guide, I aim to show how to port old mods to the BNP format, so that they can be used in BCML.  
  
# Graphics Pack mods  
  
Installing/Playing Graphics Pack mods:  
If a mod doesn't edit code, and you only want to play it, just hit "Browse" in the installation screen in BCML, then select the zip file,
or the rules.txt (if the mod is unzipped).  
  
# Upgrading to BNP:  
Unzip the mod to its own folder, so that the folder contains a content folder and a rules.txt file. Copy the filepath of this folder. Go
into the "Dev Tools" tab in BCML, and paste the filepath in the "Mod root folder" box. This should automatically fill in the mod's name
and description. (If it doesn't, write a title yourself, the description is optional.) Now press "Create BNP", and choose where to save
the file. From here, just  
  
# Direct file replacement mods  
  
These mods were made to directly replace original game files, and are a slightly more complicated to convert. I'll be using Issuelink's
[Ordon Sword](https://gamebanana.com/skins/157383) mod as an example. First, you need to locate the folder that has a folder named content.
In this case, it's `ordonswordhd.rar\mlc01.rar\mlc01\usr\title\00050000\101C9400\` The filepath is usually pretty similar to this. I suggest
7zip so you don't need to unpack any of the `.rar` files. Extract the folder that has content in it, then copy the filepath to the extracted
folder. Click on the "Dev Tools" tab in BCML, then paste the filepath in the "Mod root folder" box, and write a name and description. Now
click "Create BNP", choose a location to save it, and install the BNP file. The mod should now load. Some mods won't port quite this easily,
like [Issuelink's Visual Champion Tunic](https://gamebanana.com/skins/161477) mod. Usually this is because of strange packing or files from an 
older version of the game. If you need help or clarification, you can ask in the [BOTW Modding Hub](https://discord.gg/vPzgy5S).
