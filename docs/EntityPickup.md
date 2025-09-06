---
tags:
  - Class
---
# Class "EntityPickup"

???+ info

    你可以通过以下函数获取此类：

    * [Entity.ToPickup()](Entity.md#topickup)

    ???+ example "Example Code"
        `local entity = Isaac.GetRoomEntities()[1]:ToPickup()`

## Class Diagram
--8<-- "docs/snippets/EntityClassDiagram.md"
## Functions
### Appear·Fast () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AppearFast ( ) {: .copyable aria-label='Functions' }

___
### Can·Reroll () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanReroll ( ) {: .copyable aria-label='Functions' }

___
### Get·Coin·Value () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetCoinValue ( ) {: .copyable aria-label='Functions' }
If this is a coin, return its face value, else zero.
___
### Is·Shop·Item () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsShopItem ( ) {: .copyable aria-label='Functions' }

___
### Morph () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void Morph ( [EntityType](enums/EntityType.md) Type, int Variant, int SubType, boolean KeepPrice = false, boolean KeepSeed = false, boolean IgnoreModifiers = false ) {: .copyable aria-label='Functions' }

**KeepSeed**: 如果设置为 true，将保留拾取物的初始 RNG 种子，而不是重置它

**IgnoreModifiers**: 如果设置为true，将忽略可能将此拾取物转变为其他类型的物品效果。具体来说，这可以用来防止道具受到堕化以撒的额外选择机制的影响。（例如，如果您手动生成一个任务道具，例如 Polaroid，它将受到堕化以撒的机制的影响，这通常是不可取的。要解决此问题，您可以在生成后立即将其变形为相同的实体类型/变体/子类型，并将此参数设置为 true。）
___
### Play·Drop·Sound () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void PlayDropSound ( ) {: .copyable aria-label='Functions' }

___
### Play·Pickup·Sound () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void PlayPickupSound ( ) {: .copyable aria-label='Functions' }

___
### Try·Open·Chest () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean TryOpenChest ( [EntityPlayer](EntityPlayer.md) Player = nil ) {: .copyable aria-label='Functions' }
**Player**: The player that opened this chest
___
## Variables
### Auto·Update·Price {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean AutoUpdatePrice  {: .copyable aria-label='Variables' }

___
### Charge {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int Charge  {: .copyable aria-label='Variables' }

___
### OptionsPickupIndex {: aria-label='Variables' }
[ ](#){: .reporplus .tooltip .badge }
#### int OptionsPickupIndex  {: .copyable aria-label='Variables' }

任何非 0 的值都会导致该物品与任何其他具有相同 OptionsPickupIndex 值的物品形成选项组。

当属于选项组的物品被拾取时，所有属于同一组的其他物品都会消失。

0 是默认值，表示该物品不属于任何组。
___
### Price {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int Price  {: .copyable aria-label='Variables' }
该物品在商店中的价格。

???- info "堕化店长信息"

    在堕化店长身上，所有物品都应该有一个价格。但是，任何使用 Lua 生成的物品都不符合此规则，因此您必须手动设置价格。在分配价格的下一帧（例如 `1`）之后，它将自动调整为堕化店长的正确价格（例如 15）。这是由于 AutoUpdatePrice 功能造成的。

    该方法在大多数情况下都有效。然而，它在特殊房间（例如天使房）中会出现问题，有时价格会跳到错误的值，例如 24、99 等。解决此问题的方法是将 ShopItemId 设置为任意负值（例如 -1）。

___
### Shop·Item·Id {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int ShopItemId  {: .copyable aria-label='Variables' }

如果在商店中, 这个值描述了这个物品在商店的哪一个槽中售卖。例如，如果商店有 6 个待售物品，则房间中的拾取物将具有 0、1、2、3、4 和 5 的商店物品 ID。

当生成一个新的道具时，ShopItemId 默认为 0。这会导致 D6 将道具重置为红心。通过将商店物品 ID 设置为 -1，可以修复此行为，使道具正确重置为另一个道具。然而，非道具可能会通过 D20 或类似物品重置为道具。

通过将商店物品 ID 设置为 -2，自动价格将为恶魔交易价格。否则，这与 -1 相同。

其他负值的行为与 -1 相同。

___
### State {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int State  {: .copyable aria-label='Variables' }

___
### Timeout {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int Timeout  {: .copyable aria-label='Variables' }

使拾取物在一段时间后闪烁并消失，就像堕化玛姬掉落的临时生命值一样。该值每帧减少 1，达到 0 后拾取物消失。如果 Timeout 设置为 -1（正常拾取物的默认值），则拾取物将正常工作而不会消失。

___
### Touched {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean Touched  {: .copyable aria-label='Variables' }

___
### Wait {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int Wait  {: .copyable aria-label='Variables' }

被用于道具，以强制执行一段时间，期间玩家将不会自动拾取道具。新的道具生成时，`Wait` 值为 20（对应于 20 帧游戏时间）。该值会随着游戏帧的推移而自动减少。

目前尚不清楚此值是否用于其他类型的拾取物。

___
