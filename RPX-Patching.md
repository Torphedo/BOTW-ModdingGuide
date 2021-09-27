Sorry for the repost, I wanted to include some convenient scripts, and after talking to some people, I decided the Tools section was better. Enjoy the scripts!  
  
In this tutorial, I'll show you how to directly patch the game's executable file in order to use code edits on Wii U hardware. This method probably won't work on complex patches such as SotW, or anything that heavily relies on Cemu, like my Master Mode Tweaks mod. Keep in mind that this requires directly replacing the executable file, so keep backups!  
  
Make a copy of the update executable from your dump into whatever folder you're working in (I'll assume you already know where to find the RPX in your dump). Download the [zip](https://gamebanana.com/dl/657701) of scripts and tools, and extract next to the BOTW RPX you copied. Run `setup.bat`. This will:  
  -Generate a decompressed RPX you'll be working off of  
  -Make a backup copy of your vanilla compressed and decompressed RPXs, both stored in the `Vanilla` subfolder.  
Run `restore-vanilla.bat` to replace the current decompressed RPX with the vanilla copy in the `Vanilla` subfolder.  
  
There are 2 ways to patch the executable. Only use the second method if you run into an issue with the PPC converter, or you're attempting to port something that uses variables that can be set by the users (eg. patches that set floats that are obnoxious to encode properly).  
  
# Cemu Patch Method 
  
Go into the Cemu directory, open the graphics pack with the code edit you want, and open the `*.asm` patch file in Notepad. Copy the instruction offset, leaving off the 0x02, then add `48B5E0` (the offset of the decompressed RPX header data) to it. This will give you the offset of the instruction in the decompressed RPX. Open the decompressed RPX you created earlier in a hex editor like [HxD](https://mh-nexus.de/downloads/HxDSetup.zip), then go to the offset you calculated (Search > Go To). Use some sort of [converter](https://shell-storm.org/online/Online-Assembler-and-Disassembler/) to assemble the instruction to hex, then edit the RPX's hex starting at the offset. If the converter throws an error, try removing any letters next to numbers (so, `fmr f29, f1` becomes `fmr 29, 1`). Hit save, then re-compress the RPX (see bottom of guide).  
  
# Memory Dump Method
  
This method essentially has Cemu do all the conversion to hex (instead of doing it yourself), but has several annoying extra steps.  
  
Run BOTW with the code patch you want to use on console, and when you get to the title screen, dump the RAM by selecting `Debug > Dump Current RAM`. Go into the cemu directory, then into dump. Rename the most recent ram dump folder to `patch` or something of the sort. Now, disable the code patch, and do the same thing, but rename the new dump folder to `unpatched`. We'll be looking at the differences between the 2 dumps (to see where the code edits are and replicate them), so it doesn't matter if other code patches are being used or not, as long as you only disable 1 code patch between dumps. Go into the RAM dump folders you renamed, then delete all the files inside except for `02000000.bin`.  
  
Using WinMerge, open the `02000000.bin` in the `unpatched` folder, then the `02000000.bin` in the `patched` folder. When it asks you to show the results instead of the contents, hit `No`. Now, you should see the hex of both files next to each other. Hit `Alt + Down` to see the next difference in the file. This is the edit to the code. Jot down the offset of this difference. Now copy the `02000000.bin` from the `patched` folder to the folder with your decompressed RPX.  
  
Open the decompressed RPX and the memory dump you copied earlier in a hex editor like [HxD](https://mh-nexus.de/downloads/HxDSetup.zip). Add `48B5E0` to the offset you found with WinMerge, then go to this new offset in the RPX. Make the hex edits seen in WinMerge to the decompressed RPX, then save.  
  
Once the hex edits have been made, run `compress.bat` to make a new U-King.rpx (This will replace the U-King.rpx you currently have, but the copy in the subfolder is intact). After this, you can FTP the new RPX onto your Wii U to test it, or replace Cemu's RPX if you just want a quick and dirty test (Note: using a patched executable on Cemu kills performance for some reason).  
  
# Creating XDelta patches for distribution
  
I've bundled the command-line utility `XDelta`, along with a batch file to automatically generate patch files, and `AIO.bat`, which allows you to easily patch executables.  
  
`make-patch.bat`:  
   -Creates a patch file containing the differences between the `U-King-decompressed.rpx` next to this batch file, and the vanilla one created by `setup.bat`.  
  
`AIO.bat`:  
  -Drag any number of xdelta patches onto this batch file to create a patched RPX.  
  -Decompresses RPX to PatchedRPX\\, applies patches, recompresses, deletes decompressed RPX.
