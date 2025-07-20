---
tags:
  - Globals
  - Class
---
# Global Class "Input"

???+ info
    你可以通过 `Input` 全局表来获取这个类。

    **请注意，调用这些函数时，必须使用 `.`（句点）而不是 `:`（冒号）！**

    ???+ example "Example Code"
        ```lua
        local mousePos = Input.GetMousePosition(true)
        ```

## Functions
### Get·Action·Value () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### float GetActionValue ( int action, int controllerId ) {: .copyable aria-label='Functions' }

返回按钮被按下的当前力度。对于键盘而言，这个值为 0 或 1。对于手柄（控制器），此函数可用于获取在某个方向上移动模拟摇杆的力度.

???- example "Example Code"

    此代码会打印模拟摇杆向左移动的当前“力度”.

    ```lua
    print(Input.GetActionValue(ButtonAction.ACTION_LEFT, 1))
    ```

___
### Get·Button·Value () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### float GetButtonValue ( int button, int controllerId ) {: .copyable aria-label='Functions' }

请使用 "GetActionValue" 函数代替此函数.
___
### Get·Mouse·Position () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### [Vector](Vector.md) GetMousePosition ( boolean gameCoords ) {: .copyable aria-label='Functions' }

返回鼠标当前在游戏坐标（传入 true）或渲染坐标中的位置.

???- example "Example Code"

    此代码会在当前鼠标位置渲染 “Hello World!”.

    ```lua
    local mousePos = Input.GetMousePosition(true) -- get mouse position in world coordinates
    local screenPos = Isaac.WorldToScreen(mousePos) -- transfer game- to screen coordinates
    Isaac.RenderText("Hello World!", screenPos.X, screenPos.Y, 1 ,1 ,1 ,1 )
    ```

___
### Is·Action·Pressed () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### boolean IsActionPressed ( int action, int controllerId ) {: .copyable aria-label='Functions' }

返回某个动作按钮是否被按下。动作按钮是指任何被分配了默认功能的按钮。只要按钮被按住，此函数就会返回 true.

[所有动作枚举列表](enums/ButtonAction.md)

???- example "Example Code"

    此代码会在任何被分配了 “放置炸弹” 功能的按钮被按下时，打印 “bomb Button pressed”.

    ```lua
    if Input.IsActionPressed(ButtonAction.ACTION_BOMB, 0)  then
        print("bomb Button pressed")
    end
    ```
___
### Is·Action·Triggered () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### boolean IsActionTriggered ( int action, int controllerId ) {: .copyable aria-label='Functions' }

返回某个动作按钮是否在之前的某个时间被按下。动作按钮是指任何被分配了默认功能的按钮。只有在按钮被按下时，此函数才会返回 true。在你调用此函数并尝试在下一个更新周期（例如在下一个渲染周期）再次调用它时，它将不再返回 true.

[所有动作枚举列表](enums/ButtonAction.md)

???- example "Example Code"

    此代码会在任何被分配了 “放置炸弹” 功能的按钮被按下时，打印 “bomb Button pressed”.

    ```lua
    if Input.IsActionTriggered(ButtonAction.ACTION_BOMB, 0)  then
        print("bomb Button pressed")
    end
    ```
___
### Is·Button·Pressed () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### boolean IsButtonPressed ( int button, int controllerId ) {: .copyable aria-label='Functions' }

返回某个按钮是否被按下。只要按钮被按住，此函数就会返回 true.

[所有键盘枚举列表](enums/Keyboard.md)

???- example "Example Code"

    此代码会在 “Enter” 键被按下时，打印 “Enter Button pressed”.

    ```lua
    if Input.IsButtonPressed(Keyboard.KEY_ENTER, 0)  then
        print("Enter Button pressed.")
    end
    ```
___
### Is·Button·Triggered () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### boolean IsButtonTriggered ( int button, int controllerId ) {: .copyable aria-label='Functions' }

返回某个按钮是否在之前的某个时间被按下。只有在按钮被按下时，此函数才会返回 true。在你调用此函数并尝试在下一个更新周期（例如在下一个渲染周期）再次调用它时，它将不再返回 true.

[List of all Keyboard enums](enums/Keyboard.md)

???- example "Example Code"

    此代码会在 “Enter” 键被按下时，打印 “Enter Button was pressed”.

    ```lua
    if Input.IsButtonTriggered(Keyboard.KEY_ENTER, 0)  then
        print("Enter Button was pressed.")
    end
    ```
___
### Is·Mouse·Btn·Pressed () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### boolean IsMouseBtnPressed ( [Mouse](enums/Mouse.md) button ) {: .copyable aria-label='Functions' }

返回某个鼠标按钮是否被按下。
左键：0，右键：1，鼠标滚轮：2，后退按钮：3，前进按钮：4

???- example "Example Code"

    此代码会在鼠标 “右键” 被按下时，打印 “Right Click”.

    ```lua
    if Input.IsMouseBtnPressed(Mouse.MOUSE_BUTTON_2)  then
        print("Right Click")
    end
    ```

___
