In this tutorial, I'll be going over how to port existing Cemu code patches to BCML-compatible BNPs. This is mostly a matter of moving files around.  
  

Setup
=====

In modern code patches, the patch is in a file named patch\_.asm. If you have a patches.txt, just rename it to fit this format. Copy the rules.txt and ASM file into a folder named patches. Open rules.txt, then change the version number (eg. version = 4) to 7. Right under this, add a line that says default = true. This will mean the graphics pack is automatically enabled when installed.  
  

BNP Creation
============

Download this template [info.json](https://cdn.discordapp.com/attachments/754471358553129082/888632441072386048/info.json) and save it next to the patches folder, or copy in your own. Change the mod name and description to whatever you want (I usually just copy rules.txt). Select the patches folder and info.json, then right click and hit Add to archive in the 7zip menu (install 7zip if you don't already have it). Leave everything at default, but set the compression level to Ultra and change the file extension to .bnp. Now you can install this file with BCML.  
  

Multiple Graphics Packs
=======================

If for whatever reason you want to add more than 1 graphics pack with a BNP (eg. for more modularity), you can make a subfolder in your patches folder, then place the rules.txt and ASM file in there. BCML will push them as they are, and Cemu will read right through the extra subfolder.  
  

Explanation
===========

When a code patch BNP is installed, BCML makes a new bcmlPatches folder in the graphicsPacks folder. It contains subfolders with the name of the mod, which have whatever you placed in the patches folder. These subfolders, containing a rules.txt and a \*.asm patch file, make up a graphics pack. For the end user, installing a code patch BNP just adds a new graphics pack in Cemu, as if they had manually extracted it there.  
  

ASM to BNP
==========

After talking to my friend [Arch](https://gamebanana.com/members/1797815) about how I could potentially automate this, he created a [tool](https://gamebanana.com/tools/7458) that automatically creates BNPs from an ASM file and a rules.txt. Drag the ASM file onto the tool, and it should generate a BNP file for you.  
  
Notes:  
In case it wasn't clear, this is about Cemu patches specifically. If you want to work on porting your code patch to Wii U console, see [this](https://gamebanana.com/tools/7436) tutorial.
