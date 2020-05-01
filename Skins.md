
# Delta Custom Skins

### ⚠️ Warning ⚠️
Be aware that the properties of Delta Skins may change over time. Currently, this tutorial has information regarding iPad custom skins, but the details might change when Delta for iPad is released. Please report any errors in this tutorial by creating a [new issue.](https://github.com/noah978/Delta-Docs/issues/new/choose)

Delta Emulator was designed with the purpose of allowing custom skins to be produced *by anyone*. This allows everyone to create their own skins for either functionality or creativity. Please read on if you are interested in making your own skin or just want to know how Delta's custom skins work.

## Download templates

The following links will allow you to directly download each of the default skins for each of the systems Delta supports. It is advisable for beginners to base their skin off of the existing templates. You can download them individually or in one zip file if you plan on making skins for various systems.

*   [NES](https://github.com/rileytestut/NESDeltaCore/raw/master/NESDeltaCore/Controller%20Skin/Standard.deltaskin)
*   [SNES](https://github.com/rileytestut/SNESDeltaCore/raw/master/SNESDeltaCore/Controller%20Skin/Standard.deltaskin)
*   [N64](https://github.com/rileytestut/N64DeltaCore/raw/master/N64DeltaCore/Controller%20Skin/Standard.deltaskin)
*   [GBC](https://github.com/rileytestut/GBCDeltaCore/raw/master/GBCDeltaCore/Controller%20Skin/Standard.deltaskin)
*   [GBA](https://github.com/rileytestut/GBADeltaCore/raw/master/GBADeltaCore/Controller%20Skin/Standard.deltaskin)
*   [NDS](https://github.com/rileytestut/MelonDSDeltaCore/raw/master/MelonDSDeltaCore/Controller%20Skin/Standard.deltaskin)
*   [Download All](https://noah978.github.io/Delta-Docs/assets/all-skins.zip)

### Looking for inspiration?

Check out some of the skins other people have made at one of the following sites:

*   [DELTASKINS](http://deltaskins.us)
*   [Skins4Delta](https://skins4delta.com)
*   [Delta Skins](https://delta-skins.github.io/)
*   [Circa's Delta Skins](https://circa.im/emu/delta/skins/)

Skins4Delta also offers a [Skin Generator](https://generator.skins4delta.com/) that can take whatever image you want and apply that to the background of their default skin! While the capabilities are not infinite, you can still make your very own skin in seconds.

The [r/Delta_Emulator](https://reddit.com/r/Delta_Emulator) also has an active [Discord Server](https://discord.gg/ERssHqy) that will sometimes take skin requests.

# Skin Basics

All delta skins are contained in ```.deltaskin``` files, for example, all the default skins included with Delta are named ```Standard.deltaskin```. These are actually just ```.zip``` files with the extension renamed. So if you change the extension name from ```.deltaskin``` to ```.zip```, you can now access the files contained within. These files should include images of different sizes and orientations which have a ```.pdf``` extension and a single ```info.json``` file.

The ```info.json``` contains all the necessary information for a skin to function properly. This information includes:
*   name
*   identifier
*   gameTypeIdentifier
*   Image Names
*   Button Mappings
*   Screen Mappings
*   Whether landscape supports opacity
*   Whether the skin should be displayed in debug mode

(Don’t worry if you’re already confused, all of these will be explained further in this tutorial.)

As you can tell from the extension, this file is a JSON file. Although JSON files are primarily used by web services to transfer data, it was chosen to be used in Delta skin files due to its simplicity. Everything in this tutorial can be done via the included text editor on your computer, but it's strongly recommended you use an application designed to open and edit JSON files, as this is much less error-prone (and easy!).

*   For Mac, Cocoa JSON Editor was used to make the JSON files for the included default skins, but any other JSON editor will work fine.
*   For Windows, using an online editor is probably easiest but a powerful text editor like Atom, Sublime Text, or Coda will work as well.

While working with a JSON file, it's suggested that you close all braces and brackets (using the arrows normally found on the left side of the JSON editor for the purpose of readability.

---

Open up the ```info.json``` file and you should see these five items.

```
{
  "name" : "Standard N64",
  "identifier" : "com.delta.n64.standard",
  "gameTypeIdentifier" : "com.rileytestut.delta.game.n64",
  "debug" : false,
  "representations" : {...}
}
```

Each one will be explained further below.

### name

This item is rather self-explanatory, this is what the skin will be called within Delta’s skin selection menu. Replace the name with whatever you would like to name your skin.

### identifier

This is how Delta internally uses and stores skin files. To ensure that one skin doesn't overwrite another skin, each skin identifier should be unique. The default Delta skins have the identifier ```com.delta.console.standard```. While these can technically be set to any unique value, it is recommended that you follow Apple's reverse-dns format for this to ensure it is unique. Your identifier will look like the following: ```com.yourname.console.skinname```. Be sure to include the console if you plan to release the same skin for multiple consoles.

### gameTypeIdentifier

This is how Delta further determines the compatibility of each skin. Unlike the identifier, each gameTypeIdentifier needs to remain the same for Delta to identify which system the skin belongs to. Use the following table to decide which identifier you need to use.

| Console / System                      | gameTypeIdentifier              	|
|---------------------------------------|-----------------------------------|
| GameBoy (Color)                     	| com.rileytestut.delta.game.gbc  	|
| GameBoy Advance                     	| com.rileytestut.delta.game.gba  	|
| Nintendo DS                         	| com.rileytestut.delta.game.ds   	|
| Nintendo Entertainment System       	| com.rileytestut.delta.game.nes  	|
| Super Nintendo Entertainment System 	| com.rileytestut.delta.game.snes 	|
| Nintendo 64                         	| com.rileytestut.delta.game.n64  	|

### debug

This determines whether the skin should be displayed in "debug mode." By default this is set to false, but when set to true, Delta will overlay red squares on top of where the buttons are mapped to. It’s recommended that you set this to true while making your skin, so that you can see when the buttons can match up nicely with the image.

![Debug Mode Enabled](https://noah978.github.io/Delta-Docs/assets/example-skin-debug-enabled.png)

### representations

```
"representations" : {
  "iphone" : {...},
  "ipad" : {...}
}
```

Within the representations, you will find another bracketed category called iphone. When iPad support is released, the iPad will be listed as a separate representation. In the following section, we will be focusing on what you need to know to make new images and change out the old ones.

# Changing the Images

Almost every time you create or modify a skin, you'll be changing the images that are displayed when actually using the skin. Luckily, changing the images is rather straightforward!

Inside the iphone representation, you'll see two more categories:

```
"iphone" : {
  "standard" : {...},
  "edgeToEdge" : {...}
}
```

Standard contains the details for skins that support regular-size iPhones. EdgeToEdge gives the skin support for all X-series devices with the taller screen size. You don't have to include both categories and the skin should still work correctly for the iPhones of the chosen variety.

Delta detects what orientations are supported in a skin by the presence of the portrait and landscape items in the ```info.json``` file.

```
"edgeToEdge" : {
  "portrait" : {...},
  "landscape" : {...}
}
 ```

If you wanted to have a portrait-only skin, you'd need to delete the landscape item; similarly, if you wanted to have a landscape-only skin, you'd need to delete the portrait item. Of course, if you wanted to support both orientations, you don't need to delete either.

The following items can all be used within **both** the standard and edgeToEdge categories:

```
"portrait" : {
  "assets" : {...},
  "items" : [...],
  "screens" : [...],
  "mappingSize" : {...},
  "extendedEdges" : {...},
  "translucent" : false
}
```

For the purposes of this section, we will only focus on the **translucent** and **assets** items.

### translucent

You can determine whether the orientation you're editing should support Delta's customizable opacity feature. Typically, only landscape skins that go on top of the game screen support this feature, but there's nothing stopping you from enabling it on portrait skins or disabling it for your own landscape overlay skin. To enable this feature, set the value to true. If you want to disable this feature, set it to false, or delete it entirely.

### assets

The assets section is used to load the controller skin images. There are two ways you can create your images:
1.  Using PDF files which Delta can automatically resize for each device,
2.  Or using PNG files which you will need three different sizes to support each device.

**Using PDFs**

```
"assets" : {
  "resizable" : "iphone_edgetoedge_portrait.pdf"
},
```

The example above is named in this style: ```device_size_orientation.pdf``` and we **strongly** recommend that you name your images in a similar naming convention. But you can change the names of your images to any unique name and your ```info.json``` file reflects that name.

| Device 	| Size         	| Image Resolution 	| Aspect Ratio 	|
|---------|---------------|-------------------|---------------|
| iPhone 	| Standard     	| 1080 x 1920      	| 9 **:** 16   	|
| iPhone 	| EdgeToEdge    | 1242 x 2688      	| 9 **:** 19.5 	|
| iPad   	| Standard     	| 2048 x 2732      	| 3 **:** 4     |

---

**Using PNGs**

If you'd rather use ```.png``` images, it will require a little more work. You will need to have three differently sized images instead: small, medium, and large. When writing them in the JSON file it will look like this:

```
"assets" : {
  "small" : "iphone_edgetoedge_portrait_small.png",
  "medium" : "iphone_edgetoedge_portrait_medium.png",
  "large" : "iphone_edgetoedge_portrait_large.png"
},
```

 And again, following the naming convention is recommended. Each ```.png``` image will need to be a size that corresponds with the following devices sizes:

For standard size devices:

| Device        	| Year 	| Size   	| Image Resolution 	|
|-----------------|-------|---------|-------------------|
| iPhone SE     	| 2016 	| small  	| 640 x 1136       	|
| iPhone 8      	| 2017 	| medium 	| 750 x 1334       	|
| iPhone 8 Plus 	| 2017 	| large  	| 1080 x 1920      	|

For edgeToEdge size (aka X-series) devices:

| Device            	| Year 	| Size   	| Image Resolution 	|
|---------------------|-------|---------|-------------------|
| iPhone 11         	| 2019 	| small  	| 828 x 1792       	|
| iPhone 11 Pro     	| 2019 	| medium 	| 1125 x 2436      	|
| iPhone 11 Pro Max 	| 2019 	| large  	| 1242 x 2688      	|

If all you want to do is change the images or colors of an existing skin or one of the "default" templates, at this point you have all the necessary pieces to make your skin, and can skip to the [Finishing the Skin](https://noah978.github.io/Delta-Docs/Skins#finishing-the-skin) section below to learn how to turn these files into an actual ```.deltaskin``` file. However, if you want to customize the button mapping or screen location for your skins, carry on into the next section, **Advanced Mapping.**

# Advanced Mapping

Congratulations, if you have gotten this far in the tutorial, you know enough to make simple modifications of how a skin looks. However, skins offer more than just the ability to switch out images; they also give you full control over exactly where the buttons should go, how big they should be, and also where the game screen itself should be placed. Combining all of these, you can create incredibly different layouts for your skins, or maybe just make the game screen a bit smaller when in landscape mode. The point is, skins were designed to be flexible, and this section will show you how to take advantage of everything!

Before we begin, I need to clarify a few things about the button mappings.
*   Everything on each skin is mapped in **points**. While the actual resolution of an iPhone 8 Plus is ```1080 x 1920```, the logical resolution in **points** is ```414 x 736```.
*   Just like on regular computer display, the y-value starts at the top (y = 0) and gets larger as you move down. Similarly, the x-value starts on the left (x = 0) and gets larger as you move to the right.

Now, lets take a look at those items we skipped over previously: mappingSize, extendedEdges, items, and screens.

### mappingSize

```
"mappingSize" : {
  "width" : 414,
  "height" : 736
},
```

This is the point-based size of your image. In the expanded table below, you can see how mapping size is related to the image resolutions.

| Device 	| Size         	| mappingSize   | Image Resolution 	| Aspect Ratio 	|
|---------|---------------|---------------|-------------------|---------------|
| iPhone 	| Standard     	| 414 x 736     | 1080 x 1920      	| 9 **:** 16   	|
| iPhone 	| EdgeToEdge    | 414 x 896     | 1242 x 2688      	| 9 **:** 19.5 	|
| iPad   	| Standard     	| 768 x 1024    | 2048 x 2732      	| 3 **:** 4     |

Technically you can use any mapping size with the correct aspect ratio, but for the highest quality and precision skins, I recommend you stick to the ones listed above.

# items

Let's take a look at the format of how each button is mapped. Each button is a set of three things inside the items category. Open any button up and you should see this:

```
{
  "inputs": [
    "a"
  ],
  "frame": {
    "x": 313,
    "y": 540,
    "width": 47,
    "height": 47
  },
  "extendedEdges": {
    "top": 0,
    "bottom": 0,
    "left": 0,
    "right": 16
  }
},
```

The inputs will contain the button identifier(s) that you are currently mapping.

Just so you know what each button does, they're each listed below. The more complicated buttons requiring explanation are listed first, then the full list is included in the button charts afterwards.

### dpad

```
"inputs": {
  "up": "up",
  "down": "down",
  "left": "left",
  "right": "right"
},
```

The plus-button-like control usually located on the left side of the skin. Typically, it controls movement in games. Unlike other controls, this control is actually divided up into nine sections: eight control directions, and a center neutral section. However, there aren't nine separate mappings for each section; there's only one for the entire D-Pad. So how does Delta know how to divide up the D-Pad into different sections? Simple, it just divides the button mapping you give it into three equal sections horizontally and three equal sections vertically. Because of this, it is very important that you map the D-Pad exactly as it appears on the skin, and with no extra padding, or else the directions will not exactly match what the user sees. To properly add padding without messing up the mapping, you can take advantage of the extendedEdges property.

### thumbstick

```
"thumbstick": {
  "name": "portrait_thumbstick.pdf",
  "width": 85,
  "height": 87
},
"inputs": {
  "up": "analogStickUp",
  "down": "analogStickDown",
  "left": "analogStickLeft",
  "right": "analogStickRight"
},
```

The thumbstick is typically used for N64 skins, since it's the only system that Delta currently supports that was built with a thumbstick. But you can actually use a thumbstick instead of a dpad on **any** skin! This item includes an additional property, "thumbstick," which contains the name, width and height of a separate thumbstick image which will move around the screen with the user's thumb. Remember to use **points** for the width and height!

### ab

```
"inputs": [
  "ab"
],
```

Some skins may have an AB button. When pressed, this button actually presses both the A and B buttons at once, which can be useful for certain games. Including it is the designers choice.

### menu

```
"inputs": [
  "menu"
],
```

While the Start button typically pauses the game, this pauses the entire emulator, and allows you to access features such as Save States, Cheat Codes, Fast Forward, etc. As always, make sure to map it exactly without padding, since the pause menu that appears relies on the mapping to position itself.

### touchscreen

```
"inputs": [
  "x": "touchScreenX",
  "y": "touchScreenY"
],
```

This one is specific to Nintendo DS. The mapping must be precise so that the finger / stylus will interact with the screen appropriately. It's also worth noting that the extended edges should not be enabled for this item.

### Button Charts

The chart below shows all the buttons compatible to use for each console on Delta.

| Button     | GB(C)   | GBA     | NDS     | NES     | SNES    | N64     |
|------------|---------|---------|---------|---------|---------|---------|
| a          |    ✔   |    ✔    |    ✔   |    ✔    |    ✔    |    ✔    |
| b          |    ✔   |    ✔    |    ✔   |    ✔    |    ✔    |    ✔    |
| ab         |    ✔   |    ✔    |    ✔   |    ✔    |    ✔    |    ✔    |
| x          |         |         |    ✔   |         |    ✔    |         |
| y          |         |         |    ✔   |         |    ✔    |         |
| select     |    ✔   |    ✔    |    ✔   |    ✔    |    ✔    |         |
| start      |    ✔   |    ✔    |    ✔   |    ✔    |    ✔    |    ✔    |
| dpad       |    ✔   |    ✔    |    ✔   |    ✔    |    ✔    |    ✔    |
| cpad       |         |         |         |         |         |    ✔    |
| thumbstick |    ✔   |    ✔    |    ✔   |    ✔    |    ✔    |    ✔    |
| l          |         |    ✔    |    ✔   |         |         |    ✔    |
| r          |         |    ✔    |    ✔   |         |         |    ✔    |
| z          |         |         |         |         |         |    ✔    |

### Custom buttons

The following are all custom buttons similar to the menu button, but unlike the menu button, they are not included in the default skins and activating them will *not* pause the emulator. They work across all systems and utilize different Delta Emulator features.

```
"inputs": [
  "quickSave"
],
```

| Button            | Function                                     |
|-------------------|----------------------------------------------|
| quickSave         | Creates a save state                         |
| quickLoad         | Loads the most recent save state             |
| fastForward       | Fast forward as long as the button is held   |
| toggleFastForward | Turn fast forward on until pressed again     |

It is recommended that you remove any buttons from your skin that do not have an input for the system the skin works with. Otherwise, the user may be confused when tapping a button that doesn't do anything.

## Frame

The frame defines the location of each button in points using x, y, width and height.

Exactly how you find the location and size of the skin buttons may vary, but all Delta skins were mapped by downsizing images to their mapping sizes, opening them in **Photoshop**, and using a combination of masks and the Info window to find the exact pixel locations of each button. Once you find the required information, you can fill in the button mappings for each button (remember that x and y refer the top left of the button location).

# ExtendedEdges

In addition to the extendedEdges item in each button mapping, there is also a orientation-specific extendedEdges item. Each extendedEdges item consists of four sub-items: top, bottom, left, and right. These four items "extend" the edge of a button in that direction by whatever value it has been set to. For example, the A button may have a mapping of:

```
"frame": {
  "x": 15,
  "y": 100,
  "width": 80,
  "height": 80
},
```

However, maybe the orientation-specific extendedEdges has a value of 10 in all directions.

```
"extendedEdges": {
  "top": 10,
  "bottom": 10,
  "left": 10,
  "right": 10
}
```

Using the extendedEdges, the *actual* touch target of the A button would be:

*   x: 5
*   y: 90
*   width: 100
*   height: 100

---

This has two benefits:

1.  It is easier to map buttons, since all you need to worry about is mapping the exact location of the button, and adding the padding later.
2.  This allows padding to be added to the D-Pad and Menu button without messing up the internal calculations Delta uses for each button.

Another reason to use extendedEdges is to ensure the touch targets of buttons near the edges of the screen actually extend to the edge. This is very important, because if you don't do this, it's easy for the user to tap near the edge of the screen but not perform any action due to the touch targets not extending far enough. To make this an easy fix, each button mapping also has its own extendedEdges item, which will **add** to the orientation-specific version if you enter a value for it.

For example, let's take the A button example above. With the orientation-specific extendedEdges, you may notice that it is only 5 points away from the left edge of the screen. To get the best experience out of using your skin, you should make sure it extends all the way to the left edge. To do this, open up the a button mapping, and then open up its own extendedEdges. Once that's opened, set left to 5, and save. Now, the touch target of the A button will be:

*   x: 0
*   y: 90
*   width: 105
*   height: 100

Good, it extends all the way to edge! Per-button extendedEdges can also be applied simply to tweak the extendedEdges of a button. Just remember, map all buttons exactly as they appear on the skin with no padding, and then use extendedEdges to add the padding later.

# screens

The screens category is what Delta uses to display the game screen and what filters to use on it.

### inputFrame

Each Delta core outputs a standard sized frame for the internal resolution of the particular console. For your easy reference, all of the consoles and the full size of their inputFrame is shown below.

| Console                             	| Full inputFrame 	| Aspect Ratio 	|
|---------------------------------------|-------------------|---------------|
| GameBoy (Color)                     	| 160 x 144       	| 10 **:** 9   	|
| GameBoy Advance                     	| 240 x 160       	| 3 **:** 2    	|
| Nintendo DS                         	| 256 x 384       	| 2 **:** 3    	|
| Nintendo Entertainment System       	| 256 x 240       	| 16 **:** 15  	|
| Super Nintendo Entertainment System 	| 256 x 224       	| 8 **:** 7    	|
| Nintendo 64                         	| 256 x 224       	| 8 **:** 7    	|

You should notice that the Nintendo DS only has one full inputFrame but we know that a Nintendo DS has a top and bottom screen. The NDS emulation core outputs the top screen with the bottom screen immediately underneath it. If your skin is just going to display them on top of each other then you can use the full inputFrame to place it onto the skin.

But if you want to separate the screens, you will need to use two different screen items:

```
"screens": [
  {
    "inputFrame": {
      "x": 0,
      "y": 0,
      "width": 256,
      "height": 192
    },
    "outputFrame": {...}
  },
  {
    "inputFrame": {
      "x": 0,
      "y": 192,
      "width": 256,
      "height": 192
    },
    "outputFrame": {...}
  }
],
```

You will use exactly half the height of the full inputFrame for each of the screens. Then the top "y" will be 0 to capture the top screen and you will adjust the "y" to be 192 on the second screen to capture the bottom screen.

### outputFrame

```
"outputFrame": {
  "x": 0,
  "y": 103,
  "width": 320,
  "height": 213
}
```

The outputFrame takes whatever you part of the image you captured with the inputFrame and choose where it appears on your skin. Like with the buttons, this must be mapped using **points**. Please note that it is **strongly** recommended you provide an area with the same aspect ratio as the inputFrame.

## Screen Filters

Delta allows you to use Apple's CoreImage Filters to alter any screen item. You can find the full list of Filters and their parameters on [Apple's Reference page](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Reference/CoreImageFilterReference/index.html).

To apply a filter, you simply need an object with the name of the filter, and then the parameters that the filter requires. Often, a parameter must have one or more attributes of its own, as shown in the example below:

```
"inputFrame": {...},
"outputFrame": {...},
"filters": [
  {
    "name": "CIAffineTransform",
    "parameters": {
      "inputTransform": {
        "rotation": 180
      }
    }
  }
]
```

Note that the inputImage is not required as a parameter since Delta automatically uses the image captured by your inputFrame. Additional examples of Custom Skin filters can be found [here.](https://noah978/github.io/Delta-Docs/Skin-Filter-Examples)

Here are some common examples of parameters that require additional attributes:

For any CIColor:
```
"inputColor": {
  "r": "128",
  "g": "128",
  "b": "128"
}
```

For any CIVector:
```
"inputVector": {
  "x": "120",
  "y": "0"
}
```

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

If you don't want to transfer through iTunes, you can always send it to your device via Email, iMessage, or via downloading through an online file space like Google Drive. Once the file is on your device, "Open In..." Delta.

Once you've imported your custom skin, you can now select it in Delta’s settings under Controller Skins. The last step is to start a game of your choice, and start playing with your creation. Congrats, you worked hard for it!
