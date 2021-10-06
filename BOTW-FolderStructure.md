
In this post, I'll go over Breath of the Wild's general folder structure, and the file formats used in each of these areas of the game. The first thing
to note is that the game splits all its files between the Base Game directory (`00050000\101c9400\`) and the Update directory (`0005000e\101c9400\`), because the game disc wasn't big enough for the entire thing. (this carries over to digital versions too) This is why it won't run in Cemu
without the update. If you can't find what you're looking for in the base game, try looking in the update folder instead. 

## Actor\

This folder contains `ActorInfo.product.sbyml` and `Pack\`. The game loads `ActorInfo.product.sbyml` first, which tells it things like what
damage values to display for weapons. This ensures that there's no issues while the game is loading the full actorpack files.

Tool: [Wildbits](https://gamebanana.com/tools/6660)

Fun Fact: The `.product` in the filename indicates that this file was machine-generated when Breath of the Wild was compiled.

### Pack\

This folder contains `.sbactorpack` files (commonly known as actorpacks). These are essentially complex config/parameter files for every
weapon, object, item, armor, NPC, and enemy in the game. These are collectively known as **actors**. By editing actorpacks, you can change the
damage a weapon does, its durability, the armor value of an armor, an enemy's health, animation settings, and *much*, ***much*** more.

Tool: [Wildbits](https://gamebanana.com/tools/6660)

Fun Fact: The `.s` in the name indicates that it's been compressed with Nintendo's custom compression algorithm, Yaz0. Underneath this
compression layer, the file is a `SARC` archive (another proprietary compression format).

## Effect\

This folder contains all the game's particle effects, in `.sesetlist` files. It's currently impossible (as of time of writing, October 5 2021) to add
entirely new particle effects, we can only edit the existing ones. This is because the database of all particle effects is a completely custom format
that needs more research before new entries can be added. Significant progress has been made recently, but we're not quite there yet.

Tool: [Locke's Toolbox](https://github.com/LockeExile/Switch-Toolbox/releases) (Affectionally known to me as Lockebox)

Note: Don't use Lockebox on anything other than effect files, the rest of its code is ***really*** old.

## Event\

This folder has the game's eventflows, which are incredibly powerful if you know what you're doing. Each `.sbeventpack` file can be opened
with [Switch Toolbox](https://github.com/KillzXGaming/Switch-Toolbox/releases), at which point you can extract the `bfevl` (**B**inary **C**afe **EV**ent f**L**ow). The `.bfevl` can be edited using [eventeditor](https://pypi.org/project/eventeditor/).
When you finish making your edits, save the event flow and put it back into the `.sbeventpack` with Toolbox.

Tools: [Switch Toolbox](https://github.com/KillzXGaming/Switch-Toolbox/releases) and [eventeditor](https://pypi.org/project/eventeditor/)

## Font, Game, and Local

Font is exactly what it sounds like, Game\ has some LOD stuff you'll never need to interact with, and some obscure "Stats" files. Local\ has some region information. I forgot these folders existed, and you probably will too. 

## Map\

This contains `.smubin` files, which from my understanding, are essentially a list of models and where they're located on the map. There's a `.smubin` file for every map square. This is one of the areas of modding I know barely anything about, more information here would greatly appreciated.

Tool: [Ice Spear](https://github.com/NiceneNerd/ice-spear/releases)
