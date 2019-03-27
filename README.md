# AutoTouch Document

`Applicable to version 5.0.3 or higher`

> - AutoTouch is a “Macro” tool used to record and playback human touching and pressing on the mobile device.
> - It simulates touching and keys pressing.
> - It runs Lua scripts.
> - It provides several extended functions to achieve automation.
> - It needs Jailbreak environment.
> - It provides a Script Store to sell and buy scripts.

Table of Contents
=================

   * [AutoTouch Document](#autotouch-document)
   * [Table of Contents](#table-of-contents)
   * [Usage](#usage)
      * [How to install?](#how-to-install)
      * [How to use Activator?](#how-to-use-activator)
      * [How to record?](#how-to-record)
      * [How to play script?](#how-to-play-script)
      * [How to set play settings for script?](#how-to-set-play-settings-for-script)
      * [How to take screenshot?](#how-to-take-screenshot)
      * [How to write a script?](#how-to-write-a-script)
      * [How to use the "Function Helper" while script coding?](#how-to-use-the-function-helper-while-script-coding)
      * [How to write and manage scripts on the computer?](#how-to-write-and-manage-scripts-on-the-computer)
      * [How to use Package to orgainize the script project?](#how-to-use-package-to-orgainize-the-script-project)
      * [How to encrypt the scripts?](#how-to-encrypt-the-scripts)
      * [How to sell your script in Script Store?](#how-to-sell-your-script-in-script-store)
      * [How to download and buy scripts from Script Store?](#how-to-download-and-buy-scripts-from-script-store)
      * [How to buy AutoTouch license?](#how-to-buy-autotouch-license)
   * [Script](#script)
      * [Basis](#basis)
      * [Develop Tool](#develop-tool)
      * [Coordinate, Size and Orientation System](#coordinate-size-and-orientation-system)
      * [Extension Functions](#extension-functions)
         * [touchDown(id, x, y)](#touchdownid-x-y)
         * [touchMove(id, x, y)](#touchmoveid-x-y)
         * [touchUp(id, x, y)](#touchupid-x-y)
         * [keyDown(keyType)](#keydownkeytype)
         * [keyUp(keyType)](#keyupkeytype)
         * [getColor(x, y)](#getcolorx-y)
         * [getColors(locations)](#getcolorslocations)
         * [findColor(color, count, region)](#findcolorcolor-count-region)
         * [findColors(colors, count, region)](#findcolorscolors-count-region)
         * [findImage(imagePath, count, fuzzy, ignoreColors, region)](#findimageimagepath-count-fuzzy-ignorecolors-region)
         * [screenshot(filePath, region)](#screenshotfilepath-region)
         * [appRun(appIdentifier)](#apprunappidentifier)
         * [appKill(appIdentifier)](#appkillappidentifier)
         * [appState(appIdentifier)](#appstateappidentifier)
         * [rootDir()](#rootdir)
         * [usleep(microseconds)](#usleepmicroseconds)
         * [log(content)](#logcontent)
         * [alert(message)](#alertmessage)
         * [toast(message, delay)](#toastmessage-delay)
         * [vibrate()](#vibrate)
         * [playAudio(audioFile, times)](#playaudioaudiofile-times)
         * [stopAudio()](#stopaudio)
         * [getOrientation()](#getorientation)
         * [getScreenResolution()](#getscreenresolution)
         * [getSN()](#getsn)
         * [getVersion()](#getversion)
         * [intToRgb(intColor)](#inttorgbintcolor)
         * [rgbToInt(r, g, b)](#rgbtointr-g-b)
         * [copyText(text)](#copytexttext)
         * [clipText()](#cliptext)
         * [inputText(text)](#inputtexttext)
         * [dialog(controls, enableRemember)](#dialogcontrols-enableremember)
         * [clearDialogValues(script)](#cleardialogvaluesscript)
         * [openURL(urlString)](#openurlurlstring)
      * [Constants](#constants)
         * [Types of physical keys](#types-of-physical-keys)
         * [Types of dialog controls](#types-of-dialog-controls)
         * [Types of screen orientations](#types-of-screen-orientations)

# Usage

## How to install?
> - You can search and install AutoTouch in Cydia diredctly, it is released in BigBoss.
> - You can also add the official repo: http://apt.autotouch.net to Cydia and install AutoTouch there.
> - There is also a beta repo: http://beta.autotouch.net which contains more fresh but not so stable packages.

## How to use Activator?
> - By default AutoTouch uses volume decrease button holding or pressing to control everything, untill you install Activator by hand.
> - Add official repo: http://rpetri.ch/repo/ to Cydia.
> - Install Activator form that repo.
> - AutoTouch will automatically detect Activator and use it as the default control method.
> - Customize the actions you want to use to control AutoTouch by Activator.

## How to record?
> - At the interface where you want to start recording , hold volume decrease button (or other main control action set with Activator by youself, this point will not be repeated below) to call out the control panel.
![Control Panel](https://i.imgur.com/Rjx5f1b.png)
> - Press the "Record" button on the control panel to start recording.
> - It will record all your touching and key pressing to a script until you stop it.
> - Hold on volume decrease button (or other Activator action) again to stop the recording.
> - Then, there will be a Lua script named with create time in the script list. You can edit, rename or playback it.

## How to play script?
> - Hold on volume decrease button to call out the control panel.
> - Click the script you want to run.
> - Generally, a dialog for play setting will pop up to determine the repeat times, interval, and speed, unless you've ever set "play diretly" in the play settings for this script  before.
![Play Settings](https://i.imgur.com/Bq0b4PY.png)
> - Press the "Play" button on play settings dialog to play immediately.
> - If you press the "Hold" button, it will enter the "Ready to play" status, in which every time you short press the volume decrease button it will play the script a time. 
> - Hold volume decrease button to forcedly stop the playing, or quit the "Ready to play" status.

## How to set play settings for script?
> - You can set an Activator action to trigger a script diretly.
> - Set "play diretly" to skip the play settings dialog while playing.

## How to take screenshot?
> - Press “Snap” button on the control panel to take screenshot.
> - The screenshot will be saved as BMP image which might be used to speficy parameters of getColors, findColors or findImage.

## How to write a script?
> - Press "+" button on top right of the local script list, choose “Create a script” to open the script editor.
> - Write the code there.
> - Press "save" button to save the script.

## How to use the "Function Helper" while script coding?
> - There are "Extensions", "Indent" and "Statements" buttons on top of the keyboard in the script editor. You can conveniently insert extended functions, indent or common statement of Lua Language.
> - Press the "Extension" button to present the extended functions list, click a function to insert into the script diretly.
> - Press the "HELPER" button on the function list, it will help you to determine the coordinates, colors or key flags for the functions.
> 
>   ![Function Helper](https://i.imgur.com/ng2QWrz.png)

## How to write and manage scripts on the computer?
> - Turn on  Web Server at AutoTouch setting and visit the told URL from browser on computer. Manage scripts there.
> - You can also turn on WebDAV Server and connect the told address with  WebDAV client on computer. 

## How to use Package to orgainize the script project?
> - You can create a Package as script project to contain different scripts, files and images etc. Package must have a main.lua file as the entrance of the execution. A Package in fact is a directory named with .at extension such as xxx.at.
> - Package can be encrypted to xxx.ate which is also execuate-able and can be released to Script Store.

## How to encrypt the scripts?
> - Tap accessory button of a package or script in the local script list, choose "Encrypt".
> - Input the encryption password. Or leave it blank if you don't want one.
> - Press "Confirm" to complete the encryption. A encrypted file with the same name but ended with .lua.e or .ate will be generated in the script list then.
> - You can play the encrypted scripts, or release them to Script Store.

## How to sell your script in Script Store?
> - Visit https://autotouch.net/server/login.php from browser on computer.
> - Complete the details required to create a new script. 
> - Do provide a detailed and beautify html page for that script as the details page, a YouTube video will be much better.
> - Upload a encrypted script or package as a new version to this script.
> - Wait for the approvement.
> - You should setup the Digital Rights Management in the script by yourself, AutoTouch Script Store can not help you by now.

## How to download and buy scripts from Script Store?
> - You can directly download all scripts from the store.
> - You need to contact the author to buy the decription password. Do be careful not to be cheated, AutoTouch can do nothing to protect your money provenly.

## How to buy AutoTouch license?
> - Tap License on AutoTouch settings to enter the license management view.
> - Read the Instructions and do be aware that AutoTouch license has ONE YEAR validity period!
> -  It will automatically activate current device after the payment if you use PayPal (If failed just follow the next step).
> - You can query bought licenses with your PayPal ID email, or any activated device SN.
> - You can activate another device with a license after you query it out.
> - You can also "Activate Current Device" diretly with a license key bought from other devices.
> - You should make sure it shows "License Downloaded" at top-right of the License view after it's activated.
> - It allows only one time activation a day, you may do it again after 24 hours if you need.
![License View](https://i.imgur.com/CB0Fnfm.jpg)


# Script

## Basis
You can learn how to use Lua language from here:《[Lua Official Reference Manual](http://www.lua.org/manual/5.3/)》

## Develop Tool
[LuaStudio](http://luastudio.net/) is aprofessional development environment for debugging Lua script in your applications. It's familiar and fast and you'll wonder how you ever worked without it.

## Coordinate, Size and Orientation System
AutoTouch uses pixel based Native Resolution as the coordinate and size system. Resolutions of different iOS devices are [here](https://developer.apple.com/library/archive/documentation/DeviceInformation/Reference/iOSDeviceCompatibility/Displays/Displays.html), for example, screen size of iPhone X is 1125 x 2436.

Origin point (0, 0) is alwasy at left-top of the **Application Interface**, regardless of the device orientation. Consider only the App interface while using these functions: touchDown,touchMove,touchUp,getColors,findColors,findImage.

![For example](https://i.imgur.com/imDVXXB.png)

## Extension Functions

Extension functions are used to extend Lua language. Thus, the device can simulate some human abilities of operating the mobile phone. Moreover, extension functions also support functions including: screenshot, color searching, color matching, and picture matching.

### touchDown(id, x, y)
> Press the coordinate (x,y) on the screen.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| id    | Integer   |   Finger ID. is used to mark a finger in single-touch or multi-touch. |
| x     |   Float   |   x-coordinate on the screen   |
| y     |    Float    |  y-coordinate on the screen  |

`Return`

None

`Examples`
```lua
-- Press by one finger at coordinate (100,200).
touchDown(0, 100, 200); 

-- Press by three fingers at three locations on the screen.
touchDown(0, 100, 200);
touchDown(1, 200, 300);
touchDown(2, 300, 400);

-- Implement a tap function
function tap(x, y)
    touchDown(0, x, y);
    usleep(16000);
    touchUp(0, x, y);
end

-- Tap at (100, 200)
tap(100, 200);

```

### touchMove(id, x, y)
> Move the finger to coordinate (x,y).

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| id    | Integer   |   Finger ID. is used to mark a finger in single-touch or multi-touch. |
| x     |   Float   |   x-coordinate on the screen   |
| y     |    Float    |  y-coordinate on the screen  |

`Return`

None

`Examples`
```lua
-- Press by one finger at coordinate (100,200) and move the finger to coordinate (200,200).
touchDown(0, 100, 200);
usleep(16000);
touchMove(0, 200, 200);

-- Press by three fingers at three locations on the screen and move to new location.
touchDown(0, 100, 200);
touchDown(1, 200, 300);
touchDown(2, 300, 400);
usleep(16000);
touchMove(0, 150, 250);
touchMove(1, 250, 350);
touchMove(2, 350, 450);

```

### touchUp(id, x, y)
> Lift the finger from coordinate (x,y)

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| id    | Integer   |   Finger ID. is used to mark a finger in single-touch or multi-touch. |
| x     |   Float   |   x-coordinate on the screen   |
| y     |    Float    |  y-coordinate on the screen  |

`Return`

None

`Examples`
```lua
-- Click the screen once by one finger at coordinate (100,200).
touchDown(0, 100, 200);
usleep(16000);
touchUp(0, 100, 200);

-- Press by three fingers at three locations on the screen, move to new location, and then lift the finger.
touchDown(0, 100, 200);
touchDown(1, 200, 300);
touchDown(2, 300, 400);
usleep(16000);
touchMove(0, 150, 250);
touchMove(1, 250, 350);
touchMove(2, 350, 450);
usleep(16000);
touchUp(0, 150, 250);
touchUp(1, 250, 350);
touchUp(2, 350, 450);
```

### keyDown(keyType)
> Simulate the pressing of physical key.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| keyType     |   Integer   |   Physical key identification. Now you can use [these physical keys](#types-of-physical-keys).   |

`Return`

None

`Examples`
```lua
-- Simulate the pressing of Home Key.
keyDown(KEY_TYPE.HOME_BUTTON);

-- How to simulate a key pressing?
function keyPress(keyType)
    keyDown(keyType);
    usleep(10000);
    keyDown(keyUp);
end
keyPress(KEY_TYPE.HOME_BUTTON);

-- How to simulate a screen lock function?
function lockScreen()
    keyDown(KEY_TYPE.POWER_BUTTON);
    keyUp(KEY_TYPE.POWER_BUTTON);
end

-- How to simulate a screen unlock function?
function unlockScreen()
    keyDown(KEY_TYPE.POWER_BUTTON);
    keyUp(KEY_TYPE.POWER_BUTTON);

    usleep(1000000);

    local w, h = getScreenResolution();

    local x = 10;
    local gap = 120;
    touchDown(0, x, 200);
    while x < w do
        x = x + gap;
        usleep(16000);
        touchMove(0, x, 200);
    end
    touchUp(0, x, 200);
end
```

### keyUp(keyType)
> Simulate the lifting of physical key.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| keyType     |   Integer   |   Physical key identification. Now you can use [these physical keys](#types-of-physical-keys).   |

`Return`

None

`Examples`
```lua
-- Simulate the action of pressing and lifting Home Key.
keyDown(KEY_TYPE.HOME_BUTTON);
usleep(10000);
keyUp(KEY_TYPE.HOME_BUTTON);
```

### getColor(x, y)
> Get the color value of the pixel point of the specified coordinate on current screen.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| x     |   Float   |   x-coordinate on the screen   |
| y     |    Float    |  y-coordinate on the screen  |

`Return`

| Return     | Type   |  Specification  |
| -------- | :-----:| ----  |
| color     |   Integer   |   Integer color value of the pixel point   |

`Examples`
```lua
local color = getColor(100, 200)
alert(string.format("Pixel color is :%d", color))
-- Pop up color: 16777215

-- Keep gettting color of a location until it matches a specify color
local color
repeat
   color = getColor(100, 200)
   usleep(50000) -- Wait a while
until( color == 123456 )
-- Continue to do what's next

```

### getColors(locations)
> Get the color values of the pixel points of the specified coordinates on current screen.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| locations     |   table   |   A grouo of coordinates, just as { {x1,y1}, {x2,y2}, {x3,y4} }   |

`Return`

| Return     | Type   |  Specification  |
| -------- | :-----:| ----  |
| colors     |   table   |   Colors gotten with corresponding order.  |

`Examples`
```lua
local result = getColors({ {100, 200}, {200, 300}, {300, 400} });
for i, v in pairs(result) do
    log(string.format("Gotten color:%d", v));
end
```

### findColor(color, count, region)
> Search the coordinates of the pixel points matching the specified color on current screen.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| color     |   Integer   |   Matched color value.   |
| count     |   Integer    | The number refers to how many matched pixel points is found at most. 0 is default setting, which shows all matching points are found. 1 refers to only the first matching pixel point is found. 2 refers to only the first two pixel points are found. The less the number is, the faster the speed is.  |
| region     |   table    | You only search the result in the specified area. This area is the table type including four values {x, y, width, height}. The four values respectively represent the coordinate x, coordinate y, width, and height of the rectangular area. {100,100,200,200} is an example. If you do not want to specify the area, just input nil.  |

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| locations     |   table   |  Coordinates of matched pixel points. For example: { {x1, y1}, {x2, y2}, ... }  |

`Example`
```lua
-- Example 1:
local result = findColor(0x0000ff, 2, nil);
for i, v in pairs(result) do
    log(string.format("Found pixel: x:%f, y:%f", v[1], v[2]));
end

-- Example 2:
local result = findColor(0x00ddff, 0, {100, 50, 200, 200});
for i, v in pairs(result) do
    log(string.format("Found pixel: x:%f, y:%f", v[1], v[2]));
end

-- Example 3:
local region = {100, 50, 200, 200};
local result = findColor(0x00ddff, 0, region);
for i, v in pairs(result) do
    log(string.format("Found pixel: x:%f, y:%f", v[1], v[2]));
end

-- Example 4:
-- Get how many elements does a table have.
function tableLength(T)
  local count = 0
  for _ in pairs(T) do count = count + 1 end
  return count
end

-- Keep finding a speficied color until it's found.
local locations
repeat
   local locations = findColor(0x0000ff, 2, nil);
   usleep(50000) -- Wait a while
until( tableLength(locations) > 0)
-- Log the locations if found
for i, v in pairs(locations) do
    log(string.format("Found pixel: x:%f, y:%f", v[1], v[2]));
end
```

`Internal Implementation`
```lua
function findColor(color, count, region)
    return findColors({ {color,0,0} }, count, region);
end
```

### findColors(colors, count, region)
> Search all rectangular areas matching “specified color and their corresponding location and return the coordinate of the pixel point matching the first color in the rectangular area. This function has the search efficiency and availability far beyond findImage. For example, you need not match the whole key picture, but only match the anchors’ color and their corresponding location on the key. You can specify the number of the results by count parameter. 0 refers to all, 1 refers to the first one, and 2 refers to the first tow. region parameter can specify the search area, which is the table type {x,y,width, height}. You only input nil if no data is specified. 
> This function can use the “auxiliary” tool in the “Extension Function” of the script-editing interface to select the anchors’ colors from the screenshot and get their corresponding location to the function’s parameter automatically.
> The coordinate of the pixel point pointed by the arrow is the coordinate of the return value.

![IMG_0361.PNG-101.9kB](https://i.imgur.com/ODEtwAz.png)

`Parameters`

| Parameter| Type   |  Specification  |
| -------- | :-----:| ----  |
| colors     |   table   |  Include some color and their corresponding location, such as:{ {0x00ddff,0,0}, {0x00eeff,10,10}, {0x0000ff,0,20} }. The small table in the big table includes 3 values: the first is the color value. The second and the third are the corresponding locations of the colors to the first color. The corresponding location of the first color’s table is always (0,0). {0x00ddff,0,0} is an example. The location values of the successive colors are their locations corresponding to the first color. The matched rectangular area can be found on the screen upon these colors and corresponding location relation.  |
| count     |   Integer    | The number refers to how many matched pixel points is found at most. 0 is default setting, which shows all matching points are found. 1 refers to only the first matching pixel point is found. 2 refers to only the first two pixel points are found. The less the number is, the faster the speed is. |
| region     |   table    | You only search the result in the specified area. This area is the table type including four values {x, y, width, height}. The four values respectively represent the coordinate x, coordinate y, width, and height of the rectangular area. {100,100,200,200} is an example. If you do not want to specify the area, just input nil.  |

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| locations     |   table   |  The coordinate of the first color matched in the found rectangular area, including { {x1, y1}, {x2, y2}, ...}  |

`Examples`
```lua
-- Example 1:
local result = findColors({ {0x00ddff,0,0}, {0x00eeff,10,10}, {0x0000ff,0,20} }, 2, nil);
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 2:
local colors = { {0x00ddff,0,0}, {0x00eeff,10,10}, {0x0000ff,0,20} };
local result = findColors(colors, 0, nil);
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 3:
local colors = { {0x00ddff,0,0}, {0x00eeff,10,10}, {0x0000ff,0,20} };
local region = {100, 50, 200, 200};
local result = findColors(colors, 0, region);
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end
```

### findImage(imagePath, count, fuzzy, ignoreColors, region)
> Search the area matched the specified picture on current screen and return the coordinate of the top left corner of all areas by table format.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| imagePath     |   String   |  The path of picture to be searched. From AutoTouch v3.1.1, you need not input complete path here, but only input the location subordinated to AutoTouch file directory, namely, the path of “Local Script”. (you can get the path of the file directory by rootDir function). For example, “images/script.bmp” means “/var/mobile/Library/AutoTouch/Scripts/images/spirit.bmp”. You need not input the complete path.  |
| count     |   Integer    | The number refers to how many matched pixel points is found at most. 0 is default setting, which shows all matching points are found. 1 refers to only the first matching pixel point is found. 2 refers to only the first two pixel points are found. The less the number is, the faster the speed is. |
| fuzzy     |   float    | The floating degree of the search. 1 is default setting and refers to complete matching. 0.5 refers to 50%v of matching. |
| ignoreColors     |   table   | The color value to be ignored in the search is provided by array, such as {0xffffff, 0x2b2b2b}. You can input nil if one. |
| region     |   table    | You only search the result in the specified area. This area is the table type including four values {x, y, width, height}. The four values respectively represent the coordinate x, coordinate y, width, and height of the rectangular area. {100,100,200,200} is an example. If you do not want to specify the area, just input nil. |

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| locations     |   table   |  The array at the coordinate on the top left corner of the matched area: { {x1, y1}, {x2, y2}, ...}  |

`Examples`
```lua
-- Example 1:
local result = findImage("images/spirit.bmp", 5, 1, nil, nil);
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 2:
local result = findImage("images/spirit.bmp", 0, 0.6, nil, nil};
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 3:
local result = findImage("images/spirit.bmp", 0, {0xffffff, 0x2b2b2b}, nil};
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 4:
local imagePath = "images/spirit.bmp";
local region = {100, 50, 200, 200};
local ignoreColors = {0xffffff, 0x2b2b2b};
local result = findImage(imagePath, 1, 0.9, ignoreColors, region};
for i, v in pairs(result) do
    local x = v[1], y = v[2];
    
    log(string.format("Found rect at: x:%f, y:%f", x, y));
    
    -- Click the found location once.
    tap(x, y);
    usleep(16000);
end
```

### screenshot(filePath, region)
> Take a screenshot for the whole screen or specified area and save as BMP format at specified file path.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| filePath     |   string   | The path of screenshot. From AutoTouch v3.1.1, you only input the location subordinated to AutoTouch file directory, namely, the path of “Local Script”. (you can get the path of the file directory by rootDir function). For example, “images/script.bmp” means “/var/mobile/Library/AutoTouch/Scripts/images/spirit.bmp”. You need not input the complete path. |
| region     |   table    | You make a screenshot of the specified area. This area is the table type including four values {x, y, width, height}. The four values respectively represent the coordinate x, coordinate y, width, and height of the rectangular area. {100,100,200,200} is an example. If you do not want to specify the area, just input nil. |

`Return`

None

`Examples`
```lua
-- Take a screenshot of the whole screen and save in the specified location.
screenshot ("images/screenshot1.bmp", nil);

-- Take a screenshot of the specified area and save.        
screenshot ("images/screenshot2.bmp", {100, 100, 200, 200});
```

### appRun(appIdentifier)
> Run specified application.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| appIdentifier     |   string   |  Application identifier, including "com.apple.mobilesafari". |

`Return`

None

`Example`
```lua
-- Run Safari
appRun("com.apple.mobilesafari");
```

### appKill(appIdentifier)
> Kill specified application.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| appIdentifier     |   string   |  Application identifier, including "com.apple.mobilesafari". |

`Return`

None

`Example`
```lua
-- Kill the running Safari
appKill("com.apple.mobilesafari");
```

### appState(appIdentifier)
> Get the running state of the specified application

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| appIdentifier     |   string   |  Application identifier, including "com.apple.mobilesafari". |

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| state     |   string   |  State of Character string type: "NOT RUNNING", "ACTIVATED", "DEACTIVATED"。 |

`Example`
```lua
-- Get the state of Safari.
local state = appState("com.apple.mobilesafari");
alert(string.format("State of Safari: %s", state));
-- Pop up the state of Safari: "ACTIVATED"
```

### rootDir()
> Get the default directory address of the saved script. This is the default saving address of scripts and screenshots: "/var/mobile/Library/AutoTouch/Scripts/".

`Parameters`

None

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| dir     |   string   |  Default directory address of the saved script. |

`Examples`
```lua
local dirPath = rootDir();
alert(dirPath);
-- Popup "/var/mobile/Library/AutoTouch/Scripts/"
```

### usleep(microseconds)
> Sleep several microseconds (1/1000000)

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| microseconds     |   Integer   |  The number of paused microseconds. |

`Return`

None

`Examples`
```lua
-- Sleep 1 second.
usleep(1000000);
```

### log(content)
> Record log, can be seen in the log interface.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| content     |   string   |  The log content to be recorded. |

`Return`

None

`Examples`
```lua
log("play here...");
```

### alert(message)
> Pop up the dialog box to show specified content.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| message     |   string   |  Content to be showed. |

`Return`

None

`Examples`
```lua
alert("Hello World!");
```

### toast(message, delay)
> Show messages with Toast style and delay for some seconds.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| message     |   string   |  Content to be showed. |
| delay     |   integer   |  How long time to keep showing, default is 2 seconds. |

`Return`

None

`Examples`
```lua
toast("Hello I'm a toast!", 5); -- Show message for 5 seconds.
toast("Hello again!"); -- Show message for 2 seconds.
```

### vibrate()
> Vibrate once.。

`Parameters`

None

`Return`

None

`Examples`
```lua
-- Vibrate once.
vibrate();
```

### playAudio(audioFile, times)
> Play audio document at specified location.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| audioFile     |   string   |  Absolute path of audio document. |
| times     |   integer   |  Number of repeated plays. 0 represents infinite repeat. |

`Return`

None

`Examples`
```lua
-- Play audio infinitely.
playAudio("/var/audio.mp3", 0);
```

### stopAudio()
> Stop playing audio.

`Parameters`

None

`Return`

None

`Examples`
```lua
-- Stop playing audio.
stopAudio();
```

### getOrientation()
> Get orientation of the screen. Return the integer value. Please refer to the “Orientation Type of Screen” for specific correspondence relation.

`Parameters`

None

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| orientation     |   Integer   |  Screen orientation may be [these values](#types-of-screen-orientations) |

`示例`
```lua
local o = getOrientation();
alert(string.format("Screen orientation is : %d", 0))
-- Pop up the orientation 2 of the screen, and mark the reversed screen.
```

### getScreenResolution()
> Get screen resolution bese on pixels.

`Parameters`

None

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| width     |   Integer   |  Width of screen resolution. |
| height     |   Integer   |  Height of screen resolution. |

`Examples`
```lua
local w, h = getScreenResolution();
alert(string.format("Resolution of iPhone 6 Plus: width:%d, height:%d", w, h));
-- iPhone 6 Plus’s resolution width is 1242 and resolution height is 2208.
```

### getSN()
> Get Serial Number of the device.

`Parameters`

None

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| SN     |   string   |  Serial Number of the device. |

`Examples`
```lua
local sn = getSN();
alert(string.format("SN is : %s", sn));
-- Popup shows the SN of the device: C15NFK32TWD2
```

### getVersion()
> Get version of AutoTouch.

`Parameters`

None

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| version     |   string   |  Version of AutoTouch. |

`Examples`
```lua
local version = getVersion();
alert(string.format("Current version of AutoTouch is : %s", version));
-- Pop up shows current version of AutoTouch: 3.5.3-4
```

### intToRgb(intColor)
> Transit integer color to independent values of R,G,B.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| intColor   |   Integer   | Integer color value |

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| R   |   Integer   | Red color value. |
| G   |   Integer   | Green color value. |
| B   |   Integer   | Blue color value. |

`Examples`
```lua
local r, g, b = intToRgb(0x2b2b2b);
alert(string.format("R:%d, G:%d, B:%d", r, g, b));
```

### rgbToInt(r, g, b)
> Transit values of R,G,B to integer color value.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| R   |   Integer   | Red color value. |
| G   |   Integer   | Green color value. |
| B   |   Integer   | Blue color value. |

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| intColor   |   Integer   | Integer color value |

`Examples`
```lua
local intColor = rgbToInt(200, 255, 100);
alert(string.format("Int type color: %d", intColor));
```

### copyText(text)
> Copy specified text to clipboard.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| text     |   string   |  Text to be copied. |

`Return`

None

`Examples`
```lua
copyText("This is a copied text!");
```

### clipText()
> Get the text in the clipboard.

`Parameters`

None

`Return`

| Return     | Type  |  Specification  |
| -------- | :-----:| ----  |
| text     |   string   | Text copied in the clipboard. |

`Examples`
```lua
local text = clipText();
alert(text);
-- Popup shows the text to be copied: "This is a copied text!";
```

### inputText(text)
> Input text to the input box selected now. You can delete a character backspace by inputText("\b").

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| text     |   string   |  Text to be input. |

`Return`

None

`Examples`
```lua
inputText("Let's input some text automatically without tapping the keyboard!");
--  Delete 3 character by inputing 3 backspaces.
inputText("\b\b\b"); 
```

### dialog(controls, enableRemember)
> Pop up self-defined dialog box to accept the user input. Please refer to the example for specific usage.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| controls     |   table   | Array of self-defined controls. You can now use [these dialog box controls](#types-of-dialog-controls)  |
| enableRemember     |   boolean | Whether to use the "remember user's input" function. |

`Return`

None

`Examples`
```lua
local label = {type=CONTROLLER_TYPE.LABEL, text="Would you mind to provide some personal informations?"}
local nameInput = {type=CONTROLLER_TYPE.INPUT, title="Name:", key="Name", value="Kevin"}
local positionPicker = {type=CONTROLLER_TYPE.PICKER, title="Position:", key="Position", value="CEO", options={"CEO", "CTO", "CFO", "CXO"}}
local developerSwitch = {type=CONTROLLER_TYPE.SWITCH, title="A Developer:", key="ADeveloper", value=1}

local controls = {label, nameInput, positionPicker, developerSwitch}
local enableRemember = true;

-- Pop up the dialog box. After the popup, the script will suspend for user input until the user click “confirm” or “cancel”.
dialog(controls, enableRemember);

-- Then get the input value of user.
alert(string.format("name:%s, birthday:%s, gender:%d", nameInput.value, positionPicker.value, developerSwitch.value))
```
![3.png-115.9kB](http://static.zybuluo.com/kentkrantz/8vn5hx58pc63o12no1xhst81/3.png)

### clearDialogValues(script)
> Clear the remembered values of the dialog created by the function dialog.

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| script     |   string   | script path. eg. there is a dialog.lua script in the scripts list, use it like this: clearDialogValues("dialog.lua");  |

`Return`

None

`Examples`
```lua
-- There is a dialog.lua script in the scripts list
clearDialogValues("dialog.lua");
```

### openURL(urlString)
> Open url, or open other apps' url scheme. Look at [Always-Updated List of iOS App URL Scheme Names](https://ios.gadgethacks.com/news/always-updated-list-ios-app-url-scheme-names-0184033/) and example: [Google Maps URL Scheme for iOS](https://developers.google.com/maps/documentation/urls/ios-urlscheme)

`Parameters`

| Parameter     | Type   |  Specification  |
| -------- | :-----:| ----  |
| urlString     |   string   |  Target to open. |

`Return`

None

`Examples`
```lua
openURL("https://autotouch.net")
openURL("prefs:root=General&path=About")
openURL("musics://")
openURL("itms-apps://itunes.apple.com")
openURL("tel://+1123456")
openURL("clashofclans://")
```

## Constants

<a name="types-of-physical-keys"></a>
### Types of physical keys

| Value     |  Specification  |
| -------- | ----  |
| KEY_TYPE.HOME_BUTTON | Home Button |
| KEY_TYPE.VOLUME_DOWN_BUTTON | Volume – Button |
| KEY_TYPE.VOLUME_UP_BUTTON | Volume + Button |
| KEY_TYPE.POWER_BUTTON | Power Button |

<a name="types-of-dialog-controls"></a>
### Types of dialog controls

| Value     |  Specification  |
| -------- | ----  |
| CONTROLLER_TYPE.LABEL | Text label |
| CONTROLLER_TYPE.INPUT | Input box |
| CONTROLLER_TYPE.PICKER | Picker |
| CONTROLLER_TYPE.SWITCH | Switch |

<a name="types-of-screen-orientations"></a>
### Types of screen orientations

| Value     |  Specification  |
| -------- | ----  |
| ORIENTATION_TYPE.UNKNOWN   | Unknown orientation. Practical value is 0. |
| ORIENTATION_TYPE.PORTRAIT | Portrait screen. Home button is at the bottom. Practical value is 1. |
| ORIENTATION_TYPE.PORTRAIT_UPSIDE_DOWN | Upside-down portrait screen. Home button on the top. Practical value is 2. |
| ORIENTATION_TYPE.LANDSCAPE_LEFT | Landscape left screen. Home Key is in the left. Practical value is 3. |
| ORIENTATION_TYPE.LANDSCAPE_RIGHT | Landscape right screen. Home key is in the right. Practical value is 4. |