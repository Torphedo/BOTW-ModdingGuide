# Intro/Goals 
  
This is a WIP tutorial, so right now it only has procedure. I'm currently working on reverse-engineering how certain special materials work, so I can try to isolate
their properties. In this example, I'll be using Cafe Shader Studio to try to reverse-engineer the [Glass Armor](https://cdn.discordapp.com/attachments/754471358553129082/884300538425000007/GlassArmor.bnp)'s properties
(This serves doubly as documentation on what properties are needed to create a glass effect). At some point, I intend to follow up on Amely's work trying to understand
the `HyliaLeaking` material that's responsible for the lack of cel shading at the Bridge of Hylia.  
  
# Exporting Material Properties
  
Since the material is derived from ChuChu jelly (the material of `Item_Enemy_40`), we can compare the 2 materials to find all of the edits that were made. Using Cafe 
Shader Studio, we can [export these 
properties](https://media.discordapp.net/attachments/754471358553129082/884794976888848444/2021-09-07_09_38_51-Cafe_Shader_Studio__OpenGL_Version__3.2.0_NVIDIA_461.72.png) to JSON, which makes it far easier to study. Once both materials are
exported, we can compare their differences. I'll be using WinMerge. From here, I suggest just making these edits 1 by 1 until you see the properties you want appear.
In my case, I gave the Hylian Shield the `Item_Enemy_40` material, then tinkered with the values.  
  
My Findings:

TBD, will add after further research.
