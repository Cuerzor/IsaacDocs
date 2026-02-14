---
tags:
  - Globals
  - Class
---
# Class "FontRenderSettings"

???+ info
    
    此类在 Repentance+ 版本中新增，用于 [Font:DrawString()](Font.md#drawstring) 函数中定义文本渲染的特殊行为。

        可以通过其构造函数访问该类：

    ???+ example "Example Code"

        ```lua

            local settings = FontRenderSettings()

        ```

## Constructors
### FontRenderSettings () {: aria-label='Constructors' }
[ ](#){: .repplus .tooltip .badge }
#### [FontRenderSettings](FontRenderSettings.md) FontRenderSettings ( ) {: .copyable aria-label='Constructors' }

返回一个 FontRenderSettings 对象。

???- example "Example Code"

    Example usage:

    ```lua

        local settings = FontRenderSettings()
        settings:EnableAutoWrap()
        --returns true if the font settings have autowrap enabled

    ```
___

## Functions
### Enable·Auto·Wrap () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void EnableAutoWrap ( boolean enabled ) {: .copyable aria-label='Functions' }

___
### Enable·Truncation () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void EnableTruncation ( boolean enabled ) {: .copyable aria-label='Functions' }

___
### Get·Alignment () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### [DrawStringAlignment](enums/DrawStringAlignment.md) GetAlignment ( ) {: .copyable aria-label='Functions' }

___
### Get·Line·Height·Modifier () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### float GetLineHeightModifier ( ) {: .copyable aria-label='Functions' }

___
### Get·Max·Characters () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### int GetMaxCharacters ( ) {: .copyable aria-label='Functions' }

___
### Get·Missing·Character·Override () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### int GetMissingCharacterOverride ( ) {: .copyable aria-label='Functions' }

___
### Is·Auto·Wrap·Enabled () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### boolean IsAutoWrapEnabled ( ) {: .copyable aria-label='Functions' }

___
### Is·Truncation·Enabled () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### boolean IsTruncationEnabled ( ) {: .copyable aria-label='Functions' }

___
### Set·Alignment () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void SetAlignment ( [DrawStringAlignment](enums/DrawStringAlignment.md) alignment ) {: .copyable aria-label='Functions' }

___
### Set·Line·Height·Modifier () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void SetLineHeightModifier ( float value ) {: .copyable aria-label='Functions' }

___
### Set·Max·Characters () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void SetMaxCharacters ( int maxChars ) {: .copyable aria-label='Functions' }

___
### Set·Missing·Character·Override () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void SetMissingCharacterOverride ( int character ) {: .copyable aria-label='Functions' }
设置当需要渲染的字符缺失时所用的默认字符。此设置会覆盖之前的 [Font:SetMissingCharacter()](Font.md#setmissingcharacter) 配置.

___
