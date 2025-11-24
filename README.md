# **Devil Connection Mod Loader**

[繁體中文](https://github.com/nekodakohaku-dev/DevilConnection_Mod_Loader/blob/main/README.zh-TW.md)  |  [日本語](https://github.com/nekodakohaku-dev/DevilConnection_Mod_Loader/blob/main/README.ja.md)

This is an unofficial general-purpose Mod Loader designed for the game **"Devil Connection" (でびるコネクショん)**.

This tool allows players to load .asar language packs, patches, or functional mods via external mounting **without decoding or replacing the original massive files**. This architecture significantly reduces patch size and **better protects the copyright of the game authors and mod creators**.

## **✨ Features**

* **Non-Destructive Installation**: Uses HDiffPatch technology to inject only minimal code into the core, keeping a backup of the original file for easy restoration.  
* **Plugin System**: Automatically reads .asar files or directories from the plugins folder.  
* **Priority Management**: Supports loading multiple mods simultaneously, with override order controlled by filenames.  
* **Extremely Lightweight**: The core patch is tiny (only a few KB) and does not affect game performance.

## **🚀 Installation**

Please follow these steps to install:

1. **Download this project**:  
   * Download the latest release ZIP from \[GitHub Releases\].  
2. **Download Patch Tool**:  
   * Go to [HDiffPatch Releases](https://github.com/sisong/HDiffPatch/releases) and download the latest version.  
   * Unzip and find hpatchz.exe (Note: it is **hpatchz**, not hdiffz).  
3. **Place Files**:  
   * Copy all files from this project (Loader.js, patch.hdiff, install\_mod\_loader.bat) and the downloaded hpatchz.exe into the game's root directory.

**📂 File Structure Example:**SteamLibrary\\steamapps\\common\\でびるコネクショん\\  
│  
├── Loader.js                \<-- Core Loader  
├── patch.hdiff              \<-- Core Diff Patch  
├── install\_mod\_loader.bat   \<-- Installation Script  
├── hpatchz.exe              \<-- Patch Tool  
└── DevilConnection.exe      \<-- (Original Game Executable)

4. **Run Installer**:  
   * Double-click **install\_mod\_loader.bat**.  
   * The script will automatically backup the original file and inject the Loader.  
   * Upon success, a plugins folder will be created in the game directory.  
5. **Done**: You can now start installing mods.

## **📖 Usage**

### **🟢 Basic Usage: Installing Mods/Translations**

1. Obtain the mod file you want to use (usually in .asar format, e.g., zh-tw.asar).  
2. Place the file into the **plugins** folder in the game root directory.  
3. Start the game directly; the mod will take effect automatically.

### **🟠 Advanced Usage: Multi-Mod Priority**

The Loader supports mounting multiple mods simultaneously. Priority is determined by Filename Sorting (Z \-\> A).  
Files starting with larger numbers or later letters have higher priority (will override earlier ones).  
Example:  
Suppose the plugins folder contains:

* 01\_Base\_Translation.asar (Base Translation)  
* 99\_UI\_Fix.asar (UI Fix)

Loading Result:  
The Loader will read 99\_UI\_Fix.asar first, and then 01\_Base\_Translation.asar.  
If both mods modify the same image, the game will display the version from 99\_UI\_Fix.asar.  
This allows you to easily create "fix patches" or "compatibility packs" without repackaging the entire translation file.

## **⚠️ Notes & Removal**

* **Game Updates**: If Steam updates the game, the Loader core may become invalid. Simply re-run install\_mod\_loader.bat to repair it (the script handles backup and updates automatically).  
* **Remove Mod**: Just delete the .asar file from the plugins folder.  
* **Remove Loader**:  
  1. Delete Loader.js and the plugins folder.  
  2. Verify integrity of game files via Steam to restore app.asar.  
  3. Alternatively, manually delete app.asar and rename app.asar.bak back to app.asar.

## **📅 Changelog**

* **2025/11/24 (v1.0.0)**  
  * Initial release v1.0.0.  
  * Compatible with game version: Patch Update (2025/11/22).  
  * Support for HDiffPatch extreme compression.

## **⚖️ Disclaimer**

This tool is unofficial software created by a third party and is not affiliated with the original game developers.  
Use this software at your own risk. The author is not responsible for any damage to your game files or save data.  
Please support the original game.
