# Frequently Asked Questions

**How can I install Delta Emulator?** As of April 5th, 2024, Apple is allowing emulators that only emulate, "Retro game consoles only", this being said, you can now download Delta Emulator directly from the App Store.

<s>**How can I install Delta Emulator?** Unlike other iOS apps, you cannot install Delta from the official App Store. As of right now, the recommended installation method is through the use of the [AltStore.](http://AltStore.io) This method does currently require a computer, so it may not work for you.</s>

**What devices are supported?** Delta supports all devices iOS 12.2 and up, including special optimizations for the iPhone X series! Meaning "iPhone 5s and later, all iPad Air models and later, iPad mini 2 and later and iPod touch 6th generation" models are supported.

Note: If you have an iOS 12 but not 12.2 or above device, you can find an IPA of delta that is compatible with iOS 12.0 and up in the releases section of [Delta’s repository.](https://github.com/noah978/Delta-Docs/tree/44eb29b77898d49ab889501eaef5379d5b33bb16/rileytestut/Delta/releases/README.md)

## Usage

**How do I add games to Delta?** There are currently 3 ways to add games to Delta: 1. Open a web browser \(Ex. Safari, Chrome, etc.\) on your iOS device, go to the place you normally download your ROMs, then find the game you want to download. Begin the download, and wait until it completes. Once it's downloaded, tap either "Open in Delta..." or "Open in..." and tap Delta, and it'll then open Delta with the game ready for you to play. The "Open in" button will also work with any other application that you may store your games in. \(Ex. Google Drive, Dropbox, Files, etc.\) 2. Download the ROM you want to play on your computer. Open iTunes with your iOS device plugged in, then click on your device in the top right corner. Click "Apps" at the top of the screen, then scroll to down to the "File Sharing" section. Click Delta, then drag in the games you want to play. Then while in the Delta app, hit the add button \(top right\) and select iTunes to import. 3. If you already have ROMs for Delta in Google Drive or Dropbox \(as a part of Delta Sync: Simply activate syncing on your device. All the ROMs, saves, cheats, save states, etc. you may have should begin to download automatically.

**My ROM isn’t importing correctly, how do I fix this?** Check out the ROM guidelines for each system [here](https://noah978.github.io/Delta-Docs/ROM-Guidelines). If your ROM meets the guidelines and still doesn’t work, you might have a corrupted ROM and you should replace it with a new one. Double check that the ROM is zipped correctly - only the ROM itself should be zipped, not a folder with the ROM inside.

**How do I delete games from Delta?** Simply long-press the image of the ROM you want to delete, press the delete button and confirm any additional dialogue that pops up. Please be warned though: saves, ROMs and other associated data that you have in Dropbox or Google Drive _will_ be deleted. And subsequently, the files will be deleted on any other devices with Delta Sync enabled.

**Can I transfer files between my device and my computer?** Yes, all data can be transferred and backed up on your computer. However, only save files and ROMs will work with other emulators as Delta save states and cheat files are only compatible with Delta. Open iTunes with your iOS device plugged in, then click on your device in the top right corner. Click "Apps" at the top of the screen, then scroll to down to the "File Sharing" section. Click Delta, and now you can drag the “Database” folder to your desktop. Inside the folder is all of your data.

If iTunes is not working for you, then I would recommend using a third-party tool like [3uTools](http://www.3u.com/) or [SynciOS](https://www.syncios.com/) to transfer the save files easily.

_\(Still in Beta\)_ You can also access the ROMs and saves from the Files app in the On My iPhone section in a folder named Delta. In addition, you can export saves individually by long-pressing the game in Delta and selecting "Export Save" from the context menu.

Note: In order to find a specific game file, you will need to long press a rom in Delta, hit share, then copy deep link. The unique combination of characters following "/game/" is the name and [SHA1 Hash](https://en.wikipedia.org/wiki/SHA-1) of your file in the database folder.

**If I delete Delta, will I lose my data?** Yes. If the app no longer opens, copy all of your data to your computer \(the database folder\) so it isn’t lost, then you can try reinstalling the app and dragging your data back in. However, if you do delete the app from your phone but had Delta Sync enabled, your data in Dropbox or Google Drive will be safe and able to sync download when you get Delta reinstalled.

## General Features

**How can I enable Fast-Forward?** While playing a game, tap the Menu button, then tap the "Fast Forward" icon \(two triangles pointed right\). Or, if you have an MFi controller or a keyboard connected to your device, you can configure one of the buttons to enable fast forward whenever it is held down.

**Can Delta hold a button for me?** While playing a game, tap the Menu button, then tap the "Hold Button" icon. This will bring up the controller skin so you can choose which button\(s\) to sustain. Or, if you have an MFi controller connected to your device, you can configure one of the buttons to enter hold button mode whenever it is held down. Once you have done this, tap the buttons you want to remain pressed. Then press the menu button to exit.

**How do I change the graphics filters?** This feature is currently available in Beta with custom skin options. This will likely be expanded upon in the future for various common filters.

**Does Delta support iPad?** Yes. The public release of Delta only supports a letterboxed version of Delta currently. Full iPad support with custom skins is currently in development.

**Does Delta run natively on Apple TV?** Not yet. This is planned for the future but might take some time to complete.

**Can I link two devices with Delta running over WiFi/Bluetooth so I can trade Pokémon/battle/whatever else requires two Handheld consoles?** Not yet, but you can transfer the saves to your computer and link them together using a PC emulator such as [VBA-Link](http://www.vbalink.info/download-gba-emulator.htm) or [melonDS](http://melonds.kuribo64.net/). This feature may be coming to Delta eventually! 🤞

## Save States

**How can I create a save state?** While playing a game, tap the Menu button, then tap "Save State". From the menu that appears, you can tap on a "General" save state to overwrite it, or tap the plus button in the top left to create a new save state. A snapshot of your game and a time signature will be used to help identify the save state. Please note that locked save states and auto-saves cannot be overridden.

**How can I load a save state?** While playing a game, tap the Menu button, then tap "Load State". Tap the save state you want to load, and the game will resume from that point. You can also load the latest save state by force touching on a game, and then swiping up. If you want to choose a specific state, you can long press on the game, tap “Save States” and then select the state you wish to load.

Note: When this action is performed an Auto save state will be created to allow you to return to your previous position in the game if the load was a mistake. Additionally, loading and creating save states does not change your save file, so remember to save when available as well.

**Can I rename save states?** Yes, while playing a game, tap the Menu button. Or if you are in Delta’s main menu, long press on a game. Then tap either "Save State" or "Load State". Now, tap and hold on any save \(Auto saves excluded\), and an options list will pop up. Tap "Rename", enter the new name into the dialogue that appears, then tap "Rename" to confirm.

**Can I protect save states from being overwritten by accident?** While playing a game, tap the Menu button. Or if you are in Delta’s main menu, long press on a game. Then tap either "Save State" or "Load State". Now, long press on any save state \(Auto saves excluded\), and a dialogue will pop up asking you if you want to rename the save state or lock/unlock the save state. Tap "Lock", and the save state will be moved into the "Locked" section. You cannot overwrite a locked save state, but you can still load it and delete it. If you want to unlock a save state, tap and hold the locked save state, then tap "Unlock".

## Cheats

**How do I access the cheats menu?** While playing a game, tap the Menu button, then tap the "Cheat Codes" icon.

**How can I enable/disable cheats?** From the Cheats menu, tap a cheat to toggle between it being enabled and disabled.

**How can I add new cheats?** From the Cheats menu, tap Edit, then tap the plus button. A new cheat menu will appear, where you can name the cheat, select what type of cheat it is, and then finally type the cheat code itself. The cheat code will automatically be on.

**What types of cheats are supported?** See [here](https://noah978.github.io/Delta-Docs/Cheats) for information about accepted cheats.

## Delta Sync \(Dropbox / Google Drive\)

**How do I enable syncing?** From the main menu, enter the settings and scroll down to the cloud syncing section, then click enable syncing. From here, Delta will give you the option to sign into Dropbox or Google Drive, depending on your preference. Sign in, and Delta will start syncing data to your selected cloud service.

**Why are all my games listed as "Conflicted" after turning on Syncing?** This means a save file for this game already exists in Dropbox or Google Drive. Since Delta doesn't know which save file you'd prefer to use, it marks the game as conflicted and turns off syncing, so the correct save file isn't accidentally saved over.

**How can I get rid of a conflict or resolve a game?** From the Syncing menu, tap the name of the conflicted game. From the new view that appears, you'll see the local save file for this game, as well as any that exist in Dropbox or Google Drive. Select either the local save file or one of the Cloud save files to use on all your devices, then toggle the switch at the top on. This will sync the save file you selected to all your devices, and turn syncing back on for the game.

**Can I enable/disable syncing for individual games?** Yes! From the Syncing menu, tap the name of the game you want to enable/disable syncing for, then toggle the switch at the top of the new view.

**Can I sync to multiple cloud services?** At the moment, no. But if you really want the ability to do this, it may be added in the future.

**I accidentally chose the wrong save file to sync on a conflicted game, how can I restore the other save file?** From the Syncing menu, find the game you wish to revert to an older save file on. You can then pull up a list of previous saves and select one of them to sync with.

## Custom Controller Skins

**How can I change skins?** From the main menu, tap the settings icon in the top left corner. Scroll down to the Controller Skins section, then tap one of the emulated systems, depending on which skins you want to change. From the menu that appears, select either Portrait or Landscape, then tap the skin you want to use for the selected orientation. You can switch skins at any time.

**How can I add more skins?** There are three ways to add skins to Delta listed below, after it is imported the skin will appear in the skin selection view.

* Open a web browser \(Ex. Safari, Chrome, etc.\) on your iOS device, and go to any Delta skins website \(such as [skins4delta.com](https://skins4delta.com) or [deltaskins.us](https://deltaskins.us/). Find the skin you want, and download it. Once it's downloaded, tap either "Open in Delta..." or "Open In..." then tap Delta.
* Download the `.deltaskin` file to your Files app. Then while in Delta, hit the plus button on the top right and choose "Files." Navigate to the skin file in the Files app browser and tap to import.
* Download a `.deltaskin` file from a Delta skin website on your computer. Open iTunes with your iOS device plugged in, then click on your device in the top right corner. Click "Apps" at the top of the screen, then scroll to down to the "File Sharing" section. Click Delta, then drag in the skin you want to use.

**Can I change the controller skin opacity?** Yes! From the main menu, tap the gear in the top left corner. Scroll down to Controller Opacity, and move the slider to change how transparent the skins are. \(The custom skin has to support opacity for this to work, all default landscape skins do.\)

**Can I make a game always default to a specific skin?** You can do this by long-pressing a game and selecting "Change Controller Skin" from the context menu.

**How can I make my own skins?** Follow the tutorial located [here](https://noah978.github.io/Delta-Docs/Skins) for the complete instructions on how to make your own custom skins!

## Event Distribution

Events are not available yet, but will likely be added in an update after the initial release.

