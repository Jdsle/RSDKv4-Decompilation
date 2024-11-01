![](header.png?raw=true)

A complete decompilation of Retro Engine v4 and the menus from Sonic 1 and 2 (2013).

# **SUPPORT THE OFFICIAL RELEASE OF SONIC 1 & 2**
+ Without assets from the official releases, this decompilation will not run.

+ You can get official releases of Sonic 1 & Sonic 2 from:
  * Windows
    * Via Steam, from [Sonic Origins](https://store.steampowered.com/app/1794960)
    * Via the Epic Games Store, from [Sonic Origins](https://store.epicgames.com/en-US/p/sonic-origins)
  * iOS
    * [Sonic 1, Via the App Store](https://apps.apple.com/au/app/sonic-the-hedgehog-classic/id316050001)
    * [Sonic 2, Via the App Store](https://apps.apple.com/au/app/sonic-the-hedgehog-2-classic/id347415188)
    * A tutorial for finding the game assets from the iOS versions can be found [here](https://gamebanana.com/tuts/14491).
  * Android
    * [Sonic 1, Via Google Play](https://play.google.com/store/apps/details?id=com.sega.sonic1px)
    * [Sonic 2, Via Google Play](https://play.google.com/store/apps/details?id=com.sega.sonic2.runner)
    * [Sonic 1, Via Amazon](https://www.amazon.com.au/Sega-of-America-Sonic-Hedgehog/dp/B00D74DVKM)
    * [Sonic 2, Via Amazon](https://www.amazon.com.au/Sega-of-America-Sonic-Hedgehog/dp/B00HAPRVWS)
    * A tutorial for finding the game assets from the Android versions can be found [here](https://gamebanana.com/tuts/14492).

Even if your platform isn't supported by the official releases, you **must** buy or officially download it for the assets (you don't need to run the official release, you just need the game assets).

If you want to transfer your save(s) from the official mobile version(s), the **Android pre-forever** file path is `Android/data/com.sega.sonic1 or 2/SGame.bin` (other versions may have different file paths). Copy that file into the decompilation's folder with the name `SData.bin`.

# Additional Tweaks
* Added the built in script compiler from RSDKv5U.
* Added a built in mod loader and API, allowing to easily create and play mods with features such as save file redirection, custom achievements and XML GameConfig data.
* Custom menu and networking system for Sonic 2 multiplayer, allowing anyone to host and join servers and play 2P VS.
  * Servers may be unreliable; this feature is more or less a proof of concept.
* Egg Gauntlet Zone is playable in the Time Attack menu in Sonic 2, if you're using a version of the game that includes it.
* There is now a `settings.ini` file that the game uses to load all settings, similar to Sonic Mania.
* The dev menu can now be accessed from anywhere by pressing the `ESC` key if enabled in the config.
* The `F12` pause, `F11` step over & fast forward debug features from Sonic Mania have all been ported and are enabled if `devMenu` is enabled in the config.
* A number of additional dev menu debug features have been added:
  * `F1` will load the first scene in the Presentation stage list (usually the title screen).
  * `F2` and `F3` will load the previous and next scene in the current stage list.
  * `F5` will reload the current scene, as well as all assets and scripts.
  * `F8` and `F9` will visualize touch screen and object hitboxes.
  * `F10` will activate a palette overlay that shows the game's 8 internal palettes in real time.
* Added the idle screen dimming feature from Sonic Mania Plus, as well as allowing the user to disable it or set how long it takes for the screen to dim.

# How to Build

This project uses [CMake](https://cmake.org/), a versatile building system that supports many different compilers and platforms. You can download CMake [here](https://cmake.org/download/). **(Make sure to enable the feature to add CMake to the system PATH during the installation!)**

You will also need [Emscripten.](https://emscripten.org/docs/getting_started/downloads.html) Download and install it by following the provided instructions on the page.

## Get the source code

In order to clone the repository, you need to install Git, which you can get [here](https://git-scm.com/downloads).

Clone the repo **recursively**, using:
`git clone --recursive --single-branch --branch web https://github.com/Jdsle/RSDKv4-Decompilation`

If you've already cloned the repo, run this command inside of the repository:
```git submodule update --init --recursive```

## Compiling

> [!NOTE]  
> This fork does *not* run standalone! If you plan on making changes or edits, you will need to also build the [RSDK-Library Engine Manager](https://github.com/Jdsle/RSDK), or build your own interface.

Compiling is as simple as typing the following in the root repository directory:
```
emcmake cmake -B build
cmake --build build
```

The resulting build will be located somewhere in `build/` depending on your system.

The following cmake arguments are available when compiling:
- Use these by adding `-D[flag-name]=[value]` to the end of the `cmake -B build` command. For example, to build with `RETRO_DISABLE_PLUS` set to on, add `-DRETRO_DISABLE_PLUS=on` to the command.

### RSDKv4 flags
- `RETRO_REVISION`: What revision to compile for. Takes an integer, defaults to `3` (Origins).
- `RETRO_DISABLE_PLUS`: Whether or not to disable the Plus DLC. Takes a boolean (on/off): build with `on` when compiling for distribution. Defaults to `off`.
- `RETRO_FORCE_CASE_INSENSITIVE`: Forces case insensivity when loading files. Takes a boolean, defaults to `off`.
- `RETRO_MOD_LOADER`: Enables or disables the mod loader. Takes a boolean, defaults to `on`.
- `RETRO_NETWORKING`: Enables or disables networking features used for Sonic 2's 2P VS mode. Takes a boolean, defaults to `on`.
- `RETRO_USE_HW_RENDER`: Enables the Hardware Renderer used by the main menu and touch controls UI. Takes a boolean, defaults to `on`.
- `RETRO_ORIGINAL_CODE`: Removes any custom code. *A playable game will not be built with this enabled.* Takes a boolean, defaults to `off`.
- `RETRO_SDL_VERSION`: *Only change this if you know what you're doing.* Switches between using SDL1 or SDL2. Takes an integer of either `1` or `2`, defaults to `2`.

# Contact:
Join the [Retro Engine Modding Discord Server](https://dc.railgun.works/retroengine) for any extra questions you may need to know about the decompilation or modding it.
