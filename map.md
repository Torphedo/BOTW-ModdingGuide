Static loaded on bootup
if this is the issue, game will crash about a second after reaching title screen

dynamic loaded during loading screen
will stop halfway on loading screen if dynamic is the issue

static maps can link to objects/events
dynamic actors loaded on the fly

Bootup.pack\Ecosystem\LevelSensor.sbyml
Contain point thresholds for enemies to advance to the next tier
Also contains point award data, which is multiplied by `Level2EnemyPower`
When point threshold is reached, moves onto next tier.
Enable levelling by setting `LevelSensorMode` to 1 or more

Cannot set point reward value for custom actors without executable patch

ActorLink is the only *required* component to register an actor
Game searches for `Enemy_` for scaling

Once BasicSigOnOnly is set, it stays on
BasicSig can be toggled on and off
DefinitionName determines how the signal is sent



Trigger: Any source of input for LinkTag
I/E: Enemy, Area, Switch, Defined Save flag, Event Based requirements

AND: Signal Starts Off
Awaits input from trigger
If no Trigger, Signal is always active
When triggered, signal turns ON

NAND: Signal starts ON
Awaits input from trigger
If no Trigger, Signal is always OFF
When triggered, signal turns OFF



OR triggers if any enemies die (become inactive)
InOR will stay active unless one of the enemies is inactive, in which case it will switch off
EventTags are used to call eventflows
LinkTagNONE have no use other than to link your static actors together
	e.g. deleting the LinkTagNONE will delete everything linked to it, useful for efficient deletion of setups
	MAKE SURE to INCLUDE ZEROS IN ACTOR NAMES! (Weapon_Sword_24 is wrong)
	if you don't, the entire group will not spawn
AreaBoxes send signals to LinkTags

BOTW logic triggers don't really map to logic gates properly, act a little weird

All saveflags located in Bootup.pack\GameData\GameData.sarc

BOTW Durability represented in 100s

ActorInfo instSizes roughly 1.6x - 1.7x on switch (1.7x to be safe)

ForbidAttention stops you from picking up or opening items/chests (interaction of any kind)

![NANd_ANDS](https://user-images.githubusercontent.com/73564623/137414433-24b70c8c-1e48-41de-8d74-d9634dc25e46.png)
