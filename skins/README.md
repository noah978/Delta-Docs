# Delta Custom Skins

#### ⚠️ Warning ⚠️

Be aware that the properties of Delta Skins may change over time. Please report any errors in this tutorial by creating a [new issue.](https://github.com/noah978/Delta-Docs/issues/new/choose)

Delta Emulator was designed with the purpose of allowing custom skins to be produced _by anyone_. This allows everyone to create their own skins for either functionality or creativity. Please read on if you are interested in making your own skin or just want to know how Delta’s custom skins work.

### Download Templates <a id="download-templates"></a>

The following links will allow you to directly download each of the default skins for each of the systems Delta supports. It is advisable for beginners to base their skin off of the existing templates. You can download them individually or in one zip file if you plan on making skins for various systems.

* [NES](https://github.com/rileytestut/NESDeltaCore/raw/master/NESDeltaCore/Controller%20Skin/Standard.deltaskin)
* [SNES](https://github.com/rileytestut/SNESDeltaCore/raw/master/SNESDeltaCore/Controller%20Skin/Standard.deltaskin)
* [N64](https://github.com/rileytestut/N64DeltaCore/raw/master/N64DeltaCore/Controller%20Skin/Standard.deltaskin)
* [GBC](https://github.com/rileytestut/GBCDeltaCore/raw/master/GBCDeltaCore/Controller%20Skin/Standard.deltaskin)
* [GBA](https://github.com/rileytestut/GBADeltaCore/raw/master/GBADeltaCore/Controller%20Skin/Standard.deltaskin)
* [NDS](https://github.com/rileytestut/MelonDSDeltaCore/raw/master/MelonDSDeltaCore/Controller%20Skin/Standard.deltaskin)
* [Download All](https://noah978.github.io/Delta-Docs/assets/all-skins.zip)

#### Looking for inspiration? <a id="looking-for-inspiration"></a>

Check out some of the skins other people have made at one of the following sites:

<!--* [DELTASKINS](http://deltaskins.us/) site is no longer active -->
* [Skins4Delta](https://skins4delta.com/)
* [Delta Skins](https://delta-skins.github.io/)
* [Circa’s Delta Skins](https://circa.im/emu/delta/skins/)
* [LitRitt Designs](https://litritt.gitbook.io/designs/)

Skins4Delta also offers a [Skin Generator](https://generator.skins4delta.com/) that can take whatever image you want and apply that to the background of their default skin! While the capabilities are not infinite, you can still make your very own skin in seconds.

The [r/Delta\_Emulator](https://reddit.com/r/Delta_Emulator) subreddit also has an active [Discord Server](https://discord.gg/ERssHqy) that will sometimes take skin requests.

## Skin Basics <a id="skin-basics"></a>

All delta skins are contained in `.deltaskin` files, for example, all the default skins included with Delta are named `Standard.deltaskin`. These are actually just `.zip` files with the extension renamed. So if you change the extension name from `.deltaskin` to `.zip`, you can now access the files contained within. These files should include images of different sizes and orientations which have a `.pdf` extension and a single `info.json` file.

On macOS, select the `.json` and all `.pdf` files, right-click and select `Compress`, then use `Get Info` to manually change the extension from `.zip` to `.deltaskin`, and select `Use .deltaskin`. Compressing a folder containing the files instead of compressing within the folder will lead to 'This file is invalid'.

#### 🔥 Lit Tip 🔥

Instead of changing the file extension to compress and decompress the skin files, you can set the `.deltaskin` file type to be in opened in the [7-Zip](https://www.7-zip.org/download.html) File Manager. Doing so will allow you to open the skin and drag edited files into it to quickly overwrite changes. You can also use these [Shortcuts](https://litritt.gitbook.io/designs/Graphics/Shortcuts) to more easily access `.deltaskin` files from iOS devices.

The `info.json` contains all the necessary information for a skin to function properly. This information includes:

* Skin Name
* Skin Identifier
* Game Type Identifier
* Image Names
* Button Mappings
* Screen Mappings
* Whether landscape supports opacity
* Whether the skin should be displayed in debug mode

\(Don’t worry if you’re already confused, all of these will be explained further in this tutorial.\)

As you can tell from the extension, this file is a JSON file. Although JSON files are primarily used by web services to transfer data, it was chosen to be used in delta skin files due to its simplicity. Everything in this tutorial can be done via the included text editor on your computer, but it’s strongly recommended you use an application designed to open and edit JSON files, as this is much less error-prone \(and easy!\).

* For Mac, Cocoa JSON Editor was used to make the JSON files for the included default skins, but any other JSON editor will work fine.
* For Windows, using an online editor is probably easiest but a powerful text editor like Atom, Sublime Text, or Coda will work as well.
* For iOS, the Jayson Editor is a good app for visually browsing a JSON file, and the Koder app works as a text-based editor.

While working with a JSON file, it’s suggested that you close all braces and brackets \(using the arrows normally found on the left side of the JSON editor for the purpose of readability. If you aren’t using an editor that detects correct JSON formatting, I recommend uploading your edited JSON file to [jsonlint.com](https://jsonlint.com/) to check for syntax errors.

### The info.json <a id="the-info.json"></a>

Open up the `info.json` file and you should see these five items.

```json
{
  "name" : "Standard N64",
  "identifier" : "com.delta.n64.standard",
  "gameTypeIdentifier" : "com.rileytestut.delta.game.n64",
  "debug" : false,
  "representations" : {...}
}
```

Each one will be explained further below.

#### name <a id="name"></a>

This item is rather self-explanatory, this is what the skin will be called within Delta’s skin selection menu. Replace the name with whatever you would like to name your skin.

#### identifier <a id="identifier"></a>

This is how Delta internally uses and stores skin files. To ensure that one skin doesn’t overwrite another skin, each skin identifier should be unique. The default Delta skins have the identifier `com.delta.console.standard`. While these can technically be set to any unique value, it is recommended that you follow Apple’s reverse-dns format for this to ensure it is unique. Your identifier will look like the following: `com.yourname.console.skinname`. Be sure to include the console if you plan to release the same skin for multiple consoles.

#### gameTypeIdentifier <a id="gametypeidentifier"></a>

This is how Delta further determines the compatibility of each skin. Unlike the identifier, each gameTypeIdentifier needs to remain the same for Delta to identify which system the skin belongs to. Use the following table to decide which identifier you need to use.

| Console / System | gameTypeIdentifier |
| :--- | :--- |
| GameBoy \(Color\) | com.rileytestut.delta.game.gbc |
| GameBoy Advance | com.rileytestut.delta.game.gba |
| Nintendo DS | com.rileytestut.delta.game.ds |
| Nintendo Entertainment System | com.rileytestut.delta.game.nes |
| Super Nintendo Entertainment System | com.rileytestut.delta.game.snes |
| Nintendo 64 | com.rileytestut.delta.game.n64 |
| Sega Genesis (Beta) | com.rileytestut.delta.game.genesis |

#### debug <a id="debug"></a>

This determines whether the skin should be displayed in “debug mode.” By default this is set to false, but when set to true, Delta will overlay red squares on top of where the buttons are mapped to. It’s recommended that you set this to true while making your skin, so that you can see when the buttons can match up nicely with the image.

![Debug Mode Enabled](/assets/example-skin-debug-enabled.png)

In future versions of Delta this property will likely be removed in favor of including a debug skin option within Delta's settings.

#### representations <a id="representations"></a>

```json
"representations" : {
  "iphone" : {...},
  "ipad" : {...}
}
```

Within the representations, you will find two bracketed categories called `iphone` and `ipad`. In the following section, we will be focusing on what you need to know to make new images and change out the old ones.

### Changing the Images <a id="changing-the-images"></a>

Almost every time you create or modify a skin, you’ll be changing the images that are displayed when actually using the skin. Luckily, changing the images is rather straightforward!

Inside the iphone representation, you’ll see two more categories:

```json
"iphone" : {
  "standard" : {...},
  "edgeToEdge" : {...}
}
```

`standard` contains the details for skins that support regular-size iPhones. `edgeToEdge` gives the skin support for all X-series devices with the taller screen size. You don’t have to include both categories and the skin should still work correctly for the iPhones of the chosen variety.

Delta also detects what orientations are supported in a skin by the presence of the portrait and landscape items in the `info.json` file.

```json
"edgeToEdge" : {
  "portrait" : {...},
  "landscape" : {...}
}
```

If you wanted to have a portrait-only skin, you’d need to delete the landscape item; similarly, if you wanted to have a landscape-only skin, you’d need to delete the portrait item. Of course, if you wanted to support both orientations, you don’t need to delete either.

Inside the ipad representation, You'll also find two categories. However, instead of supporting different device types, ipad supports normal `standard` skins as well as `splitView` skins. These are displayed at the bottom of the screen like a keyboard during iPad multitasking, such as Split View, Slide Over, and Stage Manager.

```json
"ipad" : {
  "standard" : {...},
  "splitView" : {...}
}
```

The following items can all be used within **both** the `standard` and `edgeToEdge` categories:

```json
"portrait" : {
  "assets" : {...},
  "items" : [...],
  "screens" : [...],
  "mappingSize" : {...},
  "extendedEdges" : {...},
  "translucent" : false
}
```

`splitView` also supports all the same items. Note that the `screens` item is **not** needed, but works when included.

For the purposes of this section, we will only focus on the `translucent` and `assets` items.

#### translucent <a id="translucent"></a>

You can determine whether the orientation you’re editing should support Delta’s customizable opacity feature. Typically, only landscape skins that go on top of the game screen support this feature, but there’s nothing stopping you from enabling it on portrait skins or disabling it for your own landscape overlay skin. To enable this feature, set the value to true. If you want to disable this feature, set it to false, or delete it entirely.

#### assets <a id="assets"></a>

The assets section is used to load the controller skin images. There are two ways you can create your images:

1. Using PDF files which Delta can automatically resize for each device,
2. Or using PNG files which you will want three different sizes to support each device.

**Using PDFs**

```json
"assets" : {
  "resizable" : "iphone_edgetoedge_portrait.pdf"
},
```

The example above is named in this style: `device_size_orientation.pdf` and we **strongly** recommend that you name your images in a similar naming convention. But you can change the names of your images to any unique name as long as your `info.json` file reflects that name.

Below is a table that displays the correct aspect ratio and recommended image resolution of your PDFs:

| Device | Size | Image Resolution | Aspect Ratio |
| :--- | :--- | :--- | :--- |
| iPhone | Standard | 1080 x 1920 | 9 **:** 16 |
| iPhone | EdgeToEdge | 1242 x 2688 | 9 **:** 19.5 |
| iPad | Standard | 2048 x 2732 | 3 **:** 4 |

**Using PNGs**

If you’d rather use `.png` images, it will require a little more work. You will need to have three differently sized images instead: small, medium, and large. When writing them in the JSON file it will look like this:

```json
"assets" : {
  "small" : "iphone_edgetoedge_portrait_small.png",
  "medium" : "iphone_edgetoedge_portrait_medium.png",
  "large" : "iphone_edgetoedge_portrait_large.png"
},
```

And again, following the naming convention is recommended. Each `.png` image will need to be a size that corresponds with the following devices sizes:

For standard size devices:

| Device | Year | Size | Image Resolution |
| :--- | :--- | :--- | :--- |
| iPhone SE | 2016 | small | 640 x 1136 |
| iPhone 8 | 2017 | medium | 750 x 1334 |
| iPhone 8 Plus | 2017 | large | 1080 x 1920 |

For edgeToEdge size \(aka X-series\) devices:

| Device | Year | Size | Image Resolution |
| :--- | :--- | :--- | :--- |
| iPhone 11 | 2019 | small | 828 x 1792 |
| iPhone 11 Pro | 2019 | medium | 1125 x 2436 |
| iPhone 11 Pro Max | 2019 | large | 1242 x 2688 |

I would also highly recommend the following website that [catalogues all the iOS device sizes.](https://iosref.com/res)

If all you want to do is change the images or colors of an existing skin or one of the “default” templates, at this point you have all the necessary pieces to make your skin, and can skip to the [Finishing the Skin](/skins#finishing-the-skin) section below to learn how to turn these files into an actual `.deltaskin` file. However, if you want to customize the button mapping or screen location for your skins, carry on into the next section, **Advanced Mapping.**

## Advanced Mapping <a id="advanced-mapping"></a>

Congratulations, if you have gotten this far in the tutorial, you know enough to make simple modifications of how a skin looks. However, skins offer more than just the ability to switch out images; they also give you full control over exactly where the buttons should go, how big they should be, and also where the game screen itself should be placed. Combining all of these, you can create incredibly different layouts for your skins, or maybe just make the game screen a bit smaller when in landscape mode. The point is, skins were designed to be flexible, and this section will show you how to take advantage of everything!

Before we begin, I need to clarify a few things about the button mappings.

* Everything on each skin is mapped in **points**. While the actual resolution of an iPhone 11 Pro is `1125 x 2436`, the logical resolution in **points** is `414 x 896`.
  * You may also find it helpful to know that the "notch" on edgeToEdge devices extends 33 **points** from the top of the device.
* Just like on regular computer display, the y-value starts at the top \(y = 0\) and gets larger as you move down. Similarly, the x-value starts on the left \(x = 0\) and gets larger as you move to the right.

Now, lets take a look at those items we skipped over previously: mappingSize, extendedEdges, items, and screens.

### Mapping Size <a id="mapping-size"></a>

```json
"mappingSize" : {
  "width" : 414,
  "height" : 736
},
```

This is the point-based size of your image. In the expanded table below, you can see how mapping size is related to the image resolutions.

| Device | Size | mappingSize | Image Resolution | Aspect Ratio |
| :--- | :--- | :--- | :--- | :--- |
| iPhone | Standard | 414 x 736 | 1080 x 1920 | 9 **:** 16 |
| iPhone | EdgeToEdge | 414 x 896 | 1242 x 2688 | 9 **:** 19.5 |
| iPad | Standard | 768 x 1024 | 2048 x 2732 | 3 **:** 4 |

Technically you can use any mapping size with the correct aspect ratio, but to make skins with the highest quality and precision, I recommend you stick to the ones listed above.

For iPad `splitView` it is recommended to use 768 for the portrait mapping width and 1024 for the landscape mapping width. The height will depend on your skin, and a shorter height will mean less multitasking content being covered up.

### Extended Edges <a id="extended-edges"></a>

In addition to the orientation-specific `extendedEdges`, there is also an `extendedEdges` in each button mapping that overrides these values. Each `extendedEdges` consists of up to four sub-items: `top`, `bottom`, `left`, and `right`. These four sub-items “extend” the edge of a touch target of a button in that direction by whatever value it has been set to.

For example, the A button may have a mapping of:

```json
"inputs": {
  "a"
}
"frame": {
  "x": 15,
  "y": 100,
  "width": 80,
  "height": 80
},
"extendedEdges": {...}
```

However, the orientation-specific `extendedEdges` has a value of 10 in all directions.

```json
"portrait" : {
  "assets" : {...},
  "items" : [...],
  "screens" : [...],
  "mappingSize" : {...},
  "extendedEdges": {
    "top": 10,
    "bottom": 10,
    "left": 10,
    "right": 10
  }
}
```

Using these values, the _actual_ touch target of the A button would be:

* x: 5
* y: 90
* width: 100
* height: 100

This has two benefits:

1. It is easier to map buttons, since all you need to worry about is mapping the exact location of the button, and adding the padding later.
2. This allows padding to be added to the D-Pad and thumbsticks without messing up the internal calculations Delta uses for each button.

Another reason to use `extendedEdges` is to ensure the touch targets of buttons near the edges of the screen actually extend to the edge. This is very important, because if you don’t do this, it’s easy for the user to tap near the edge of the screen but not perform any action due to the touch targets not extending far enough. To make this an easy fix, each button mapping also has its own `extendedEdges` item, which will **override** the orientation-specific version if you enter a value for it.

For example, let’s take the A button example above. With the orientation-specific `extendedEdges`, you may notice that it is only 5 points away from the right edge of the screen. To get the best experience out of using your skin, you should make sure it extends all the way to the right edge. To do this, open up the button mapping, and then open up its own `extendedEdges`. Once that’s opened, set left to 15, and save. Now, the touch target of the A button will be:

* x: 0
* y: 90
* width: 105
* height: 100

Good, it extends all the way to edge! Per-button `extendedEdges` can also be applied simply to tweak the `extendedEdges` of a button. Just remember, map all buttons exactly as they appear on the skin with no padding, and then use `extendedEdges` to add the padding later.

### The Buttons <a id="items"></a>

Let’s take a look a closer look at the format of how each button is mapped. Each button is a set of three things inside the `items` category. Open any button up and you should see this:

```json
"items": [
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
  }
],
```

You should already know how the [extendedEdges](/skins#extended-edges) works, so next up we'll cover the `frame` and then the various `inputs` you can use.

#### frame <a id="frame"></a>

The `frame` defines the location of each button in points using `x`, `y`, `width` and `height`.

Exactly how you find the location and size of the skin buttons may vary, but all Delta skins were mapped by downsizing images to their mapping sizes, opening them in **Photoshop**, and using a combination of masks and the Info window to find the exact pixel locations of each button. Once you find the required information, you can fill in the button mappings for each button \(remember that x and y refer the top left of the button location\).

#### inputs <a id="inputs"></a>

The inputs will contain the button identifier\(s\) that you are currently mapping.

Just so you know what each button does, they’re each listed below. The more complicated buttons requiring explanation are listed first, then the full list is included in the [button charts](/skins#button-charts) afterwards. Take note that the more complex buttons like `dpad` and `thumbstick` use a **dictionary** with keys instead of the normal **list** of button identifiers.

#### D-Pad <a id="d-pad"></a>

```json
"inputs": {
  "up": "up",
  "down": "down",
  "left": "left",
  "right": "right"
},
```

The plus-button-like control usually located on the left side of the skin. Typically, it controls movement in games. Unlike other controls, this control is actually divided up into nine sections: eight control directions, and a center neutral section. However, there aren’t nine separate mappings for each section; there’s only one for the entire D-Pad. So how does Delta know how to divide up the D-Pad into different sections? Simple, it just divides the button mapping you give it into three equal sections horizontally and three equal sections vertically. Because of this, it is very important that you map the D-Pad exactly as it appears on the skin, and with no extra padding, or else the directions will not exactly match what the user sees. To properly add padding without messing up the mapping, you can take advantage of the `extendedEdges` property.

#### Thumbstick <a id="thumbstick"></a>

```json
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

The thumbstick is typically used for N64 skins, since it’s the only system that Delta currently supports that was built with a thumbstick. But you can actually use a thumbstick instead of a D-Pad on **any** skin! This item includes an additional property, “thumbstick,” which contains the `name`, `width` and `height` of a separate thumbstick image which will move around the screen with the user’s thumb. Remember to use **points** for the `width` and `height`!

#### 🔥 Lit Tip 🔥

Within the `inputs` section of both dpads and thumbsticks, you can specify inputs other than direction ones. Since the corners of the input activate 2 buttons at once, this can be useful for creating interesting and unique buttons combos for niche games. The example below demonstrates using a dpad made of a, b, x, and y.

```json
"inputs": {
  "up": "x",
  "down": "b",
  "left": "y",
  "right": "a"
},
```

#### Touch Screen <a id="touch-screen"></a>

```json
"inputs": {
  "x": "touchScreenX",
  "y": "touchScreenY"
},
```

This one is specific to Nintendo DS. The mapping must be precise so that the finger / stylus will interact with the screen appropriately \(it should be identical to the lower screen's `outputFrame` in the [screens](/skins#game-screens) property\). It’s also worth noting that `extendedEdges` **should** be included for this item with a value of **0** for each to override the orientation-specific values.

#### menu <a id="menu"></a>

While the Start button typically pauses the game, this pauses the entire emulator, and allows you to access features such as Save States, Cheat Codes, Fast Forward, etc. As always, make sure to map it exactly without padding, since the pause menu that appears relies on the mapping to position itself.

### Button Charts <a id="button-charts"></a>

The chart below shows all the buttons compatible to use for each console on Delta.

| Button | GB\(C\) | GBA | NDS | NES | SNES | N64 | SG |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| a | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| b | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| c |  |  |  |  |  |  | ✔ |
| x |  |  | ✔ |  | ✔ |  | ✔ |
| y |  |  | ✔ |  | ✔ |  | ✔ |
| select | ✔ | ✔ | ✔ | ✔ | ✔ |  |
| start | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| mode |  |  |  |  |  |  | ✔ |
| dpad | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| cUp |  |  |  |  |  | ✔ |  |
| cDown |  |  |  |  |  | ✔ |  |
| cLeft |  |  |  |  |  | ✔ |  |
| cRight |  |  |  |  |  | ✔ |  |
| thumbstick | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| l |  | ✔ | ✔ |  | ✔ | ✔ |  |
| r |  | ✔ | ✔ |  | ✔ | ✔ |  |
| z |  |  |  |  |  | ✔ | ✔ |

#### Custom Buttons <a id="custom-buttons"></a>

The following are all custom buttons similar to the menu button, but unlike the menu button, they are not included in the default skins and activating them will _not_ pause the emulator. They work across all systems and utilize different Delta Emulator features.

```json
"inputs": [
  "quickSave"
],
```

| Button | Function |
| :--- | :--- |
| quickSave | Creates a save state |
| quickLoad | Loads the most recent save state |
| fastForward | Fast forward as long as the button is held |
| toggleFastForward | Turn fast forward on until pressed again |

It is recommended that you remove any buttons from your skin that do not have an input for the system the skin works with. Otherwise, the user may be confused when tapping a button that doesn’t do anything.

#### Using Multiple Inputs

Say for example, you need to be able to press both the A button and the B button at the same time. It's a lot easier to do this on a physical controller than using touch controls. To conquer this issue, you can create buttons that use multiple inputs! Simply list 2 or more regular buttons in the inputs property. The following example can be used as a soft reset combo in the GameBoy Pokemon games:

```json
"inputs": [
  "a",
  "b",
  "start",
  "select"
],
```

### Game Screens <a id="game-screens"></a>

The `screens` category is what Delta uses to display the game screen\(s\) and what filters to use on it.

#### inputFrame <a id="inputframe"></a>

Each Delta emulation core outputs a standard sized frame for the internal resolution of the particular console. For your easy reference, all of the consoles and the full size of their `inputFrame` is shown below. The `inputFrame` property can also be omitted in which case Delta will just select the full screen output.

| Console | Full inputFrame | Aspect Ratio |
| :--- | :--- | :--- |
| GameBoy \(Color\) | 160 x 144 | 10 **:** 9 |
| GameBoy Advance | 240 x 160 | 3 **:** 2 |
| Nintendo DS | 256 x 384 | 2 **:** 3 |
| Nintendo Entertainment System | 256 x 240 | 16 **:** 15 |
| Super Nintendo Entertainment System | 256 x 224 | 8 **:** 7 |
| Nintendo 64 | 256 x 224 | 8 **:** 7 |
| Sega Genesis | 320 x 224<br>256 x 224<br>320 x 240 (a few PAL games) | 10 **:** 7<br>8 **:** 7<br>4 **:** 3 |

You should notice that the Nintendo DS only has one full `inputFrame` but we know that a Nintendo DS has a top and bottom screen. The NDS emulation core outputs the top screen with the bottom screen immediately underneath it. If your skin is just going to display them on top of each other then you can use one screen with the full `inputFrame` to place it onto the skin.

But if you want to separate the screens, you will need to use two different screen items:

```json
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

You will use exactly half the height of the full `inputFrame` for each of the screens. Then the top `y` will be 0 to capture the top screen and you will adjust the `y` to be 192 on the second screen to capture the bottom screen.

Note about SEGA Genesis: currently the `inputFrame` is not supported since there are so a many different out put sizes. Simply omit the `inputFrame` and specify only the `outputFrame` if you would like to specify a location on the skin. Changes to the way skins handle systems with varying output sizes will come in the future.

#### outputFrame <a id="outputframe"></a>

```json
"outputFrame": {
  "x": 0,
  "y": 103,
  "width": 320,
  "height": 213
}
```

The `outputFrame` takes whatever you part of the image you captured with the `inputFrame` and choose where it appears on your skin. Like with the buttons, this must be mapped using **points**. Please note that it is **strongly** recommended you provide an area with the same aspect ratio as the `inputFrame`.

### Screen Filters <a id="screen-filters"></a>

Delta allows you to use Apple’s CoreImage Filters to alter any screen item. You can find the full list of filters and their parameters on [Apple’s Reference page](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Reference/CoreImageFilterReference/index.html).

To apply a filter, you simply need an object with the name of the filter, and then the parameters that the filter requires. Often, a parameter must have one or more attributes of its own, as shown in the example below:

```json
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

Note that the `inputImage` is not required as a parameter since Delta automatically uses the image captured by your `inputFrame`. Additional examples of Custom Skin filters can be found [here.](filter-examples.md)

Here are some common examples of parameters that require additional attributes:

For any CIColor:

```json
"inputColor": {
  "r": 128,
  "g": 128,
  "b": 128
}
```

For any CIVector:

```json
"inputVector": {
  "x": 120,
  "y": 0
}
```

For any CIRectangle:

```json
"inputRectangle": {
  "x": 20,
  "y": 0,
  "width": 50,
  "height": 50
}
```

## Finishing the Skin <a id="finishing-the-skin"></a>

At this point, you have everything you need to convert the files into a skin file you can start using in Delta! Now, the last thing to do is to actually import it into Delta, which thankfully is the easiest part.

As you learned previously, every `.deltaskin` file is just a zip file with the `.zip` extension renamed. That means, to turn your files into a skin file, all you need to do is compress all the individual files into one zip file and rename the extension `.deltaskin`.

Please take note that:

* When compressing the files, make sure to compress **only** the files themselves, and not the containing folder. If you zip the folder and not the files directly, Delta will not be able to extract the files correctly upon import, which will prevent the skin file from being used.
* When renaming the extension, make sure the extension actually changes. Sometimes, the file may look like its extension was changed, but the computer might have \(invisibly\) added the extension back on the end of the filename. On a Mac, the best way to ensure the extension changes properly is to right-click the file, click Get Info, and then change the extension there.

Once you have your `.deltaskin` file, you need to import it into Delta. If you’re working at your computer, generally the easiest way to do this is via iTunes. To import via iTunes, you can follow these instructions:

1. Connect your iOS device to your computer.
2. Open iTunes.
3. Click on your device that appears in the top left corner.
4. Click the Apps tab near the top of the iTunes window.
5. Scroll down to File Sharing.
6. Click Delta, then drag the skin file into Delta.
7. Launch Delta on your device, hit the plus sign on the top right, and select import from iTunes.

If you don’t want to transfer through iTunes, you can always send it to your device via Email, iMessage, or via downloading through an online file space like Google Drive. Once the file is on your device, “Open In…” Delta.

Once you’ve imported your custom skin, you can now select it in Delta’s settings under Controller Skins. The last step is to start a game of your choice, and start playing with your creation. Congrats, you worked hard for it!
