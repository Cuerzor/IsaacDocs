---
tags:
  - Globals
  - Class
---
# Class "Sprite"

???+ info
    此类可通过其构造函数或以下函数访问:

    * [Entity.GetSprite()](Entity.md#getsprite)
    * [GridEntity.GetSprite()](GridEntity.md#getsprite)
    * [GridEntityDoor.ExtraSprite](GridEntityDoor.md#extrasprite)
    * [GridEntityPressurePlate.TimerPlate](GridEntityPressurePlate.md#timerplate)

    ???+ example "Example Code"
        ```lua
        local mySprite = Sprite()
        ```

## Constructors
### Sprite () {: aria-label='Constructors' }
[ ](#){: .alldlc .tooltip .badge }
#### [Sprite](Sprite.md) Sprite ( ) {: .copyable aria-label='Constructors' }

___
## Functions
### Get·Animation () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### string GetAnimation ( ) {: .copyable aria-label='Functions' }
返回当前正在播放的动画的名称.

___
### Get·Default·Animation () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### string GetDefaultAnimation ( ) {: .copyable aria-label='Functions' }
从当前加载的 anm2 文件中返回 `DefaultAnimation` 的值.

此函数似乎与 `GetDefaultAnimationName()` 相同.

???- example "Example Code"
    This code print the default animation name "WalkDown" of the player sprite.

    ```lua
    local player = Isaac.GetPlayer()
    local sprite = player:GetSprite()
    print(sprite:GetDefaultAnimation()) -- this prints "WalkDown"
    ```

___
### Get·Default·Animation·Name () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### string GetDefaultAnimationName ( ) {: .copyable aria-label='Functions' }
从当前加载的 anm2 文件中返回 `DefaultAnimation` 的值.

此函数似乎与 `GetDefaultAnimation()` 相同.

???- example "Example Code"
    This code print the default animation name "WalkDown" of the player sprite.

    ```lua
    local player = Isaac.GetPlayer()
    local sprite = player:GetSprite()
    print(sprite:GetDefaultAnimationName()) -- this prints "WalkDown"
    ```

___
### Get·Filename () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### string GetFilename ( ) {: .copyable aria-label='Functions' }
返回精灵上加载的 anm2 文件的路径.

???- example "Example Code"
    This code print the .anm2 path of the player sprite.

    ```lua
    local player = Isaac.GetPlayer()
    local sprite = player:GetSprite()
    print(sprite:GetFilename()) -- this prints "gfx/001.000_Player.anm2"
    ```

___
### Get·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetFrame ( ) {: .copyable aria-label='Functions' }
返回当前正在渲染的动画的帧序号.

___
### Get·Layer·Count () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetLayerCount ( ) {: .copyable aria-label='Functions' }
返回精灵上加载的 anm2 文件中的图层数量。所有动画使用相同数量的图层.

___
### Get·Overlay·Animation () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### string GetOverlayAnimation ( ) {: .copyable aria-label='Functions' }
返回当前播放的叠加动画的名称。（叠加动画是可以与正常动画同时播放的独立次要动画。）

___
### Get·Overlay·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetOverlayFrame ( ) {: .copyable aria-label='Functions' }
返回当前正在渲染的叠加动画的帧编号。（叠加动画是可以与正常动画同时播放的独立次要动画。）

___
### Get·Texel () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [KColor](KColor.md) GetTexel ( [Vector](Vector.md) SamplePos, [Vector](Vector.md) RenderPos, float AlphaThreshold, int LayerID = 0 ) {: .copyable aria-label='Functions' }
返回精灵在给定采样位置的像素颜色。RenderPos 可以忽略并设置为零向量

___
### Is·Event·Triggered () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsEventTriggered ( string EventName ) {: .copyable aria-label='Functions' }
如果动画中指定的事件当前正在触发，则返回 true.

___
### Is·Finished () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsFinished ( string AnimationName ) {: .copyable aria-label='Functions' }

#### boolean IsFinished ( ) {: .copyable aria-label='Functions' }
如果动画播放完成，则为true
___
### Is·Loaded () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsLoaded ( ) {: .copyable aria-label='Functions' }
如果使用Sprite:Load()加载的动画加载成功了，则为true
___
### Is·Overlay·Finished () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsOverlayFinished ( string AnimationName ) {: .copyable aria-label='Functions' }

#### boolean IsOverlayFinished ( ) {: .copyable aria-label='Functions' }
如叠加动画播放完成，则为true
___
### Is·Overlay·Playing () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsOverlayPlaying ( string AnimationName ) {: .copyable aria-label='Functions' }

#### boolean IsOverlayPlaying ( ) {: .copyable aria-label='Functions' }
根据精灵是否正在播放提供的叠加动画名称返回 true/false。名称在给定精灵的 anm2 文件中设置
___
### Is·Playing () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsPlaying ( string AnimationName ) {: .copyable aria-label='Functions' }

#### boolean IsPlaying ( ) {: .copyable aria-label='Functions' }
根据精灵是否正在播放提供的动画名称返回 true/false。名称在给定精灵的 anm2 文件中设置.

???- example "Example Code"
    This code checks the name of the current animation ("Appear" and "Idle" are used by cards), then replaces its animations with ones loaded from a custom anm2 file called "Custom_Animations.anm2", which has the same animation names.

    ```lua
	if mySprite:IsPlaying("Appear") then
		mySprite:Load("gfx/Custom_Animations.anm2", true)
		mySprite:LoadGraphics()
		mySprite:Play("Appear",true)
		mySprite:Update()
	elseif mySprite:IsPlaying("Idle") then
		mySprite:Load("gfx/Custom_Animations.anm2", true)
		mySprite:LoadGraphics()
		mySprite:Play("Idle",true)
		mySprite:Update()
	end
    ```

___
### Load () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Load ( string ANM2Path, boolean LoadGraphics ) {: .copyable aria-label='Functions' }
加载给定的 anm2 文件。每个精灵必须加载一个 anm2 文件才能显示任何内容.

- ANM2Path - 包含此精灵所有动画的 anm2 文件的路径。这应该是相对于 “resources” 文件夹的路径.
- LoadGraphics - 是否在加载 anm2 文件后自动调用`Sprite.LoadGraphics`方法.

???- example "Example Code"
    This code creates a new sprite object, loads an .anm2 file and renders it on the screen.

    ```lua
	local mySprite = Sprite()
	mySprite:Load("gfx/myCoolAnimation.anm2", true)
    mySprite:Render(Vector(75,75), Vector(0,0), Vector(0,0))
    ```

___
### Load·Graphics () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void LoadGraphics ( ) {: .copyable aria-label='Functions' }
用于加载精灵的 anm2 中指定的 PNG 文件。通常，只有在之前向`Sprite.Load`方法的`loadGraphics`参数传递了 `false`，或者调用了`Sprite.ReplaceSpritesheet`方法时，才会调用此方法.

???- example "Example Code"
    This code creates a new sprite object and replaces the spritesheet of layer 0 of a sprite object with a different spritesheet.

    ```lua
	local mySprite = Sprite()
	mySprite:Load("gfx/myCoolAnimation.anm2", true)
	mySprite:ReplaceSpritesheet(0, "gfx/my_new_spritesheet.png")
	mySprite:LoadGraphics()
    ```

___
### Play () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Play ( string AnimationName, boolean Force ) {: .copyable aria-label='Functions' }
开始执行给定的动画，从第 0 帧开始。调用此方法后，必须在每个更新帧上调用`Sprite.Update`方法（如果要在渲染回调中更新动画，请确保仅在偶数帧上运行），以便将动画推进到下一帧。（通常，您还会使用`Sprite.IsFinished`方法检查动画是否完成。）

再次调用此方法将把当前帧重置回 0.

- **Force** - 如果为 true，当前正在播放的动画（如果有）将被停止。如果为 false，并且已经有当前正在播放的动画，此方法将不执行任何操作，当前动画将继续播放.

???- example "Example Code"
    This code plays and renders a sprite.

    ```lua
    	-- Sprite objects only need to be created and loaded once.
	local mySprite = Sprite()
	mySprite:Load("gfx/myCoolAnimation.anm2", true)

	-- Execute this function only once! for example when an event is triggered
	function myPlaySpriteFunction()
		mySprite:Play("MyAnimation", true)
	end

	-- Execute this function every POST_RENDER. For example in the MC_POST_RENDER callback.
	function myRenderSpriteFunction()
		mySprite:Update()
		mySprite:Render(Vector(50,50), Vector(0,0), Vector(0,0))
	end
    ```

___
### Play·Overlay () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void PlayOverlay ( string AnimationName, boolean Force ) {: .copyable aria-label='Functions' }
开始执行给定的叠加动画，从第 0 帧开始。（叠加动画是可以与正常动画同时播放的独立次要动画。）调用此方法后，必须在每个更新帧上调用Sprite.Update方法（如果要在渲染回调中更新动画，请确保仅在偶数帧上运行），以便将动画推进到下一帧。（通常，您还会使用Sprite.IsOverlayFinished方法检查动画是否完成。）

再次调用此函数将始终把当前叠加帧重置回 0.

- **Force** - Force - 如果为 true，当前正在播放的动画（如果有）将被停止。如果为 false，并且已经有当前正在播放的动画，此方法将不执行任何操作，当前动画将继续播放.

???- example "Example Code"
    This code plays and renders an overlay sprite.

    ```lua
    	-- Sprite objects only need to be created and loaded once.
	local mySprite = Sprite()
	mySprite:Load("gfx/myCoolAnimation.anm2", true)

	-- Execute this function only once! for example when an event is triggered
	function myPlaySpriteFunction()
		mySprite:PlayOverlay("MyOverlayAnimation", true)
	end

	-- Execute this function every POST_RENDER. For example in the MC_POST_RENDER callback.
	function myRenderSpriteFunction()
		mySprite:Render(Vector(50,50), Vector(0,0), Vector(0,0))
	end
    ```

___
### Play·Random () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void PlayRandom ( int Seed ) {: .copyable aria-label='Functions' }
从当前加载的 anm2 文件中播放随机动画.

___
### Reload () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Reload ( ) {: .copyable aria-label='Functions' }
重新加载anm2文件
___
### Remove·Overlay () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveOverlay ( ) {: .copyable aria-label='Functions' }
取消执行给定的叠加动画
___
### Render () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Render ( [Vector](Vector.md) Position, [Vector](Vector.md) [Vector](Vector.md) TopLeftClamp = Vector.Zero, [Vector](Vector.md) BottomRightClamp = Vector.Zero ) {: .copyable aria-label='Functions' }
在给定的屏幕位置渲染精灵对象，其中 (0, 0) 是屏幕的左上角。

为了绘制精灵，需要在每个渲染帧上调用此函数。（例如在MC_POST_RENDER回调中。）

TopLeftClamp 和 BottomRightClamp 可用于裁剪精灵。

???- example "Example Code"
    This code renders a sprite.

    ```lua
    	-- Sprite objects only need to be created and loaded once.
	local mySprite = Sprite()
	mySprite:Load("gfx/myCoolAnimation.anm2", true)

	-- Execute this function every POST_RENDER. For example in the MC_POST_RENDER callback.
	function myRenderSpriteFunction()
		mySprite:Render(Vector(50,50))
	end
    ```

___
### Render·Layer () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void RenderLayer ( int LayerId, [Vector](Vector.md) Position, [Vector](Vector.md) TopLeftClamp = Vector.Zero, [Vector](Vector.md) BottomRightClamp = Vector.Zero ) {: .copyable aria-label='Functions' }
在给定的屏幕位置渲染精灵的特定图层，其中 (0,0) 是屏幕的左上角。

这与Sprite.Render方法类似，但它只会渲染精灵的特定图层，而不是一次渲染所有图层。

TopLeftClamp 和 BottomRightClamp 可用于裁剪精灵。

???- example "Example Code"
    This code renders layer 3 of a sprite. Layer IDs in most cases start at index 0!

    ```lua
    	-- Sprite objects only need to be created and loaded once.
	local mySprite = Sprite()
	mySprite:Load("gfx/myCoolAnimation.anm2", true)

	-- Execute this function every POST_RENDER. For example in the MC_POST_RENDER callback.
	function myRenderSpriteFunction()
		mySprite:RenderLayer(2, Vector(50,50))
	end
    ```
___
### Replace·Spritesheet () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### boolean ReplaceSpritesheet ( int LayerId, string PngFilename ) {: .copyable aria-label='Functions' }
更改与精灵特定图层关联的 “.png” 文件。这不会更改使用正在被替换的 “.png” 文件的其他图层。

替换精灵表后，必须随后调用`Sprite.LoadGraphics`方法.

In Repentance+, this returns `true` if the spritesheet at the given layer id was successfully replaced *and* if the new spritesheet is not the same as the old one, otherwise returns `false`.

???- example "Example Code"
    This code creates a new sprite object and replaces the spritesheet of layer 0 of a sprite object with a different spritesheet.

    ```lua
	local mySprite = Sprite()
	mySprite:Load("gfx/myCoolAnimation.anm2", true)
	mySprite:ReplaceSpritesheet(0, "gfx/my_new_spritesheet.png")
	mySprite:LoadGraphics()
    ```

___
### Reset () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Reset ( ) {: .copyable aria-label='Functions' }

___
### Set·Animation () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean SetAnimation ( string AnimationName, boolean Reset = true ) {: .copyable aria-label='Functions' }

与`Sprite.Play`方法类似，但不会启动动画.

- **Reset** - 为 false 时将从当前帧继续动画。这对于动态在不同 FloatDirection 动画之间交替的随从以及其他遵循类似行为的实体来说是一个非常好的工具.

___
### Set·Frame () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void SetFrame ( int FrameNum ) {: .copyable aria-label='Functions' }
#### void SetFrame ( string AnimationName, int FrameNum ) {: .copyable .secondH4 aria-label='Functions' }

将当前动画更改为特定帧。

请注意，通常，您会使用`Sprite.Update`方法自动迭代精灵的动画帧。因此，此方法通常用于不播放动画的精灵。

`Sprite.SetFrame`方法有两个重载：一个支持同时设置动画，另一个使用当前正在播放的动画。


___
### Set·Last·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetLastFrame ( ) {: .copyable aria-label='Functions' }

将当前播放的动画设置为其最后一帧.
___
### Set·Layer·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetLayerFrame ( int LayerId, int FrameNum ) {: .copyable aria-label='Functions' }

___
### Set·Overlay·Animation () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean SetOverlayAnimation ( string AnimationName, bool Reset = true ) {: .copyable aria-label='Functions' }

与`Sprite.PlayOverlay`方法类似，但不会启动动画.

- **Reset** - 为 false 时将从当前帧继续动画。这对于动态在不同 FloatDirection 动画之间交替的随从以及其他遵循类似行为的实体来说是一个非常好的工具.

___
### Set·Overlay·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetOverlayFrame ( string AnimationName, int FrameNum ) {: .copyable aria-label='Functions' }

___
### Set·Overlay·Render·Priority () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetOverlayRenderPriority ( boolean RenderFirst ) {: .copyable aria-label='Functions' }

___
### Stop () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Stop ( ) {: .copyable aria-label='Functions' }

___
### Update () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Update ( ) {: .copyable aria-label='Functions' }

将当前播放的动画推进一帧.

___
### Was·Event·Triggered () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean WasEventTriggered ( string EventName ) {: .copyable aria-label='Functions' }
如果动画中指定的事件在某个时刻被触发，则返回 true，并在动画停止播放前保持为 true.

___
## Variables
### Color {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Color](Color.md) Color  {: .copyable aria-label='Variables' }

___
### FlipX {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean FlipX  {: .copyable aria-label='Variables' }

___
### FlipY {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean FlipY  {: .copyable aria-label='Variables' }

___
### Offset {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) Offset  {: .copyable aria-label='Variables' }

___
### Playback·Speed {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float PlaybackSpeed  {: .copyable aria-label='Variables' }

___
### Rotation {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Rotation  {: .copyable aria-label='Variables' }

___
### Scale {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) Scale  {: .copyable aria-label='Variables' }

___
