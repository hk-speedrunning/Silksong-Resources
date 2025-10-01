# Setup Guides

> [!TIP]
> Please note that much of this process is subject to rapid change, and as such this document may be out of date. For help, you can ask in #ss-tech-support in the Discord.

---

- [Setup Guides](#setup-guides)
  - [Livesplit](#livesplit)
  - [Recording using OBS](#recording-using-obs)
  - [Installing Practice Mods](#installing-practice-mods)
    - [BepInEx](#bepinex)
      - [Launching unmodded for runs: Steam](#launching-unmodded-for-runs-steam)
      - [Launching unmodded for runs: All Platforms](#launching-unmodded-for-runs-all-platforms)
    - [DebugMod](#debugmod)
    - [QuickWarp](#quickwarp)

---

## Livesplit

We do not accept the ingame timer as it is too inaccurate and imprecise; we instead use a custom load remover in Livesplit.

> [!IMPORTANT]
> This guide is for Livesplit Windows: guides for other operating systems will come shortly. For now you can adapt the [Hollow Knight ASR guide for Livesplit One Druid](https://github.com/AlexKnauth/hollowknight-autosplit-wasm?tab=readme-ov-file#instructions-for-livesplit-one-druid).

- Download the latest version of [LiveSplit](https://livesplit.org/downloads/) & extract the contents to a new `Livesplit/` folder.
  - This folder can be anywhere you like, but some Windows installs may prevent Livesplit from working properly if it is in your Downloads folder.

Configuring the autosplitter manually is not recommended, as it is more complex & the configuration wizard is unusably slow. Instead, we recommend generating [HKSplitmaker](https://hksplitmaker.com/?game=silksong) to generate the splits with icons & the autosplitter preconfigured.

- Go to [HKSplitmaker](https://hksplitmaker.com/?game=silksong) & find pre-made splits for your category, then press `Generate`.
  - If your category does not have pre-made splits, use the UI to create your own.
- Press `Download` - HKSplitmaker will then prompt you to save a `lss` file.
- Open Livesplit & `Right Click -> Open Splits...`. Select the `lss` file you just downloaded.
- Activate the autosplitter if it hasn't been already. `Right Click > Edit Splits` and click the `Activate` button above the splits table next to the note about the configurable load remover.
- Verify the autosplitter has downloaded successfully by pressing `Right Click > Edit Splits... > (above the splits table) Settings`. This window should have more than 2 items in it; if it only has 2 items, close the splits file without saving & restart Livesplit.
  - _This is because on first download Livesplit may delete the settings saved in the LSS file; this workaround ensures you don't accidentally delete the autosplitter config._
- `Right Click -> Compare Against... -> Game Time`. This tells Livesplit to show you the load-removed time, rather than real time.

## Recording using OBS

> [!Tip]
> This section will later be served with a video guide.

To capture both Livesplit & Silksong at the same time, we recommend [OBS Studio](https://obsproject.com/download).

- Create a Game Capture (or Window Capture if Game Capture does not work) for Silksong itself.
- Create a Window Capture for Livesplit.
  - If you wish for Livesplit to appear with a transparent background, you need to 'key' out the background.
  - To do this, right click your Livesplit source & press `Filters`. Add a new `Color Key` filter. Set the color to the background color of your Livesplit layout, and fiddle with the settings until it looks right.
- Feel free to move your sources in the preview until they look right - you can resize them if they do not fit on the canvas, or if you want to place Livesplit beside the game rather than on top.

Make sure your video follows the [video guidelines](/video_guidelines.md)!

## Installing Practice Mods

Please note that you _**must be on an unmodified install**_ for Speedrun.com submissions; see below for instructions on launching unmodded.

### BepInEx

BepInEx 5 is the modloader we use for Silksong mods. You need to install it to install any mods.

- Download the x64 .zip file for your OS from [this version](https://github.com/BepInEx/BepInEx/releases/latest).
- Extract the downloaded .zip to your Game Files[^1]. Your folder should look like this:
  ![Folder showing the BepInEx folder alongside Hollow Knight Silksong.exe](/media/images/BPXInstallFolder.png)
- Launch the game once to allow BepInEx to generate files & directories for you.
- Check that BepInEx loaded correctly by verifying that the `BepInEx/` folder now contains a `plugins` subfolder.

#### Launching unmodded for runs: Steam

This method adds a separate game to Steam which will always launch with BepInEx.

- Right click `Hollow Knight: Silksong` in the sidebar, press `Properties...`
- Add `--doorstop-enabled false` to the Launch Options bar. This makes your default install unmodded.
- Press `Add a Game > Add non-Steam Game` at the bottom of the sidebar. When prompted, direct it to your existing installation (specifically the Hollow Knight Silksong executable).
  - You can find your game files by right clicking on `Hollow Knight: Silksong` & pressing `Manage > Browse Local Files`.
- Add [this file](https://github.com/hk-speedrunning/Silksong-Resources/releases/download/files/steam_appid.txt) to your game files.
- Rename your duplicate game - this one will launch modded.

#### Launching unmodded for runs: All Platforms

> [!TIP]
> We are currently working on documenting easier methods for other platforms. In the meantime, you can create a second install using whichever method works for your platform.

### DebugMod

DebugMod is the premier practice tool for Silksong, based on HK's DebugMod. A simple usage guide can be found [here](/tools_usage.md).

- Download `DebugMod.zip` from the [Release Page](https://github.com/hk-speedrunning/Silksong.DebugMod).
- Extract the `DebugMod.zip`'s contents to `Game Files`[^1]`/BepInEx/plugins`.

### QuickWarp

A mod that lets you warp to any scene in the game by pressing F5.

- Download `QuickWarp.zip` from the [Release Page](https://github.com/hk-speedrunning/Silksong.QuickWarp).
- Extract the `QuickWarp.zip`'s contents to `Game Files`[^1]`/BepInEx/plugins`.

[^1]: Game files are located _(by default using Steam)_ at:

    - Windows: `C:\Program Files (x86)\Steam\steamapps\common\Hollow Knight Silksong\`
    - Linux: `~/.local/share/Steam/steamapps/common/Hollow Knight Silksong/`
    - MacOS: `~/Library/Application Support/unity.Team-Cherry.Silksong`
