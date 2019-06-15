# AutoTouch 文档

`该文档适用于5.1.2-7或以上版本`

> - AutoTouch是一个用来录制和回放触摸操作的“宏”工具。
> - 它可以模拟手指在屏幕上的触摸操作，和按键操作。
> - 它可以运行Lua脚本。
> - 它提供了一系列扩展函数来支撑你实现各种自动化。
> - 它需要在越狱环境下使用。
> - 它提供了一个脚本市场供您购买或出售脚本。

### [English Document](/)

### [常见问题与答案](/zh-Hans/QA)

目录
=================

   * [用法](#用法)
      * [怎样安装？](#怎样安装)
      * [怎样使用Activator?](#怎样使用activator)
      * [怎样录制?](#怎样录制)
      * [怎样播放？](#怎样播放)
      * [怎样截屏?](#怎样截屏)
      * [怎样写一个脚本](#怎样写一个脚本)
      * [怎样在编辑脚本时使用函数“帮助”来方便地插入函数和参数？](#怎样在编辑脚本时使用函数帮助来方便地插入函数和参数)
      * [怎样在电脑上编写和管理脚本？](#怎样在电脑上编写和管理脚本)
      * [怎样创建一个脚本Package项目?](#怎样创建一个脚本package项目)
      * [怎样加密脚本？](#怎样加密脚本)
      * [怎样发布脚本到商城？](#怎样发布脚本到商城)
      * [怎样从商城下载和购买脚本？](#怎样从商城下载和购买脚本)
      * [怎样购买授权？](#怎样购买授权)
   * [脚本](#脚本)
      * [基础](#基础)
      * [开发工具](#开发工具)
      * [Coordinate, Size and Orientation System](#coordinate-size-and-orientation-system)
      * [扩展库](#扩展库)
         * [LuaCURL](#luacurl)
         * [LuaSocket](#luasocket)
         * [LuaSec](#luasec)
         * [LuaSqlite3](#luasqlite3)
         * [json.lua](#jsonlua)
         * [Plist](#plist)
         * [Penlight](#penlight)
         * [LuaFileSystem](#luafilesystem)
         * [WebSocket](#websocket)
      * [扩展函数](#扩展函数)
         * [touchDown(id, x, y)](#touchdownid-x-y)
         * [touchMove(id, x, y)](#touchmoveid-x-y)
         * [touchUp(id, x, y)](#touchupid-x-y)
         * [keyDown(keyType)](#keydownkeytype)
         * [keyUp(keyType)](#keyupkeytype)
         * [getColor(x, y)](#getcolorx-y)
         * [getColors(locations)](#getcolorslocations)
         * [findColor(color, count, region, debug)](#findcolorcolor-count-region-debug)
         * [findColors(colors, count, region, debug)](#findcolorscolors-count-region-debug)
         * [findImage(targetImagePath, count, threshold, region, debug, method)](#findimagetargetimagepath-count-threshold-region-debug-method)
         * [screenshot(filePath, region)](#screenshotfilepath-region)
         * [appRun(appIdentifier)](#apprunappidentifier)
         * [appKill(appIdentifier)](#appkillappidentifier)
         * [appState(appIdentifier)](#appstateappidentifier)
         * [rootDir()](#rootdir)
         * [currentPath()](#currentpath)
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
         * [frontMostAppId()](#frontmostappid)
         * [frontMostAppOrientation()](#frontmostapporientation)
         * [intToRgb(intColor)](#inttorgbintcolor)
         * [rgbToInt(r, g, b)](#rgbtointr-g-b)
         * [copyText(text)](#copytexttext)
         * [clipText()](#cliptext)
         * [inputText(text)](#inputtexttext)
         * [dialog(controls, orientations)](#dialogcontrols-orientations)
         * [clearDialogValues(script)](#cleardialogvaluesscript)
         * [openURL(urlString)](#openurlurlstring)
         * [isLicensed()](#islicensed)
         * [setAutoLaunch(scriptPath, on)](#setautolaunchscriptpath-on)
         * [listAutoLaunch()](#listautolaunch)
         * [stop()](#stop)
      * [HTTP APIs](#http-apis)
         * [运行一个脚本](#运行一个脚本)
         * [停止运行一个脚本](#停止运行一个脚本)
         * [列出指定目录下的全部脚本](#列出指定目录下的全部脚本)
         * [创建一个新文件夹](#创建一个新文件夹)
         * [创建一个新文件](#创建一个新文件)
         * [删除一个文件](#删除一个文件)
         * [重命名一个文件或文件夹](#重命名一个文件或文件夹)
      * [固定值](#固定值)
         * [Types of physical keys](#types-of-physical-keys)
         * [Types of dialog controls](#types-of-dialog-controls)
         * [Types of screen orientations](#types-of-screen-orientations)

# 用法

## 怎样安装？
> - AutoTouch有在BigBoss源发布，所以您可以在Cydia/Sileo中直接搜索安装。
> - 您还可以将官方源[https://apt.autotouch.net](https://apt.autotouch.net)添加到Cydia/Sileo中来下载安装。
> - 您还可以将官方测试源[https://beta.autotouch.net](https://beta.autotouch.net)添加到Cydia/Sileo中来安装更新的版本。

## 怎样使用Activator?
> - AutoTouch默认使用长按音量减键和单击音量减键来进行控制，如果您从Cydia/Sileo手动安装Activator，那么您可以使用Activator来自定义这些控制动作。
> - 添加Activator官方源: http://rpetri.ch/repo/到Cydia/Sileop。
> - 搜索并安装Actiavtor。
> - AutoTouch将自动侦测到Activator。
> - 根据需要通过Activator自定义您的控制动作，但千万不要将包含触摸的动作设为AutoTouch的控制动作，因为这类动作会被录制到脚本里，进而导致AutoTouch无法循环播放。

## 怎样录制?
> - 在任何您想开始录制操作的界面，长按音量减键（或您设置的其它Activator控制动作），来弹出控制面板，控制面板上包含一个录制按钮和一个脚本列表。
> ![Control Panel](https://i.imgur.com/ELcGi3A.png)
> - 点击控制面板上的红色“录制”按钮，它将震动提示并开始录制；
> - 现在开始您的触摸操作和一些按键操作会被录制到脚本中；
> - 长按音量减键（或您设置的其它Activator控制动作）来停止录制；
> - 然后会有一个以录制时间为文件名的Lua脚本保存到Record目录，您可以播放或编辑它。

## 怎样播放？
> - 长按音量减键（或您设置的其它控制动作）来调出控制面板。
> - 点击您要播放的脚本来播放它。
> - 点击Play Options按钮会开启播放设置对话框，它会询问您所需要的播放设置。
> - 点击`Hold`按钮来开启`Hold`模式，在此模式下，每一次单击音量减键(或您在Activator中设置的其它动作)，它都会进行播放。
> - 再次长按音量减键可以推出`Hold`模式。
> - 播放中长按音量减键可以强制停止。

## 怎样截屏?
> - 使用iOS自身的截屏功能，或者使用AutoTouch控制面板上的截屏按钮来截屏，截屏图片会保存在iOS系统相册中。
> - 截屏图片可以在脚本编辑器的`助手`中为getColors, findColors 或findImage指定参数提供帮助。

## 怎样写一个脚本
> - 在AutoTouch App的本地脚本列表界面，点击右上方“+”按钮来新建脚本，编辑并保存。

## 怎样在编辑脚本时使用函数“帮助”来方便地插入函数和参数？
> - 在脚本编辑界面的键盘区域上部，有两个按钮：“扩展函数”和“常用语法”，可以通过它们便捷地插入扩展函数和Lua语言常用语法。
> - 点击“扩展函数”按钮，会弹出函数选择列表，点击列表中的函数，将直接插入扩展函数到脚本中，供您做进一步编辑。
> - 在前述的“扩展函数”列表中，部分函数的右边有个“辅助”按钮，用来打开一些便捷的参数获取工具。这些“辅助”工具主要有这几类：屏幕坐标获取、颜色拾取、应用标识(Identifier)获取，实体按键选择。
> - 在“屏幕坐标获取“工具中，打开一张已保存在脚本列表中的BMP格式屏幕截图，手指放大图片到能看到像素点的程度，点击像素点，就可以获取该像素点在屏幕中的坐标，被点击的像素点会变成红色来标识已被选择。
> - 同理在“颜色拾取”工具中，打开图片放大到能看到像素点，点击像素点能获取像素颜色值。
> - “应用标识选择”可以在appRun/appKill/appState/appIsActive时方便地选择目标应用。
> - “实体按键”用在keyDown/keyUp时选择目标按键。
> - 点击“常用语法”可以快速地插入Lua语言常用语法。
> 
>   ![Function Helper](https://i.imgur.com/ng2QWrz.png)

## 怎样在电脑上编写和管理脚本？
> - 您可以在设置界面开启Web Server，然后通过电脑上的浏览器访问提示的URL，然后在其中编辑脚本。
> - 您也可以在设置界面开启WebDAV Server，然后在电脑上通过WebDAV客户端软件连接提示的地址，然后在其中编辑脚本。

## 怎样创建一个脚本Package项目?
> - 你可以创建一个Package项目，它可以包含不同的脚本，文件，图片等所需素材。一个Package实际上是一个名称带.at后缀的文件夹。Package的秘诀在于其中的main.lua文件，它是个脚本的入口。
> - Package可以被整体加密和压缩成一个xxx.ate文件，这个文件可以直接被AutoTouch来执行。

## 怎样加密脚本？
> - 在AutoTouch点击脚本，选择“加密”；
> - 输入加密密码，无需密码留空即可;
> - 点击确定即可完成加密，并生成一个同名但.ate结尾的加密文件；
> - 可以选择加密脚本进行播放，设有密码的根据提示输入密码即可。

## 怎样发布脚本到商城？
> - 您可以将自己的优秀脚本发布在商店中，以分享或售卖给其他人。
> - 在电脑上浏览器访问https://autotouch.net/server/login.php；
> - 按引导填写所需信息，并在HTML栏，填入HTML的页面代码，这些HTMl将用来展示您的脚本详情。你可以在这个页面嵌入一个视频，来讲解您的脚本的功能。
> - 然后发布一个新版本，也就是上传一个xxx.ate的脚本压缩包；
> - 接下来等待审核通过，或者在Discord中与我们联系。
> - 目前您需要自行搭建脚本的授权管理，您可以在脚本中请求您的服务器来查验授权，授权确认的才能执行。AutoTouch暂时无法在这个环节帮助您。

## 怎样从商城下载和购买脚本？
> - 您可以直接从商店中下载所有的脚本。
> - 然后跟作者联系来购买密码。请务必自行注意不要被骗，如果被骗AutoTouch对此无能为力。

## 怎样购买授权？
> - 点击“设置”界面的“授权”按钮来打开授权管理界面。
> - 在打开的“AutoTouch授权管理”页面，点击“说明”可以查看授权协议细则。下方可通过PayPal或淘宝店来购买授权。
> - 通过PayPal购买的，支付完成后，服务器会自动激活当前设备（极偶然的情况下可能激活不成功，如果不成功，请看后文，使用您的PayPal账号邮箱查询出授权码，再“激活当前设备”即可）。
> - 通过淘宝购买的，支付完成后，系统会通过“旺旺”发送授权码给您，获得授权码后，通过“查询我的授权”，用“授权码查询”查出授权信息，然后激活设备。
> - 显示授权成功后，您需要重新进入“授权”界面一次，以使程序下载授权文件。如果您的网络不好，会下载失败（尽管页面可能显示已授权，但由于<a href="http://baike.baidu.com/link?url=7pb7jwC5XxrFI7kxCwTVzv5W5DgCCL4X3uHWkssvhEUV6DI1g1Y4CEaKukb9W7nJk_lu2dxf6Ali1U6Ht-xeGCckfjbBC3_4_UPXBGfY3HxkZKg9cTwFHQvDCNA0NFz2aXjud0Nk2VTJF0_FGkpgbK" target="_blank">GFW</a>的缘故，仍可能会下载失败），如失败，请换网络环境（比如WIFI换4G，联通换电信等）或翻墙，重复进入授权界面，会再尝试下载。授权被验证后，您将获得无限播放时间和全部功能.
> - 您可分别使用三个查询按钮查询到您的授权记录，然后可以激活其它设备。一旦一台新的设备被同一授权码激活，则之前使用此授权码激活的设备会被取消激活。
> - 系统限制为一天只能进行依次激活操作（不是每天都要激活一次），如有需要您可以24小时后再进行激活其它设备的操作。

![License View](https://i.imgur.com/CB0Fnfm.jpg)


# 脚本

## 基础
您可以从这里学习Lua语言的使用：《[Lua Official Reference Manual](http://www.lua.org/manual/5.3/)》

## 开发工具
[LuaStudio](http://luastudio.net/)

## Coordinate, Size and Orientation System
AutoTouch的坐标体系是建立在像素的基础上，请看[不同设备的像素尺寸](https://developer.apple.com/library/archive/documentation/DeviceInformation/Reference/iOSDeviceCompatibility/Displays/Displays.html), 比如iPhone X 的屏幕尺寸是1125 x 2436.

无论设备的方向是怎样的，坐标远点(0, 0)总是在App界面的`左上角`。所以在为AutoTouch编写脚本时，您只需要考虑相应的App的界面即可：坐标原点永远在App界面左上角。

![比如](https://i.imgur.com/imDVXXB.png)

## 扩展库
> AutoTouch自带了一些第三方扩展库，但您也可以自己添加扩展库，只要将符合格式的 `.so`库文件放置在`/usr/local/lib/lua/5.3`，以及`.lua`文件放置在`/var/mobile/Library/AutoTouch/Library/LuaLibraries`，Respring即可启用这个库。当然为iOS平台编译扩展库是有点技术门槛的。

> **警告:** **一定不要** 使用跟扩展库相同的名字作为您自己脚本的文件名，如`lcurl`, `lfs`, `lsqlite3`。

### LuaCURL
> curl is used in command lines or scripts to transfer data. It is also used in cars, television sets, routers, printers, audio equipment, mobile phones, tablets, settop boxes, media players and is the internet transfer backbone for thousands of software applications affecting billions of humans daily.

> It supports DICT, FILE, FTP, FTPS, Gopher, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMB, SMBS, SMTP, SMTPS, Telnet and TFTP. curl supports SSL certificates, HTTP POST, HTTP PUT, FTP uploading, HTTP form based upload, proxies, HTTP/2, cookies, user+password authentication (Basic, Plain, Digest, CRAM-MD5, NTLM, Negotiate and Kerberos), file transfer resume, proxy tunneling and more.

> [Learn More](https://github.com/Lua-cURL/Lua-cURLv3)

`Examples:`

```lua
-- HTTP Get
local curl = require('lcurl')
curl.easy{
    url = 'http://httpbin.org/get',
    httpheader = {
      "X-Test-Header1: Header-Data1",
      "X-Test-Header2: Header-Data2",
    },
    writefunction = alert -- use io.stderr:write()
  }
  :perform()
:close()

-- HTTP Post
curl.easy()
  :setopt_url('http://posttestserver.com/post.php')
  :setopt_writefunction(io.write)
  :setopt_httppost(curl.form() -- Lua-cURL guarantee that form will be alive
    :add_content("test_content", "some data", {
      "MyHeader: SomeValue"
    })
    :add_buffer("test_file", "filename", "text data", "text/plain", {
      "Description: my file description"
    })
    :add_file("test_file2", "BuildLog.htm", "application/octet-stream", {
      "Description: my file description"
    })
  )
  :perform()
:close()
```

### LuaSocket
> LuaSocket is a Lua extension library which supported [TCP](http://w3.impa.br/~diego/software/luasocket/introduction.html#tcp), [UDP](http://w3.impa.br/~diego/software/luasocket/introduction.html#udp), [SMTP](http://w3.impa.br/~diego/software/luasocket/smtp.html), [HTTP](http://w3.impa.br/~diego/software/luasocket/http.html), [FTP](http://w3.impa.br/~diego/software/luasocket/ftp.html) protocols. Learn how to use it from the [Learn More](http://w3.impa.br/~diego/software/luasocket/introduction.html).

### LuaSec
> LuaSec is a binding for OpenSSL library to provide TLS/SSL communication. It takes an already established TCP connection and creates a secure session between the peers.[Learn More](https://github.com/brunoos/luasec/wiki)

### LuaSqlite3
> LuaSQLite 3 is a thin wrapper around the public domain SQLite3 database engine. [Learn More](http://lua.sqlite.org/index.cgi/doc/tip/doc/lsqlite3.wiki)

### json.lua
> json.lua provides operation methods on json.
[GitHub](https://github.com/rxi/json.lua) 
[LICENSE](https://github.com/rxi/json.lua/blob/master/LICENSE)

`Usage`
```lua
local json = require "json"
local jsonString =json.encode({ 1, 2, 3, { x = 10 } }) -- Returns '[1,2,3,{"x":10}]'
local luaTable = json.decode('[1,2,3,{"x":10}]') -- Returns { 1, 2, 3, { x = 10 } }
```

### Plist
> Plist library provides a batch of methods to operate on plist files.

`Usage`
```lua
local plist = require("plist")

-- Read a plist file, return it as a lua table, return nil if failed.
local luaTable = plist.read(plistFilePath);

-- Write a lua table as a plist into a file, the foramt parameter specifis "xml", "binary" you want to write with.
local done = plist.write(luaTable, plistFilePath, format);

-- Load a plist string to lua table.
local luaTable = plist.load(plistString);

-- Dump a lua table to plist data with format "xml" or "binary"
local plistData = plist.dump(luaTable, format);
```

### Penlight
> A set of pure Lua libraries focusing on input data handling (such as reading configuration files), functional programming (such as map, reduce, placeholder expressions,etc), and OS path management. 
[GitHub](https://github.com/stevedonovan/Penlight)
[Document](http://stevedonovan.github.io/Penlight/api/index.html)
[LICENSE](https://github.com/stevedonovan/Penlight/blob/master/LICENSE.md)

It has plenty of modules:

Paths, Files and Directories

  * `path`: queries like `isdir`,`isfile`,`exists`, splitting paths like `dirname` and `basename`
  * `dir`: listing files in directories (`getfiles`,`getallfiles`) and creating/removing directory paths
  * `file`: `copy`,`move`; read/write contents with `read` and `write`

Application Support

  * `app`: `require_here` to rebase `require` to work with main script path; simple argument parsing `parse_args`
  * `lapp`: sophisticated usage-text-driven argument parsing for applications
  * `config`: flexibly read Unix config files and Windows INI files
  * `strict`: check for undefined global variables - can use `strict.module` for modules
  * `utils`,`compat`: Penlight support for unified Lua 5.1/5.2 codebases
  * `types`: predicates like `is_callable` and `is_integer`; extended `type` function.

Extra String Operations

  * `utils`: can split a string with a delimiter using `utils.split`
  * `stringx`: extended string functions covering the Python `string` type
  * `stringio`:  open strings for reading, and creating strings using standard Lua IO methods
  * `lexer`:  lexical scanner for splitting text into tokens; special cases for Lua and C
  * `text`:  indenting and dedenting text, wrapping paragraphs; optionally make `%` work as in Python
  * `template`:  small but powerful template expansion engine
  * `sip`:  Simple Input Patterns - higher-level string patterns for parsing text

Extra Table Operations

  * `tablex`: copying, comparing and mapping over
  * `pretty`: pretty-printing Lua tables, and various safe ways to load Lua as data
  * `List`: implementation of Python 'list' type - slices, concatenation and partitioning
  * `Map`, `Set`, `OrderedMap`: classes for specialized kinds of tables
  * `data`: reading tabular data into 2D arrays and efficient queries
  * `array2d`: operations on 2D arrays
  * `permute`: generate permutations

Iterators, OOP and Functional

   * `seq`:  working with iterator pipelines; collecting iterators as tables
   * `class`: a simple reusable class framework
   * `func`: symbolic manipulation of expressions and lambda expressions
   * `utils`: `utils.string_lambda` converts short strings like `|x| x^2` into functions
   * `comprehension`: list comprehensions: `C'x for x=1,4'()=={1,2,3,4}`

### LuaFileSystem
> LuaFileSystem is a Lua library developed to complement the set of functions related to file systems offered by the standard Lua distribution.

> LuaFileSystem offers a portable way to access the underlying directory structure and file attributes.[Learn More](https://keplerproject.github.io/luafilesystem/index.html)

### WebSocket
> This module provides Lua modules for [Websocket Version 13](http://tools.ietf.org/html/rfc6455) conformant clients and servers.

[GitHub](https://github.com/lipp/lua-websockets)
[LICENSE](https://github.com/lipp/lua-websockets/blob/master/COPYRIGHT)
[Examples](https://github.com/lipp/lua-websockets/tree/master/examples)

`Usage`
```lua
-- Client
-- connects to a echo websocket server running a localhost:8080
-- sends a strong every second and prints the echoed messages
-- to stdout

local ev = require'ev'
local ws_client = require('websocket.client').ev()

ws_client:on_open(function()
    print('connected')
  end)

ws_client:connect('ws://echo.websocket.org','echo')

ws_client:on_message(function(ws, msg)
    print('received',msg)
  end)

local i = 0

ev.Timer.new(function()
    i = i + 1
    ws_client:send('hello '..i)
end,1,1):start(ev.Loop.default)

ev.Loop.default:loop()
```

## 扩展函数

扩展函数用于扩展Lua语言，使具备模拟人类操作手机的一些能力。还提供截屏、颜色查找、颜色匹配、图片匹配等功能。

### touchDown(id, x, y)
> 在屏幕的(x, y)坐标按下。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| id    | 整型   |   手指编号，用来在单点、多点触摸标识一个手指，通常取值0到9。 |
| x     |   浮点   |   屏幕x坐标   |
| y     |    浮点    |  屏幕y坐标  |

`返回值`

无

`示例`
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
> 移动手指到(x, y)坐标。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| id    | 整型   |   手指编号，用来在单点、多点触摸标识一个手指，通常取值0到9。 |
| x     |   浮点   |   屏幕x坐标   |
| y     |    浮点    |  屏幕y坐标  |

`返回值`

无

`示例`
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
> 从(x, y)坐标抬起手指。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| id    | 整型   |   手指编号，用来在单点、多点触摸标识一个手指，通常取值0到9。 |
| x     |   浮点   |   屏幕x坐标   |
| y     |    浮点    |  屏幕y坐标  |

`返回值`

无

`示例`
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
> 模拟实体键按下动作。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| keyType     |  整型  |   实体键标识，现在可使用[这些实体按键](#types-of-physical-keys).   |

`返回值`

无

`示例`
```lua
-- Simulate the pressing of Home Key.
keyDown(KEY_TYPE.HOME_BUTTON);

-- How to simulate a key pressing?
function keyPress(keyType)
    keyDown(keyType);
    usleep(10000);
    keyUp(keyType);
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
> 模拟实体键抬起动作。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| keyType     |  整型  |   实体键标识，现在可使用[这些实体按键](#types-of-physical-keys).   |

`返回值`

无

`示例`
```lua
-- Simulate the action of pressing and lifting Home Key.
keyDown(KEY_TYPE.HOME_BUTTON);
usleep(10000);
keyUp(KEY_TYPE.HOME_BUTTON);
```

### getColor(x, y)
> 在当前屏幕获取指定坐标位置像素点的颜色值。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| x     |   浮点   |   屏幕x坐标   |
| y     |    浮点    |  屏幕y坐标  |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| color     |  整型  |   像素点的整数类型颜色值   |

`示例`
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
> 获取屏幕多个点的颜色值。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| locations     |  表  |   多个坐标点的列表，如{ {x1,y1}, {x2,y2}, {x3,y4} }   |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| colors     |  表  |   对应坐标点的颜色值的列表。  |

`示例`
```lua
local result = getColors({ {100, 200}, {200, 300}, {300, 400} });
for i, v in pairs(result) do
    log(string.format("Gotten color:%d", v));
end
```

### findColor(color, count, region, debug)
> 在当前屏幕查找所有匹配指定颜色的像素点坐标。

`参数`

| 参数     | 类型   |  说明  | 可选 | 默认值 |
| -------- | :-----:| ----  | :----:  | :----:  |
| color     |  整型  |   匹配的颜色值。   | 否 | |
| count     |  整型  | 最多查找多少个匹配的像素点，默认是0，表示查找所有匹配点。如果是1，表示查出第一个即可，若是2表示查出前两个即可。查找的个数越少速度越快。 | 否 | 0 |
| region     |  表  | You only search the result in the specified area. This area is the table type including four values {x, y, width, height}. The four values respectively represent the coordinate x, coordinate y, width, and height of the rectangular area. {100,100,200,200} is an example. If you do not want to specify the area, just input nil.  | 否 | nil |
| debug    |  布尔  | If pass debug=true, it will produce a image ends with "-Debug.PNG" marked the matching areas. |  是  | false |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| locations     |  表  |  Coordinates of matched pixel points. For example: { {x1, y1}, {x2, y2}, ... }  |

`示例`
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
-- Keep finding a speficied color until it's found.
local locations
repeat
   local locations = findColor(0x0000ff, 2, nil);
   usleep(50000) -- Wait a while
until(#locations > 0)
-- Log the locations if found
for i, v in pairs(locations) do
    log(string.format("Found pixel: x:%f, y:%f", v[1], v[2]));
end
```

`内部实现`
```lua
function findColor(color, count, region)
    return findColors({ {color,0,0} }, count, region);
end
```

### findColors(colors, count, region, debug)
> 查找所有匹配“指定颜色及它们的相对位置”的矩形区域，返回找到的矩形区域中匹配第一个颜色的像素的坐标。该函数具有比findImage高得多的查找效率和可用度，比如查找一个按钮，不用像findImage一样去匹配整个按钮图片，只用匹配按钮中的几个锚点的颜色和它们的相对位置即可。可以使用count参数限定希望查找结果的个数，0表示查找所有，1标识查找第1个，2表示查找前两个。region参数可以用来限定查找的区域，为{x, y, width, height}的table类型，不限定时传入nil即可。

> 这个函数可以使用脚本编辑界面“扩展函数”中的“辅助”工具，快速地从屏幕截图中选择几个锚点颜色，并自动获取它们的相对位置来插入到函数参数位置。
> 下图箭头所指像素点的坐标为返回值的坐标。

![IMG_0361.PNG-101.9kB](https://i.imgur.com/ODEtwAz.png)

`参数`

| 参数     | 类型   |  说明  | 可选 | 默认值 |
| -------- | :-----:| ----  | :----:  | :----:  |
| colors     |  表  |  包含一些颜色以及它们的相对位置，比如{ {0x00ddff,0,0}, {0x00eeff,10,10}, {0x0000ff,0,20} }，大table中的小table包含三个值，第一个是颜色值，第二个和第三个值是该颜色相对于第一个颜色的相对位置，其中第一个颜色的table的相对位置总是(0,0)，比如{0x00ddff,0,0}这个颜色，而后续的几个颜色的位置值，是它们相对于第一个颜色的位置。用这些颜色和相对位置关系，可以从屏幕中匹配到符合的矩形区域。 | 否 | |
| count     |  整型  | 最多查找多少个匹配的像素点，默认是0，表示查找所有匹配点。如果是1，表示查出第一个即可，若是2表示查出前两个即可。查找的个数越少速度越快。 | 否 | 0 |
| region     |  表  | 限定在指定区域进行查找。该参数是包含{x, y, width, height}四个值的一个table类型，四个值分别是矩形区域的左上x,y坐标，和矩形区域的宽和高，比如{100, 100, 200,
        200}。如果不想限定区域，传入nil即可。 | 否 | nil |
| debug    |  布尔  | 如果传入true, 在查找的同时将会产生一个文件名以"-Debug.PNG"结尾的图片文件来标示查找的区域。 |  是  | false |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| locations     |  表  |  查找到的矩形区域中匹配第一个颜色的像素点的坐标。比如：{ {x1, y1}, {x2, y2}, ...} |

`示例`
```lua
-- Example 1:
local result = findColors({ {0x00ddff,0,0}, {0x00eeff,10,10}, {0x0000ff,0,20} }, 2, nil, true);
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 2:
local colors = { {0x00ddff,0,0}, {0x00eeff,10,10}, {0x0000ff,0,20} };
local result = findColors(colors, 0, nil, true);
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

### findImage(targetImagePath, count, threshold, region, debug)
> 在当前屏幕查找匹配指定图片的区域，以table形式返回找到的所有区域的左上角坐标。

![Imgur](https://i.imgur.com/9eyFOu7.png)

`参数`

| 参数     | 类型   |  说明  | 可选 | 默认值 |
| -------- | :-----:| ----  | :----:  | :----:  |
| targetImagePath     |  字符串  |  需要查找的图片的相对路，比如 "images/gold.PNG". JPG/JPEG/PNG/BMP格式的图片都支持  | 否 | |
| count     |  整型  | 最多查找多少个匹配的像素点，默认是0，表示查找所有匹配点。如果是1，表示查出第一个即可，若是2表示查出前两个即可。查找的个数越少速度越快。|  是  | 0 |
| threshold |  浮点  | 查找的精度, 最大值1表示完全相同, 最下值-1表示完全不相同, 默认是0.9, 通常0.99表现就很好. 如果你只想使用默认值，那么传入nil即可 |  是  | 0.9 |
| region    |  表  | 限定在指定区域进行查找。该参数是包含{x, y, width, height}四个值的一个table类型，四个值分别是矩形区域的左上x,y坐标，和矩形区域的宽和高，比如{100, 100, 200,
        200}。如果不想限定区域，传入nil即可。 |  是  |  全屏幕区域 |
| debug    |  布尔  | 如果传入true, 在查找的同时将会产生一个文件名以"-Debug.PNG"结尾的图片文件来标示查找的区域。 |  是  | false |
| method    |  integer  | 查找方法，默认是1，如果你想使用更智能的方法，请传入2，方法2能匹配相同图形但是大小，方向，颜色有改变的目标 | YES | 1 |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| center locations     |  表  |  匹配区域中心坐标的列表. 比如：{ {x1, y1}, {x2, y2}, ...}  |

`示例`
```lua
-- Example 1:
local result = findImage("images/Gold.PNG", 5, 0.99, nil, true)
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 2:
local result = findImage("images/Gold.PNG", nil, nil, nil, true)
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 3:
local result = findImage("images/Gold.PNG", 3)
for i, v in pairs(result) do
    log(string.format("Found rect at: x:%f, y:%f", v[1], v[2]));
end

-- Example 4:
local imagePath = "images/spirit.PNG";
local region = {100, 100, 300, 300};
local result = findImage(imagePath, 2, 0.98, region, true)
for i, v in pairs(result) do
    local x = v[1], y = v[2];

    log(string.format("Found rect at: x:%f, y:%f", x, y));
    
    -- Click the found location once.
    tap(x, y);
    usleep(16000);
end

-- Example 5:
local imagePath = "images/spirit.PNG";
local region = {100, 100, 300, 300};
-- Use method 2 to find image
local result = findImage(imagePath, 2, 0.98, region, true, 2)
```

### screenshot(filePath, region)
> 全屏幕或者指定区域截屏。

> 如果filePath参数为nil，它将截屏以PNG格式图片保存到系统相册的“AutoTouch”文件夹下。如果指定了filePath，则会保存到filePath位置。

> 如果region参数为nil，它将对全屏幕截屏，否则只对指定区域截屏。

> 点击AutoTouch本地脚本界面的右上角的“+”按钮，选择“复制到这里”，可以将一个图片从iOS系统相册复制到AutoTouch目录，供在本定使用。这意味着您可以利用第三方工具对iOS相册中的图片进行编辑，然后复制到这里供AutoTouch使用。

`参数`

| 参数     | 类型   |  说明  | 可选 | 默认值 |
| -------- | :-----:| ----  | :-----: | :-----: |
| filePath     |  字符串  | 截图保存地址 |  是  | 默认在系统相册的"AutoTouch"目录下 |
| region     |  表  | 截屏区域， {x, y, width, height}， 如{100,100,200,200}。如果不像指定，直接传入nil，将全屏幕截图。 |  是  | nil |

`返回值`

无

`示例`
```lua
-- Take shot of the whole screen and save into  "AutoTouch" album of iOS Photo Library.
screenshot();

-- Take a screenshot of the whole screen and save to the specified path, if no PNG as path extension, .PNG will automatically added.
screenshot ("images/screenshot1");

-- Take a screenshot of the specified area and save.
screenshot ("images/screenshot2.PNG", {100, 100, 200, 200});

-- Take a screenshot of the specified area and save into  "AutoTouch" album of iOS Photo Library.
screenshot (nil, {100, 100, 200, 200});
```

### appRun(appIdentifier)
> 运行一个App

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| appIdentifier     |  字符串  |  应用标识，如"com.apple.mobilesafari"。您可以从[这里](https://offcornerdev.com/bundleid.html)查找应用标识。 |

`返回值`

无

`示例`
```lua
-- Run Safari
appRun("com.apple.mobilesafari");
```

### appKill(appIdentifier)
> 关闭一个App

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| appIdentifier     |  字符串  |  应用标识，如"com.apple.mobilesafari"。您可以从[这里](https://offcornerdev.com/bundleid.html)查找应用标识。 |

`返回值`

无

`示例`
```lua
-- Kill the running Safari
appKill("com.apple.mobilesafari");
```

### appState(appIdentifier)
> 获取一个App的运行状态。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| appIdentifier     |  字符串  |  应用标识，如"com.apple.mobilesafari"。您可以从[这里](https://offcornerdev.com/bundleid.html)查找应用标识。 |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| state     |  字符串  |  字符串类型的状态, 它们是: "NOT RUNNING", "ACTIVATED", "DEACTIVATED"。 |

`示例`
```lua
-- Get the state of Safari.
local state = appState("com.apple.mobilesafari");
alert(string.format("State of Safari: %s", state));
-- Pop up the state of Safari: "ACTIVATED"
```

### rootDir()
> AutoTouch存放本地脚本等文件的根目录，也就是: "/var/mobile/Library/AutoTouch/Scripts/".

`参数`

无

`返回值`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| dir     |  字符串  |  AutoTouch存放文件的根目录。 |

`示例`
```lua
local dirPath = rootDir();
alert(dirPath);
-- Popup "/var/mobile/Library/AutoTouch/Scripts/"
```

### currentPath()
> 获得当前运行脚本的全路径。

`参数`

无

`返回值`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| path     |   字符串   |  当前运行脚本的全路径。 |

`示例`
```lua
local path = currentPath();
alert(path);
-- Popup "/var/mobile/Library/AutoTouch/Scripts/test.lua"
```

### usleep(microseconds)
> 停顿若干个微秒，即1/1000000秒

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| microseconds     |  整型  |  停顿多少微秒。 |

`返回值`

无

`示例`
```lua
-- Sleep 1 second.
usleep(1000000);
```

### log(content)
> 记录日志，可在日志界面查看。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| content     |  字符串  |  日志内容 |

`返回值`

无

`示例`
```lua
log("play here...");
```

### alert(message)
> 弹出框提示信息

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| message     |  字符串  |  信息内容 |

`返回值`

无

`示例`
```lua
alert("Hello World!");
```

### toast(message, delay)
> toast形式展示信息若干秒。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| message     |  字符串  |  信息内容 |
| delay     |  整型  |  展示多久，默认2秒。 |

`返回值`

无

`示例`
```lua
toast("Hello I'm a toast!", 5); -- Show message for 5 seconds.
toast("Hello again!"); -- Show message for 2 seconds.
```

### vibrate()
> 震动一次，没有震动功能的设备无效果 ，比如iPod Touch和iPad

`参数`

无

`返回值`

无

`示例`
```lua
-- Vibrate once.
vibrate();
```

### playAudio(audioFile, times)
> 播放指定位置的音频文件。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| audioFile     |  字符串  |  音频文件绝对路径。 |
| times     |  整型  |  重复播放次数。0表示无限重复。 |

`返回值`

无

`示例`
```lua
-- Play audio infinitely.
playAudio("/var/audio.mp3", 0);
```

### stopAudio()
> 停止播放音频。

`参数`

无

`返回值`

无

`示例`
```lua
-- Stop playing audio.
stopAudio();
```

### getOrientation()
> 获取屏幕方向。返回整型值，具体对应关系请看“屏幕方向类型”。

`参数`

无

`返回值`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| orientation     |  整型  |  屏幕方向，可能是[这些值](#types-of-screen-orientations) |

`示例`
```lua
local o = getOrientation();
alert(string.format("Screen orientation is : %d", 0))
-- Pop up the orientation 2 of the screen, and mark the reversed screen.
```

### getScreenResolution()
> 获取屏幕像素分辨率。

`参数`

无

`返回值`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| width     |  整型  |  宽度 |
| height     |  整型  |  高度 |

`示例`
```lua
local w, h = getScreenResolution();
alert(string.format("Resolution of iPhone 6 Plus: width:%d, height:%d", w, h));
-- iPhone 6 Plus’s resolution width is 1242 and resolution height is 2208.
```

### getSN()
> 获取设备序列号。

`参数`

无

`返回值`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| SN     |  字符串  | 设备序列号。 |

`示例`
```lua
local sn = getSN();
alert(string.format("SN is : %s", sn));
-- Popup shows the SN of the device: C15NFK32TWD2
```

### getVersion()
> 获取当前AutoTouch版本号。

`参数`

无

`返回值`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| version     |  字符串  |  AutoTouch版本号。 |

`示例`
```lua
local version = getVersion();
alert(string.format("Current version of AutoTouch is : %s", version));
-- Pop up shows current version of AutoTouch: 3.5.3-4
```

### frontMostAppId()
> 当前在前台运行的App的标识。

`参数`

无

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| App Identifier     |  字符串  |  App标识 |

`示例`
```lua
local appId = frontMostAppId();
alert(string.format("Current front most App is : %s", appId));
```

### frontMostAppOrientation()
> 当前前台运行的App的界面方向，可能是[这些值](#types-of-screen-orientations)

`参数`

无

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| orientation     |  整型  |  屏幕方向，可能是[这些值](#types-of-screen-orientations) |

`示例`
```lua
local orientation = frontMostAppOrientation();
alert(string.format("Orientation of current front most App is : %d", orientation));
```

### intToRgb(intColor)
> 将整型颜色值转换为R, G, B单独的值。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| intColor   |  整型  | 整型颜色值。 |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| R   |  整型  | Red值 |
| G   |  整型  | Green值 |
| B   |  整型  | Blue值 |

`示例`
```lua
local r, g, b = intToRgb(0x2b2b2b);
alert(string.format("R:%d, G:%d, B:%d", r, g, b));
```

### rgbToInt(r, g, b)
> 将R, G, B色值转换为整形颜色值。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| R   |  整型  | Red值 |
| G   |  整型  | Green值 |
| B   |  整型  | Blue值 |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| intColor   |  整型  | 整型颜色值。 |

`示例`
```lua
local intColor = rgbToInt(200, 255, 100);
alert(string.format("Int type color: %d", intColor));
```

### copyText(text)
> 将一段文本复制到剪贴板

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| text     |  字符串  |  文本 |

`返回值`

无

`示例`
```lua
copyText("This is a copied text!");
```

### clipText()
> 获得剪贴板中的文本

`参数`

无

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| text     |  字符串  |  文本 |

`示例`
```lua
local text = clipText();
alert(text);
-- Popup shows the text to be copied: "This is a copied text!";
```

### inputText(text)
> 输入文本到当前选中的输入框中。inputText("\b")可以退格删除一个字符。

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| text     |  字符串  | 文本 |

`返回值`

无

`示例`
```lua
inputText("Let's input some text automatically without tapping the keyboard!");
--  Delete 3 character by inputing 3 backspaces.
inputText("\b\b\b"); 
```

### dialog(controls, orientations)
> 显示一个自定义的对话框，用法请见下面的示例。

`参数`

| 参数     | 类型   |  说明  | 可选 | 默认值 |
| -------- | :-----:| ----  | :----:  | :----:  |
| controls     |  表  | 控件列表. 可以使用这些控件 [these dialog box controls](#types-of-dialog-controls)  | 否 | |
| orientations |  表    | 对话框限定的方向 [方向值](#types-of-screen-orientations). | 是 | 自动 |

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| 被点击按钮的Flag    |   整型  |   |


`示例`
```lua
local label = {type=CONTROLLER_TYPE.LABEL, text="Would you mind to provide some personal informations?"}
local nameInput = {type=CONTROLLER_TYPE.INPUT, title="Name:", key="Name", value="Bob"}
local positionPicker = {type=CONTROLLER_TYPE.PICKER, title="Position:", key="Position", value="CEO", options={"CEO", "CTO", "CFO", "CXO"} }
local developerSwitch = {type=CONTROLLER_TYPE.SWITCH, title="A Developer:", key="ADeveloper", value=1}

-- It's an option for users to determine weather the inputs should be remembered, if you use this control in the dialog.
local remember = {type=CONTROLLER_TYPE.REMEMBER, on=false}

--[[ Define buttons:
type = CONTROLLER_TYPE.BUTTON
title = Button text
color = Button background color, it's optional, the default value is 0x428BCA
width = Button width upon percentage of the dialog width, it's optional, the default value is 0.5, max value is 1.0.
flag = Integer type of button flag for identifying which button is tapped.
collectInputs = Boolean type specifying wheather the dialog should collect the inputs while this button is tapped. ]]--
local btn1 = {type=CONTROLLER_TYPE.BUTTON, title="Button 1", color=0x71C69E, width=0.8, flag=1, collectInputs=false}
local btn2 = {type=CONTROLLER_TYPE.BUTTON, title="Button 2", color=0xFF5733, flag=2, collectInputs=true}
local btn3 = {type=CONTROLLER_TYPE.BUTTON, title="Button 3", color=0xFFB7D0, width=1.0, flag=3, collectInputs=false}
local btn4 = {type=CONTROLLER_TYPE.BUTTON, title="Button 4", width=1.0, flag=4, collectInputs=true}

local controls = {label, nameInput, positionPicker, developerSwitch, btn1, btn2, remember, btn3, btn4}

-- Pop up the dialog. After popping, the script will suspend waiting for user input until any button is tapped, then returns the flag of tapped button.

-- What orientations the dialog could be, it's optional
local orientations = { ORIENTATION_TYPE.LANDSCAPE_LEFT, ORIENTATION_TYPE.LANDSCAPE_RIGHT };

local result = dialog(controls, orientations);

if (result == 1) then
    alert(string.format("name:%s, birthday:%s, gender:%d", nameInput.value, positionPicker.value, developerSwitch.value))
else
    alert(string.format("Dialog returned: %s", result))
end
```
![dialog](https://i.imgur.com/GN9wji7.png)

### clearDialogValues(script)
> 清除之前记住的对话框的输入值

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| script     |  字符串  | 对话框所在的脚本或Package  |

`返回值`

无

`示例`
```lua
-- There is a dialog.lua script in the scripts list
clearDialogValues("dialog.lua");
```

### openURL(urlString)
> 打开一个App的URL scheme. 请见[Always-Updated List of iOS App URL Scheme Names](https://ios.gadgethacks.com/news/always-updated-list-ios-app-url-scheme-names-0184033/) and example: [Google Maps URL Scheme for iOS](https://developers.google.com/maps/documentation/urls/ios-urlscheme)

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| urlString     |  字符串  |  目标URL Scheme |

`返回值`

无

`示例`
```lua
openURL("https://autotouch.net")
openURL("prefs:root=General&path=About")
openURL("musics://")
openURL("itms-apps://itunes.apple.com")
openURL("tel://+1123456")
openURL("clashofclans://")
```

### isLicensed()
> 检查当前AutoTouch是否已授权

`参数`

无

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| licensed     |  布尔  | 是否已授权 |

`示例`
```lua
if isLicensed() then
    alert("Your device is licensed by AutoTouch!");
end
```

### setAutoLaunch(scriptPath, on)
> 对一个脚本开启或关闭开机自动启动

`参数`

| 参数     | 类型   |  说明  |
| -------- | :-----:| ----  |
| filePath     |  字符串  |  脚本的相对地址，如"/Records/test.lua"。 |
| on     |  布尔  |  true是打开，false是关闭 |

`返回值`

无

`示例`
```lua
setAutoLaunch("/Records/test.lua", on);
```

### listAutoLaunch()
> 列出所有开机启动的脚本

`参数`

无

`返回值`

| 返回值     | 类型   |  说明  |
| -------- | :-----:| ----  |
| scripts     |  表  |  开机启动的脚本的相对地址  |

`示例`
```lua
local scripts = listAutoLaunch()
for i, v in pairs(scripts) do
    alert(v);
end
```

### stop()
> 停止当前脚本的执行

`Parameters`

无

`Return`

无

`Examples`
```lua
-- 退出当前脚本执行
stop();
```

## HTTP APIs
> AutoTouch也提供了一些HTTP接口，您可以用HTTP请求的方式在局域网远程调用，这些接口也就是`Web Server`使用的接口。

### 运行一个脚本
> GET /control/start_playing?path=/scriptPath

`参数`

| 参数     |  说明  |
| -------- | ----  |
| path     | 脚本相对路径  |

`返回值`

Successful:
```json
{
    "status": "success"
}
```

Failed:
```json
{
    "status": "fail",
    "info": ""
}
```

`示例`

```
HTTP GET http://192.168.1.99:8080/control/start_playing?path=/scriptPath
```

```json
{
    "status": "fail",
    "info": "Script doesn't exist."
}
```

### 停止运行一个脚本
> GET /control/stop_playing?path=/scriptPath

`参数`

| 参数     |  说明  |
| -------- | ----  |
| path     | 脚本相对路径  |

`返回值`

Successful:
```json
{
    "status": "success"
}
```

Failed:
```json
{
    "status": "fail",
    "info": ""
}
```

`示例`

```
HTTP GET http://192.168.1.99:8080/control/start_playing?path=/scriptPath
```

```json
{
    "status": "fail",
    "info": "Script doesn't exist."
}
```

### 列出指定目录下的全部脚本
> GET /files?path=/Records

`参数`

| 参数     |  说明  |
| -------- | ----  |
| path     | 指定目录  |

`返回值`

```json
{
    "files": [
        {
            "filePath": "",
            "fileSize": "",
            "iconName": ""
        },
        ...
    ]
}
```

`示例`

```
HTTP GET http://192.168.1.99:8080/files?path=/Records
```

```json
{
    "files": [
        {
            "filePath": "/Records/2019-03-10: 12:00:00.lua",
            "fileSize": "12kb",
            "iconName": "script"
        },
        ...
    ]
}
```

### 创建一个新文件夹
> GET /file/newFolder?path=/Test

`参数`

| 参数     |  说明  |
| -------- | ----  |
| path     | 新文件夹路径  |

`返回值`

Successful:
```json
{
    "status": "success"
}
```

Failed:
```json
{
    "status": "fail",
    "info": ""
}
```

`示例`

```
HTTP GET http://192.168.1.99:8080/file/newFolder?path=/Test
```

```json
{
    "status": "success"
}
```

### 创建一个新文件
> GET /file/new?path=/newFilePath

`参数`

| 参数     |  说明  |
| -------- | ----  |
| path     | 新文件路径 |

`返回值`

Successful:
```json
{
    "status": "success"
}
```

Failed:
```json
{
    "status": "fail",
    "info": ""
}
```

`示例`

```
HTTP GET http://192.168.1.99:8080/file/new?path=/newFilePath
```

```json
{
    "status": "fail",
    "info": "Invalid file path"
}
```

### 删除一个文件
> GET /file/delete?path=/filePathToDelete

`参数`

| 参数     |  说明  |
| -------- | ----  |
| path     | 要删除的文件的路径  |

`返回值`

Successful:
```json
{
    "status": "success"
}
```

Failed:
```json
{
    "status": "fail",
    "info": ""
}
```

`示例`

```
HTTP GET http://192.168.1.99:8080/file/delete?path=/filePathToDelete
```

```json
{
    "status": "fail",
    "info": "Invalid file path"
}
```

### 重命名一个文件或文件夹
> GET /file/rename?path=/oldFilePath&newPath=newFilePath

`参数`

| 参数     |  说明  |
| -------- | ----  |
| path     | 旧路径  |
| newPath  | 新路径  |

`返回值`

Successful:
```json
{
    "status": "success"
}
```

Failed:
```json
{
    "status": "fail",
    "info": ""
}
```

`示例`

```
HTTP GET http://192.168.1.99:8080/file/rename?path=/oldFilePath&newPath=newFilePath
```

```json
{
    "status": "fail",
    "info": "Invalid file path"
}
```

## 固定值

### Types of physical keys

| 值     |  说明  |
| -------- | ----  |
| KEY_TYPE.HOME_BUTTON | Home Button |
| KEY_TYPE.VOLUME_DOWN_BUTTON | Volume – Button |
| KEY_TYPE.VOLUME_UP_BUTTON | Volume + Button |
| KEY_TYPE.POWER_BUTTON | Power Button |

### Types of dialog controls

| 值     |  说明  |
| -------- | ----  |
| CONTROLLER_TYPE.LABEL | Text label |
| CONTROLLER_TYPE.INPUT | Input box |
| CONTROLLER_TYPE.PICKER | Picker |
| CONTROLLER_TYPE.SWITCH | Switch |
| CONTROLLER_TYPE.BUTTON | Button |
| CONTROLLER_TYPE.REMEMBER | Switch for remember user inputs |

### Types of screen orientations

| 值     |  说明  |
| -------- | ----  |
| ORIENTATION_TYPE.UNKNOWN   | Unknown orientation. Practical value is 0. |
| ORIENTATION_TYPE.PORTRAIT | Portrait screen. Home button is at the bottom. Practical value is 1. |
| ORIENTATION_TYPE.PORTRAIT_UPSIDE_DOWN | Upside-down portrait screen. Home button on the top. Practical value is 2. |
| ORIENTATION_TYPE.LANDSCAPE_LEFT | Landscape left screen. Home Key is in the left. Practical value is 3. |
| ORIENTATION_TYPE.LANDSCAPE_RIGHT | Landscape right screen. Home key is in the right. Practical value is 4. |