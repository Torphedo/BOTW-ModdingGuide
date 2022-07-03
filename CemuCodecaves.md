## Intro
In this guide, I'll go over how you can turn all the PowerPPC instructions in a Cemu codecave into assembled hex. In this binary form, they are working PPC
instruction data, and could theoretically be placed into an RPX executable.
This is a key step in porting previously Cemu-exclusive patches to the Wii U console.

## Finding Offsets
Install the graphics pack of your choice. For this example, I'll be using an [older/simpler version](https://gamebanana.com/dl/590357) of
[dragbe](https://gamebanana.com/members/1695242)'s Durability UI mod.    
If the assembly file starts with `[BotWV208]`, change the text in the brackets to something unique. Boot the game, then select `Debug > View PPC Debugger`
from the options bar.      

<img src="https://user-images.githubusercontent.com/73564623/177022961-a871138e-988e-442d-98cd-07fc54b19586.png" width="400"/>

Find the `Modules` window on the bottom left, then move it up above the `Breakpoints` window so you can actually see it. Resize the `Address` column until
the entire address is visible.    
<p align="center">
  <img src="https://user-images.githubusercontent.com/73564623/177023078-ea2dff9b-648e-4f38-81f9-f9003934438c.png" width="500">
  <img src="https://user-images.githubusercontent.com/73564623/177023077-f1c9955a-66ec-4d30-aee3-7ef49f547156.png" width="500">
</p>

Copy down the address of your desired codecave in Notepad or another text editor. If you put in a custom name earlier, it will be under that name.
In this example, the desired codecave is `DurabilityUI`, at address `0x01800000`. Open Windows Calculator, and select Programmer mode in the sidebar.
Paste in the address you copied, then subtract `1800000`. Copy down the result, this will be your data's offset in a RAM dump later. Also copy down the
value in the `Size` column of Cemu's `Modules` window.

## Finding The Data
Next, select `Debug > Dump Current RAM` in the menu bar. If you already have a `dump` folder in your Cemu folder, delete it first unless you need it for
something. The dump will take a little bit, don't worry if Cemu freezes up. Go into the `dump` folder, and then into the most recent ram dump folder.
If you don't already have one, install a hex editor like [HxD](https://mh-nexus.de/downloads/HxDSetup.zip), then open `01800000.bin`. Press `Ctrl + G`,
then paste the offset you found in the calculator earlier and press `OK` (If the offset is 0, skip this step). Holding `Shift`, use the arrow keys to select
bytes until the `Length` value at the bottom of the window matches the `Size` value you copied down earlier:     

<img src="https://user-images.githubusercontent.com/73564623/177023591-6dba0343-dda7-41de-af68-1182ca363201.png" width="500"/>

Copy the bytes, then paste them into a new file and save it so you can find it later.
