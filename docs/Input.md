---
tags:
  - Globals
  - Class
---
# Global Class "Input"

???+ info
    你可以通过 `Input` 全局表来获取这个类.

    **请注意，调用这些函数时，必须使用 `.`（句点）而不是 `:`（冒号）！**

    ???+ example "Example Code"

        ```lua

        local mousePos = Input.GetMousePosition(true)

        ```

## Functions
### Get·Action·Value () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### float GetActionValue ( [ButtonAction](enums/ButtonAction.md) action, int controllerId ) {: .copyable aria-label='Functions' }

返回按钮被按下的当前力度。使用键盘时，该值为 0 或 1。使用控制器时，可用于获取模拟摇杆向某个方向移动的力度.

???- example "Example Code"

    此代码打印模拟摇杆向左移动的当前 “力度”.

    ```lua

    print(Input.GetActionValue(ButtonAction.ACTION_LEFT, 1))

    ```

___
### Get·Button·Value () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### float GetButtonValue ( [Keyboard](enums/Keyboard.md) button, int controllerId ) {: .copyable aria-label='Functions' }

请使用 "GetActionValue" 函数代替此函数.
___
### Get·Mouse·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetMousePosition ( boolean gameCoords ) {: .copyable aria-label='Functions' }

返回当前鼠标在游戏坐标（true）或渲染坐标中的位置.

???- example "Example Code"

    此代码在当前鼠标位置渲染 “Hello World!”.

    ```lua

    local mousePos = Input.GetMousePosition(true) -- get mouse position in world coordinates
    local screenPos = Isaac.WorldToScreen(mousePos) -- transfer game- to screen coordinates
    Isaac.RenderText("Hello World!", screenPos.X, screenPos.Y, 1 ,1 ,1 ,1 )

    ```

___
### Is·Action·Pressed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsActionPressed ( [ButtonAction](enums/ButtonAction.md) action, int controllerId ) {: .copyable aria-label='Functions' }

返回某个动作按钮是否被按下。动作按钮是指任何被分配了默认功能的按钮。只要按钮被按住，此函数就会返回 true.

[List of all Action enums](enums/ButtonAction.md)

???- example "Example Code"

    此代码在任何被分配给 “放置炸弹” 功能的按钮被按下时，打印 “bomb Button pressed”.

    ```lua

    if Input.IsActionPressed(ButtonAction.ACTION_BOMB, 0)  then
        print("bomb Button pressed")
    end

    ```
___
### Is·Action·Triggered () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsActionTriggered ( [ButtonAction](enums/ButtonAction.md) action, int controllerId ) {: .copyable aria-label='Functions' }

返回某个动作按钮在之前某个时间是否被按下。动作按钮是指任何被分配了默认功能的按钮。只有当按钮被按下时，此函数才会返回 true。在你调用此函数并尝试在下一个更新周期（例如在下一个渲染周期）再次调用时，它将不再返回 true.

[所有动作枚举列表](enums/ButtonAction.md)

???- example "Example Code"

    此代码在任何被分配给 “放置炸弹” 功能的按钮被按下时，打印 “bomb Button pressed”.

    ```lua

    if Input.IsActionTriggered(ButtonAction.ACTION_BOMB, 0)  then
        print("bomb Button pressed")
    end

    ```
___
### Is·Button·Pressed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsButtonPressed ( [Keyboard](enums/Keyboard.md) button, int controllerId ) {: .copyable aria-label='Functions' }

返回某个按钮是否被按下。只要按钮被按住，此函数就会返回 true.

[所有键盘枚举列表](enums/Keyboard.md)

???- example "Example Code"

    此代码在 “Enter” 按钮被按下时，打印 “Enter Button pressed”.

    ```lua

    if Input.IsButtonPressed(Keyboard.KEY_ENTER, 0)  then
        print("Enter Button pressed.")
    end

    ```
___
### Is·Button·Triggered () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsButtonTriggered ( [Keyboard](enums/Keyboard.md) button, int controllerId ) {: .copyable aria-label='Functions' }

返回某个按钮在之前某个时间是否被按下。只有当按钮被按下时，此函数才会返回 true。在你调用此函数并尝试在下一个更新周期（例如在下一个渲染周期）再次调用时，它将不再返回 true.

[所有键盘枚举列表](enums/Keyboard.md)

???- example "Example Code"

    此代码在 “Enter” 按钮被按下时，打印 “Enter Button was pressed”.

    ```lua

    if Input.IsButtonTriggered(Keyboard.KEY_ENTER, 0)  then
        print("Enter Button was pressed.")
    end

    ```
___
### Is·Mouse·Btn·Pressed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsMouseBtnPressed ( [Mouse](enums/Mouse.md) button ) {: .copyable aria-label='Functions' }

返回某个鼠标按钮是否被按下.
左键：0，右键：1，鼠标滚轮：2，后退按钮：3，前进按钮：4

???- example "Example Code"

    此代码在 “右键” 鼠标按钮被按下时，打印 “Right Click”.

    ```lua

    if Input.IsMouseBtnPressed(Mouse.MOUSE_BUTTON_2)  then
        print("Right Click")
    end

    ```

___
