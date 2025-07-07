# InfiltrationEngine ToolingForTinkerers
**This repository is a fork** of the original, which may be found @ https://github.com/MoonstoneSkies/InfiltrationEngine-Custom-Missions

For the purposes of anyone not in-deep trying to experiment with undocumented stuff, those tools will do just fine

**Do NOT submit bug reports for bugs which occur when using this fork of the tools**, only report a bug if it can be reproduced with the unmodified official tooling

To confirm that users of the tool have read this, none of this fork's features will function without setting a "`ToolingIsInFactForTinkerers`" attribute to `true` on `workspace`

## Attribute Discard Logging
After enabling tinker features (see prior section) attribute discard logging will be enabled - this will log a warning any time an attribute is discarded by the exporter, accompanied by a reason for the discard

Discards come in the following levels, ordered highest to lowest priority
1) `AttrUnknown` - Attribute is not known to be valid and will not be bypassed
2) `AttrIncompat` - Attribute's type is not compatible with the known valid type
3) `AttrUnknownBypass` - Attribute is not known to be valid but bypassing is enabled
4) `UncaughtDiscard` - A discard my code didn't catch elsewhere, currently a failsafe for failing to detect a discard
5) `DefaultPolicy` - Attribute's value was the same as the default value, and was discarded as serializing defaults was disabled

The `TinkerAttrLogLevel` attribute on `workspace` may be set to any of the following values to limit logging:
- `NONE`/`MIN`
- `ATTR_UNKNOWN`
- `ATTR_INCOMPAT`/`DEFAULT`
- `ATTR_UNKNOWN_BYPASS`
- `UNCAUGHT_DISCARD`
- `DEFAULT_POLICY`
- `MAX`/`ALL`

# InfiltrationEngine Custom Missions
This repository contains tooling and templates for the InfiltrationEngine games, better known as Entry Point: Freelancer's Cut and Operators

A more complete guide for this system can be found here, courtesy of GhfjSpero:
https://docs.google.com/document/d/1LAvisY11Fq8_jbyoq5iz7pWnZoSETy429hJYfsEwdP0

Mission templates and prop models provided in this repo are licensed under Creative Commons Attribution-NonCommercial-ShareAlike license (https://creativecommons.org/licenses/by-nc-sa/4.0/). Generally, this means is that you're free to create and share derivative works for non-commercial purposes as long as they are distributed under the same license.

## Quick Start
The InfiltrationEngineTools plugin provided in this repo are the internal tools used for the development of official missions. Install them by placing them in the plugins folder for Roblox Studio. The Prop Preview plugin also requires the Props asset from the Templates folder to be added to the place file that you're opening (refer to the README in the asset itself for more details). All tooling requires your mission to be placed in workspace and named `DebugMission` to function properly

The SerializationTools plugin generates the mission codes from your custom missions that can be loaded into the game. It's installed in the same way as the InfiltrationEngineTools plugin.

## Using Mission Templates
Official missions are provided as templates to work off of/learn from for creating custom missions. When inserting a mission template into Roblox Studio, make sure workspace is clear of other parts and models (including the baseplate). If the mission is moved from it's original location on insert (or dragged to another location later) the pathfinding data will be offset and NPC pathing will likely break. You can check if pathfinding nodes are in the correct place using the Meadow Map plugin.

## Loading Mission In Game
To test your mission in game, open the Mission Exporter and hit generate code. If things are set up properly, one or more code segments will by generated that can then be selected and copied. Once you have mission codes, you can enter the game, start a custom mission from the main menu, and then copy your mission codes into the input modal. While in the custom mission or custom mission lobby, you can hit L at any time to reopen the modal and load a different mission code. If multiple code segments are given by the exporter, they must all be copied into the modal individually (Roblox restricts how many characters can be copied into a textbox at once)

Currently, Custom Missions are only available in Entry Point: Freelancer's Cut experimental servers, and can only be played singleplayer.

## GitHub Gist Importing
To make missions easier to share, you can upload the mission data to a GitHub Gist. You can copy the link to the Gist into the load mission modal instead of the code segments. You CANNOT use segmented mission codes for this - You can export large missions as a single code by creating an attribute called `ReadDocs` on workspace and setting it to true. Codes more than 200k characters cannot be directly imported into Roblox.
