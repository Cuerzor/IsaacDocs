---
tags:
  - Globals
  - Class
---
# Class "Font"

???+ info
    这个类是用来加载和渲染字体的。它可以通过以下方式访问:

    * [Game.GetFont()](Game.md#getfont)

    ???+ example "Example Code"

        ```lua

            local myFont = Font()

        ```

## Constructors
### Font () {: aria-label='Constructors' }
[ ](#){: .alldlc .tooltip .badge }
#### [Font](Font.md) Font ( ) {: .copyable aria-label='Constructors' }

"Font" 类的构造函数.

???- example "Example Code"

    Example usage.

    ```lua

        local f = Font() -- init font object
        f:Load("font/terminus.fnt") -- load a font into the font object
        f:DrawString("Hello World!",60,50,KColor(1,1,1,1),0,true) -- render string with loaded font on position 60x50y

    ```

___
## Functions
### Draw·String () {: aria-label='Functions' }
[ ](#){: .rep .tooltip .badge }
#### void DrawString ( string String, float PositionX, float PositionY, [KColor](KColor.md) RenderColor, int BoxWidth = 0, boolean Center = false ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void DrawString ( string String, float PositionX, float PositionY, float sizeX, float sizeY, [KColor](KColor.md) RenderColor, [FontRenderSettings](FontRenderSettings.md) settings ) {: .copyable aria-label='Functions' }
将 UTF8 转换为 UTF16，然后在屏幕上绘制字符串.

`BoxWidth` 和 `Center` 变量可以用于对齐文本。需要注意以下几点:

* 如果 `BoxWidth` 为零，文本将左对齐，`Center` 参数会被忽略.
* 如果 `BoxWidth` **不为零**，且 `Center` 参数为 `false`，则文本会在 `BoxWidth` 范围内右对齐.
* 如果 `BoxWidth` **不为零**，且 `Center` 参数为 `true`，则文本会在 `BoxWidth` 范围内居中对齐.

???- bug "Bug"
    如果调用此函数时 `String` 或 `RenderColor` 参数为 `nil`，游戏会崩溃.

???- example "Example Code"

    Example usage.

    ```lua

        -- In an initialization function:
        local f = Font() -- init font object
        f:Load("font/terminus.fnt") -- load a font into the font object

        -- In a render function on every frame:
        f:DrawString("Hello World!",60,50,KColor(1,1,1,1),0,true) -- render string with loaded font on position (60, 50)

    ```

___
### Draw·String·Scaled () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void DrawStringScaled ( string String, float PositionX, float PositionY, float ScaleX, float ScaleY, [KColor](KColor.md) RenderColor, int BoxWidth = 0, boolean Center = false ) {: .copyable aria-label='Functions' }
将 UTF8 转换为 UTF16，然后在屏幕上绘制缩放后的字符串.

???- bug "Bug"
    如果调用此函数时 `String`  或 `RenderColor` 参数为 `nil` ，游戏会崩溃.

???- example "Example Code"

    Example usage.

    ```lua

        local f = Font() -- init font object
        f:Load("font/terminus.fnt") -- load a font into the font object
        f:DrawStringScaled("Hello World!",60,50,0.5,0.5,KColor(1,1,1,1),0,true) -- render string with loaded font on position 60x50y

    ```

___
### Draw·String·Scaled·UTF8 () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void DrawStringScaledUTF8 ( string String, float PositionX, float PositionY, float ScaleX, float ScaleY, [KColor](KColor.md) RenderColor, int BoxWidth = 0, boolean Center = false ) {: .copyable aria-label='Functions' }
在屏幕上绘制缩放后的 Unicode 文本字符串.

???- bug "Bug"
    如果调用此函数时 `String`  或 `RenderColor` 参数为 `nil` ，游戏会崩溃.

???- example "Example Code"

    Example usage.

    ```lua

        local f = Font() -- init font object
        f:Load("font/terminus.fnt") -- load a font into the font object
        f:DrawStringScaledUTF8("Hello World!",60,50,0.5,0.5,KColor(1,1,1,1),0,true) -- render string with loaded font on position 60x50y

    ```

___
### Draw·String·UTF8 () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void DrawStringUTF8 ( string String, float PositionX, float PositionY, [KColor](KColor.md) RenderColor, int BoxWidth = 0, boolean Center = false ) {: .copyable aria-label='Functions' }
在屏幕上绘制一串 Unicode 文本.

`BoxWidth` 和 `Center` 参数可用于对齐文本，注意如下:

* 如果 `BoxWidth` 为零，文本将左对齐，`Center` 参数会被忽略.
* 如果 `BoxWidth` **不为零**，且 `Center` 参数为 `false`，则文本会在 `BoxWidth` 范围内右对齐.
* 如果 `BoxWidth` **不为零**，且 `Center` 参数为 `true`，则文本会在 `BoxWidth` 范围内居中对齐.

???- bug "Bug"
    如果调用此函数时 `String` 或 `RenderColor` 参数为 `nil`，游戏会崩溃。

???- example "Example Code"

    Example usage.

    ```lua

        local f = Font() -- init font object
        f:Load("font/terminus.fnt") -- load a font into the font object
        f:DrawStringUTF8("Hello World!",60,50,KColor(1,1,1,1),0,true) -- render string with loaded font on position 60x50y

    ```

___
### Get·Baseline·Height () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetBaselineHeight ( ) {: .copyable aria-label='Functions' }
返回从行的绝对顶部到字符基线的像素数(基准高度).
___
### Get·Character·Width () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetCharacterWidth ( char Character ) {: .copyable aria-label='Functions' }
返回指定字符的像素宽度.
___
### Get·Line·Height () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetLineHeight ( ) {: .copyable aria-label='Functions' }
返回每行文本之间的像素距离(行高度).
___
### Get·String·Width () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetStringWidth ( string String ) {: .copyable aria-label='Functions' }
将字符串从 UTF8 转换为 UTF16，并返回该字符串的像素宽度.

???- bug "Bug"
    如果调用此函数时参数为 `nil`，游戏会崩溃.
___
### Get·String·Width·UTF8 () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetStringWidthUTF8 ( string String ) {: .copyable aria-label='Functions' }
返回 Unicode 文本的像素宽度.
___
### Is·Loaded () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsLoaded ( ) {: .copyable aria-label='Functions' }
返回字体是否已被加载.
___
### Load () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Load ( string FilePath ) {: .copyable aria-label='Functions' }
加载字体。要检查字体是否实际加载成功，可随后调用 [IsLoaded()](#isloaded) 方法.

???- bug "Bug"
    加载自定义字体时，传递给此函数的路径实际上是相对于游戏的 `resources` 文件夹，而不是你的 mod 的 `resources` 文件夹，这与 [`Sprite:Load()`](./Sprite.md#load) 等函数的行为不一致。你可以用如下代码加载自定义字体：

    ```lua
    local MOD_FOLDER_NAME = "mymod" -- change to your mod's directory. note that this can be different depending on how the mod was downloaded: if downloaded from the steam workshop, it will have an underscore with the mod's steam id at the end (e.g. "mymod_12345")
    local CUSTOM_FONT_FILE_PATH = "font/mycoolfont.fnt" -- relative to your "resources" folder

    local customFont = Font()
    customFont:Load("mods/" .. MOD_FOLDER_NAME .. "/resources/" .. CUSTOM_FONT_FILE_PATH)
    ```

???- example "Example Code"

    Example usage.

    ```lua

        local f = Font() -- init font object
        f:Load("font/terminus.fnt") -- load a font into the font object
        f:DrawString("Hello World!", 60, 50, KColor.White, 0, true) -- render string with loaded font on position 60x50y

    ```

___
### Set·Missing·Character () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetMissingCharacter ( char MissingCharacter ) {: .copyable aria-label='Functions' }
设置当字体遇到缺失字符时所使用的字符.
___
### Unload () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Unload ( ) {: .copyable aria-label='Functions' }
从内存中卸载字体.
___
