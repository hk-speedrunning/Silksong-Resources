# Setup Guides

> [!TIP]
> Please note that much of this process is subject to rapid change, and as such this document may be out of date. For help, you can ask in #ss-tech-support in the Discord.

---

- [Setup Guides](#setup-guides)
  - [Livesplit](#livesplit)
    - [LiveSplit (Windows)](#livesplit-windows)
    - [LiveSplit One Druid (Windows, Linux, Mac)](#livesplit-one-druid-windows-linux-mac)
      - [Mac requirement: Rosetta](#mac-requirement-rosetta)
    - [OBS LiveSplit One (Windows, Linux)](#obs-livesplit-one-windows-linux)
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

### LiveSplit (Windows)

- Download the latest version of [LiveSplit](https://livesplit.org/downloads/) & extract the contents to a new `Livesplit/` folder.
  - This folder can be anywhere you like, but some Windows installs may prevent Livesplit from working properly if it is in your Downloads folder.
  - You must have LiveSplit version 1.8.34 or later. You can check the version via right click -> `About`. Livesplit automatically prompts you for updates to both itself and the autosplitter - please don't reject any of these updates.

Configuring the autosplitter manually is not recommended, as it is more complex & the configuration wizard is unusably slow. Instead, we recommend using [HKSplitmaker](https://hksplitmaker.com/?game=silksong) to generate the splits with icons & the autosplitter preconfigured.

- Go to [HKSplitmaker](https://hksplitmaker.com/?game=silksong) & find pre-made splits for your category, then press `Generate`.
  - If your category does not have pre-made splits, use the UI to create your own.
- Press `Download` - HKSplitmaker will then prompt you to save a `lss` file.
- Open Livesplit & `Right Click -> Open Splits...`. Select the `lss` file you just downloaded.
- Activate the autosplitter if it hasn't been already. `Right Click > Edit Splits` and click the `Activate` button above the splits table next to the note about the configurable load remover.
  - If the Activate button is greyed out, re-select the game name from the dropdown, and if that doesn't work see this footnote.[^2]
- Verify the autosplitter has downloaded successfully by pressing `Right Click > Edit Splits... > (above the splits table) Settings`. This window should have more than 2 items in it; if it only has 2 items, close the splits file without saving & restart Livesplit.
  - _This is because on first download Livesplit may delete the settings saved in the LSS file; this workaround ensures you don't accidentally delete the autosplitter config._
- `Right Click -> Compare Against... -> Game Time`. This tells Livesplit to show you the load-removed time, rather than real time.

### LiveSplit One Druid (Windows, Linux, Mac)

Go to the [LiveSplit One Druid Latest Release](https://github.com/AlexKnauth/livesplit-one-druid/releases/latest) page,
and under the `Assets` section, download the one for your architecture and operating system.

When you run LiveSplitOne, it needs to have permission to read memory of other processes.
- Windows: no additional steps required.
- Linux: set the capabilities to include `CAP_SYS_PTRACE`, with a command like `sudo setcap CAP_SYS_PTRACE=+eip LiveSplitOne` to run once after downloading LiveSplitOne.
- Mac: you have to run it under `sudo`, with a command like `sudo ./LiveSplitOne` to run every time you want to open it.

Right-click or Control-click for the context menu:
- Splits, Open... : Select your `.lss` splits file. Go to [HKSplitMaker](https://hksplitmaker.com/?game=silksong) to generate and download `.lss` splits files.
- Open Auto-splitter... : Select the `silksong_autosplit_wasm_stable.wasm` file. Go to the [silksong-autosplit-wasm Latest Release](https://github.com/AlexKnauth/silksong-autosplit-wasm/releases/latest) to download that.
- Compare Against: Game Time.
- Hotkeys: Configure the hotkeys you want. The default hotkeys use numpad, so if your computer doesn't have a numpad, configure them differently.

#### Mac requirement: Rosetta

The autosplitter currently requires the game to be running as an Intel / x86_64 process, not an Apple / arm64 process.
So on Apple Silicon (M1, M2, etc.) Macs, you have to run the game under Rosetta:
- Right click on `Hollow Knight Silksong.app` in Game Files[^1], `Get Info`,  check the box for `Open using Rosetta`.
- Next to `Hollow Knight Silksong.app`, put a [`steam_appid.txt`](https://github.com/hk-speedrunning/Silksong-Resources/releases/download/files/steam_appid.txt) file containing the number `1030300`.
- Open `Hollow Knight Silksong.app` directly from where it is in Game Files, not from your Steam library.
- Check in Activity Moniter, on the CPU tab, the Kind column should say `Intel` for Silksong, not `Apple`.

### OBS LiveSplit One (Windows, Linux)

Go to the [OBS LiveSplit One Latest Release](https://github.com/AlexKnauth/obs-livesplit-one/releases/latest) page,
and under the `Assets` section, download the one for your architecture and operating system.
Follow the instructions in [How to install](https://github.com/AlexKnauth/obs-livesplit-one?tab=readme-ov-file#how-to-install):
- Windows: Extract the `obs-livesplit-one.dll` to `C:\Program Files\obs-studio\obs-plugins\64bit` or equivalent install directory.
- Linux: Ensure the plugins folder exists with `mkdir -p $HOME/.config/obs-studio/plugins`, then extract with a command like `tar -zxvf obs-livesplit-one-*-x86_64-unknown-linux-gnu.tar.gz -C $HOME/.config/obs-studio/plugins/`.

When you run OBS, it needs to have permission to read memory of other processes.
- Windows: no additional steps required.
- Linux: set the capabilities to include `CAP_SYS_PTRACE`, with a command like `sudo setcap CAP_SYS_PTRACE=+eip /usr/bin/obs` to run once after downloading OBS.

Add OBS Source: LiveSplit One.

Properties:
- Splits: Select your splits file. Go to [HKSplitMaker](https://hksplitmaker.com/?game=silksong) to generate and download `.lss` splits files.
- Activate

Open the OBS Settings from File, Settings:
- Go to the Hotkeys section and scroll down until you find LiveSplit One.
- Set a hotkey for `Toggle Timing Method`, and hit Ok.
- Hit that hotkey once to switch from the default, Real Time, to Game Time.

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
    - MacOS: `~/Library/Application Support/Steam/steamapps/common/Hollow Knight Silksong/Hollow Knight Silksong.app`

[^2]: Some internet providers may block GitHub addresses from resolving (eg. Chinese ISPs). You can add a custom DNS resolution to hopefully bypass this.

    - Open Notepad (or another text editor) as Administrator.
    - On Windows, open `C:\Windows\System32\drivers\etc\hosts`
    - On Linux, open `/etc/hosts`
    - On MacOS, open `/private/etc/hosts`
    - Add `151.101.192.133 raw.githubusercontent.com # Allows downloads from GitHub` on a new line and save.
