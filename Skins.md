### ⚠️ Warning ⚠️
This tutorial currently lacks any information regarding iPad custom skins. Details about iPad skins will be included once they arrive in Delta. Be aware that the properties of Delta Skins may change over time. Please report any errors in this tutorial by creating a [new issue.](https://github.com/noah978/Delta-Docs/issues/new/choose)

# Delta Custom Skins

Delta Emulator was designed with the purpose of allowing custom skins to be produced *by anyone*. This allows everyone to create their own skins for either functionality or creativity. Please read on if you are interested in making your own skin or just want to know how Delta's custom skins work.

## Download templates

The following links will allow you to directly download each of the default skins for each of the systems Delta supports. It is advisable for beginners to base their skin off of the existing templates. You can download them individually or in one zip file if you plan on making skins for various systems.

*   [NES](https://github.com/rileytestut/NESDeltaCore/raw/master/NESDeltaCore/Controller%20Skin/Standard.deltaskin)
*   [SNES](https://github.com/rileytestut/SNESDeltaCore/raw/master/SNESDeltaCore/Controller%20Skin/Standard.deltaskin)
*   [N64](https://github.com/rileytestut/N64DeltaCore/raw/master/N64DeltaCore/Controller%20Skin/Standard.deltaskin)
*   [GBC](https://github.com/rileytestut/GBCDeltaCore/raw/master/GBCDeltaCore/Controller%20Skin/Standard.deltaskin)
*   [GBA](https://github.com/rileytestut/GBADeltaCore/raw/master/GBADeltaCore/Controller%20Skin/Standard.deltaskin)
*   [NDS](https://github.com/rileytestut/DSDeltaCore/raw/master/DSDeltaCore/Controller%20Skin/Standard.deltaskin)
*   [Download All](https://drive.google.com/uc?authuser=0&id=1RQsKmhS38JTjtdmZ3YjcSFZ1KojXzPWI&export=download)

Please note that the Nintendo DS default skin is still currently the same design as SNES with modifications to fit the screen size of the DS.

## Skin Basics

All delta skins are contained in ```.deltaskin``` files, for example, all the default skins included with Delta are named ```Standard.deltaskin```. These are actually just ```.zip``` files with the extension renamed. So if you change the extension name from ```.deltaskin``` to ```.zip```, you can now access the files contained within. These files should include images of different sizes and orientations which have a ```.pdf``` extension and a single ```info.json``` file.

The info.json contains all the necessary information for a skin to function properly. This information includes:
*   name
*   identifier
*   gameTypeIdentifier
*   Image Names
*   Button Mappings
*   Whether landscape supports opacity
*   Whether the skin should be displayed in debug mode

(Don’t worry if you’re already confused, all of these will be explained further in this tutorial.)

As you can tell from the extension, this file is a JSON file. Although JSON files are primarily used by web services to transfer data, it was chosen to be used in Delta skin files due to its simplicity. Everything in this tutorial can be done via the included text editor on your computer, but it's strongly recommended you use an application designed to open and edit JSON files, as this is much less error-prone (and easy!).

*   For Mac, Cocoa JSON Editor was used to make the JSON files for the included default skins, but any other JSON editor will work fine.
*   For Windows, using an online editor is probably easiest but a powerful text editor like Atom, Sublime Text, or Coda will work as well.

While working with a JSON file, it's suggested that you close all brackets (using the arrows normally found on the left side of the JSON editor) for the purpose of readability.

---

Open up the ```info.json``` file and you should see these five items.

*   name
*   identifier
*   gameTypeIdentifier
*   debug
*   representations

Each one will be explained further below.

### name

This item is rather self-explanatory, this is what the skin will be called within Delta’s skin selection menu. Replace the name with whatever you would like to name your skin.

### identifier

This is how Delta internally uses and stores skin files. To ensure that one skin doesn't overwrite another skin, each skin identifier should be unique. The default Delta skins have the identifier com.Delta.gba.standard. However, it is recommended that you follow Apple's reverse-dns format for this to ensure it is unique. For example, use com.rileytestut.retro. The actual value of identifier doesn't matter so long as it is unique.

### gameTypeIdentifier

This is how Delta further determines the compatibility of each skin. Unlike the identifier, each gameTypeIdentifier needs to remain the same for Delta to identify which system the skin belongs to. For example, the Standard GBA skin has the following gameTypeIdentifier: com.rileytestut.Delta.game.gba.

### debug

This determines whether the skin should be displayed in “debug mode.” By default this is set to false, but when set to true, Delta will overlay red squares on top of where the buttons are mapped to. It’s recommended that you set this to true while making your skin, so that the buttons can nicely match up with the image.

![Debug Mode Enabled](http://www.gba4iosapp.com/images/tutorials/skins/debug_mode.png)

### representations

Within the representations, you will find another bracketed category called iPhone. When iPad support is released, the iPad will be listed as a separate representation. In the following section, we will be focusing on the items inside the iPhone representation.

# Changing the Images

Almost every time you create or modify a skin, you'll be changing the images that are displayed when actually using the skin. Luckily, changing the images is rather straightforward!

Inside the iPhone category, you'll see two new more categories: **standard** and **edgeToEdge**. Standard contains the details for skins that support for regular iPhones. EdgeToEdge gives the skin support for all X-series devices with the taller screen size. You don't have to include both categories and the skin should still work for the iPhones of the chosen variety.

Delta detects what orientations are supported in a skin by the presence of the portrait and landscape items in the ```info.json``` file. If you wanted to have a portrait-only skin, you'd need to delete the landscape item; similarly, if you wanted to have a landscape-only skin, you'd need to delete the portrait item. Of course, if you wanted to support both orientations, you don't need to delete either.

The following items *can* all be used within both the standard and edgeToEdge categories even if they aren't in the default skins.

*   assets
*   items
*   gameScreenFrame
*   mappingSize
*   extendedEdges
*   translucent

For the purposes of this section, we will only focus on the **translucent** and **asset** items.

### translucent

You can determine whether the orientation you're editing should support Delta's customizable opacity feature. Typically, only landscape skins that go on top of the game screen support this feature, but there's nothing stopping you from enabling it on portrait skins or disabling it for your own landscape overlay skin. To enable this feature, set the value to true. If you want to disable this feature, set it to false, or delete it entirely.

### assets

The assets section is used to load the controller skin images. It should be in this format "resizable" : "name_of_file" In the standard skins it looks like this: ```"resizable" : "iphone_landscape.pdf"``` and we **strongly** recommend that you name your images in a similar naming convention. But you can change the names of your images to anything you want so long as each one is unique and your info.json file reflects that name.

If you'd rather use ```.png``` images, it will require a little more work. You will need to have three differently sized images instead: small, medium, and large. When writing them in the JSON file it will look like this:  ```"small" : "iphone_landscape_small.pdf"``` and again, following the naming convention is recommended. Each ```.png``` image will need to be a size that corresponds with the following devices sizes:

For standard (aka non-X-series) devices:
*   Small = iPhone SE
*   Medium = iPhone 8
*   Large = iPhone 8 Plus

For edgeToEdge (aka X-series) devices:
*   Small = iPhone 11 Pro
*   Medium = iPhone 11
*   Large = iPhone 11 Pro Max

If all you want to do is change the images of an existing skin or one of the "default" templates, at this point you have all the necessary pieces to make your skin, and can skip to the [Finishing the Skin](https://github.com/rileytestut/DeltaCore/wiki/Skins#finishing-the-skin) section below to learn how to turn these files into an actual ```.deltaskin``` file. However, if you want to customize the button mapping or screen location for your skins, carry on into the next section, **Advanced Mapping.**

# Advanced Mapping

Congratulations, if you have gotten this far in the tutorial, you know enough to make simple modifications of how a skin looks. However, skins offer more than just the ability to switch out images; they also give you full control over exactly where the buttons should go, how big they should be, and also where the game screen itself should be placed. Combining all of these, you can create incredibly different layouts for your skins, or maybe just make the game screen a bit smaller when in landscape mode. The point is, skins were designed to be flexible, and this section will show you just how to take advantage of everything!

Before we begin, I need to clarify a few things about the button mappings.
*   Everything on each skin is mapped in **points**. On regular displays, one point is one pixel but on retina displays, one point is actually four pixels; two pixels wide and two pixels tall. So even though the iPhone image is 640 x 480 pixels, everything should be mapped as if it were 320 x 240.
*   Just like on regular computer display, the value starts at the top (y = 0) and gets larger as you move down.

Now, lets take a look at those items we skipped over previously: gameScreenFrame, mappingSize, extendedEdges, and items.

### GameScreenFrame

This is the x, y, width and height of your game screen in points.

### MappingSize

This is the point size width and height of your image.

### ExtendedEdges

In addition to the extendedEdges item in each button mapping, there is also a orientation-specific extendedEdges item. Each extendedEdges item consists of four sub-items: top, bottom, left, and right. These four items "extend" the edge of a button in that direction by whatever value it has been set to. For example, the A button may have a mapping of:

*   x: 15
*   y: 100
*   width: 80
*   height: 80

However, maybe the orientation-specific extendedEdges has a value of 10 in all directions. Now, the actual touch target of the A button would be:

*   x: 5
*   y: 90
*   width: 100
*   height: 100

This has two benefits:

1.  It is easier to map buttons, since all you need to worry about is mapping the exact location of the button, and adding the padding later.
2.  This allows padding to be added to the D-Pad and Menu button without messing up the internal calculations Delta uses for each button.

Another reason to use extendedEdges is to ensure the touch targets of buttons near the edges of the screen actually extend to the edge. This is very important, because if you don't do this, it's easy for the user to tap near the edge of the screen but not perform any action due to the touch targets not extending far enough. To make this an easy fix, each button mapping also has its own extendedEdges item, which will overwrite the orientation-specific version if you enter a value for it. For example, let's take the A button example above. With the orientation-specific extendedEdges, you may notice that it is only 5 points away from the left edge of the screen. To get the best experience out of using your skin, you should make sure it extends all the way to the left edge. To do this, open up the a button mapping, and then open up its own extendedEdges. Once that's opened, set left to 5, and save. Now, the touch target of the A button will be:

*   x: 0
*   y: 90
*   width: 105
*   height: 100

Good, it extends all the way to edge! Per-button extendedEdges can also be applied simply to tweak the extendedEdges of a button. Just remember, map all buttons exactly as they appear on the skin with no padding, and then use extendedEdges to add the padding later.

# items

let's take a look at the format of how each button is mapped. Open any button up and you should see four or five items:

*   x
*   y
*   width
*   height
*   extendedEdges (certain button mappings in the default skins may not have this)

The first four items define the exact location of the button in the image in points, with no padding around it.

Exactly how you find the location and size of the skin buttons may vary, but all Delta skins were mapped by downsizing images to non-retina sizes, opening them in **Photoshop**, and using a combination of masks and the Info window to find the exact pixel locations of each button. Once you find the required information, you can fill in the button mappings for each button ( x and y refer to the x and y co-ordinates of the top left of the button location).

Just so you know what each button does, they're each listed individually below. The more complicated buttons are listed first, then the simple ones are included in the button charts afterwards.

### dpad

The plus-button-like control usually located on the left side of the skin. Typically, it controls movement in games. Unlike other controls, this control is actually divided up into nine sections: eight control directions, and a center neutral section. However, there aren't nine separate mappings for each section; there's only one for the entire D-Pad. So how does Delta know how to divide up the D-Pad into different sections? Simple, it just divides the button mapping you give it into three equal sections horizontally and three equal sections vertically. Because of this, it is very important that you map the D-Pad exactly as it appears on the skin, and with no extra padding, or else the directions will not exactly match what the user sees. To properly add padding without messing up the mapping, you can take advantage of the extendedEdges property.

### thumbstick

The thumbstick is typically used for N64 skins, since it's the only system that Delta currently supports with a thumbstick. But you can actually use a thumbstick instead of a dpad on your skin! This item includes an additional property, "thumbstick," which contains the name, width and height of a separate thumbstick image which will move around the screen with the user's thumb. Similar to the dpad, the mapping is vital that you use the exact position of the button.

### ab

Some skins may have an AB button. When pressed, this button actually presses both the A and B buttons at once, which can be useful for certain games. Including it is the designers choice.

### menu

While the Start button typically pauses the game, this pauses the entire emulator, and allows you to access features such as Save States, Cheat Codes, Fast Forward, etc. As always, make sure to map it exactly without padding, since the pause menu that appears relies on the mapping to position itself.

### touchscreen

This one is specific to Nintendo DS. The mapping must be precise so that the finger / stylus will interact with the screen appropriately. It's also worth noting that the extended edges should not be enabled for this item.

### button charts

| Button     | GB(C)   | GBA     | DS      | NES     | SNES    | N64     |
|------------|---------|---------|---------|---------|---------|---------|
| a          | &check; | &check; | &check; | &check; | &check; | &check; |
| b          | &check; | &check; | &check; | &check; | &check; | &check; |
| x          |         |         | &check; |         | &check; |         |
| y          |         |         | &check; |         | &check; |         |
| select     | &check; | &check; | &check; | &check; | &check; |         |
| start      | &check; | &check; | &check; | &check; | &check; | &check; |
| dpad       | &check; | &check; | &check; | &check; | &check; | &check; |
| cpad       |         |         |         |         |         | &check; |
| thumbstick |         |         |         |         |         | &check; |
| l          |         | &check; | &check; |         |         | &check; |
| r          |         | &check; | &check; |         |         | &check; |
| z          |         |         |         |         |         | &check; |

The following are all custom buttons like the menu button. They work across all systems and utilize Delta Emulator features.

| Button            | Function                                     |
|-------------------|----------------------------------------------|
| quickSave         | Creates a save state                         |
| quickLoad         | Loads the most recent save state             |
| fastForward       | Fast forward as long as the button is held   |
| toggleFastForward | Turn fast forward on until next button press |

It is recommended that you remove any buttons from your skin that do not have an input for the system the skin works with. Otherwise, the user may be confused when tapping a button that doesn't do anything.

# Finishing the Skin

At this point, you have everything you need to convert the files into a skin file you can start using in Delta! Now, the last thing to do is to actually import it into Delta, which thankfully is the easiest part.

As you learned previously, every ```.deltaskin ``` file is just a zip file with the ```.zip ``` extension renamed. That means, to turn your files into a skin file, all you need to do is compress all the individual files into one zip file and rename the extension ```.deltaskin ```.

Please take note that:
*   When compressing the files, make sure to compress the files themselves, and not the containing folder. If you zip the folder and not the files directly, Delta will not be able to extract the files correctly upon import, which will prevent the skin file from being used.
*   When renaming the extension, make sure the extension actually changes. Sometimes, the file may look like its extension was changed, but the computer might have (invisibly) added the extension back on the end of the filename. On a Mac, the best way to ensure the extension changes properly is to right-click the file, click Get Info, and then change the extension there.

Once you have your ```.deltaskin``` file, you need to import it into Delta. If you're working at your computer, generally the easiest way to do this is via iTunes. To import via iTunes, you can follow these instructions:

1.  Connect your iOS device to your computer.
2.  Open iTunes.
3.  Click on your device that appears in the top left corner.
4.  Click the Apps tab near the top of the iTunes window.
5.  Scroll down to File Sharing.
6.  Click Delta, then drag the skin file into Delta.
7.  Launch Delta on your device, hit the plus sign on the top right, and select import from iTunes.

If you don't want to transfer through iTunes, you can always send it to your device via Email, iMessage, or via downloading through an online file space like Google Drive.. Once you receive it on your device, Open In... Delta, and then you can select the newly imported skin in Delta’s settings.

Once you've imported your custom skin, the last step is to start a game of your choice, and start playing with your creation. Congrats, you worked hard for it!
