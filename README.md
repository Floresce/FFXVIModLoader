# Final Fantasy XVI Mod Loader
A forked mod loader originated from techiew's Elden Mod Loader: https://github.com/techiew/EldenRingModLoader

This is a simple mod loader that injects both .DLL and .ASI files from the "mods" folder. I was able to test and use [FFXVIFix](https://github.com/Lyall/FFXVIFix) with this mod loader.

I would not recommend using this fork version of the Mod Loader, as this was mainly used for testing. I would recommend checking out [FINAL FANTASY XVI Modding](https://nenkai.github.io/ffxvi-modding/).

Here's some instructions from the original repo that can apply be applied for this:

## Load ordering
To specify a load order for a mod, create a folder with the same name as your DLL inside the "mods" folder. Inside the folder create "load.txt" and enter the load order number, which must go from 0 and up. Mods will load in order from lowest to highest number with an interval of 1 second. 

Alternatively, you can specify the load order in "mod_loader_config.ini" like so:
```
[loadorder]
MyDllMod.dll = 1
```
(This overrides the load order specified in the "mods" folder).

Mods with a load order of 0 will be loaded instantly, even ignoring the load delay set inside "mod_loader_config.ini". I recommend not using 0 unless the mod is absolutely required to have an immediate effect, as race conditions may occur for some types of mods if they load too quickly.

If a load order is not specified for a mod, it will automatically receive a load order after the highest specified load order. Mods can have the same load order number, in which case they will load at the same time.