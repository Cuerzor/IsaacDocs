---
tags:
  - Class
  - Player
---
# Class "EntityPlayer"

???+ info
    你可以通过以下函数获取此类：

    * [Entity.ToPlayer()](Entity.md#toplayer)
    * [EntityFamiliar.Player](EntityFamiliar.md#player)
    * [EntityPlayer.GetMainTwin()](EntityPlayer.md#getmaintwin)
    * [EntityPlayer.GetOtherTwin()](EntityPlayer.md#getothertwin)
    * [EntityPlayer.GetSubPlayer()](EntityPlayer.md#getsubplayer)
    * [Game.GetNearestPlayer()](Game.md#getnearestplayer)
    * [Game.GetPlayer()](Game.md#getplayer)
    * [Game.GetRandomPlayer()](Game.md#getrandomplayer)
    * [Isaac.GetPlayer()](Isaac.md#getplayer)

    ???+ example "Example Code"
        `local player = Isaac.GetPlayer()`

## Class Diagram
--8<-- "docs/snippets/EntityClassDiagram.md"
## Functions
### Add·Black·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddBlackHearts ( int BlackHearts ) {: .copyable aria-label='Functions' }

给玩家添加黑心。1个单位是半颗心。用负数移除它们。

???- example "Example Code"

    This code adds 1 full black heart to the player.

    ```lua
    Isaac.GetPlayer():AddBlackHearts(2)
    ```

___
### Add·Blood·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddBloodCharge ( int Amount ) {: .copyable aria-label='Functions' }

给玩家添加血量充能。血量充能在除堕化伯大妮以外的角色上没有任何作用。

___
### Add·Blue·Flies () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) AddBlueFlies ( int Amount, [Vector](Vector.md) Position, [Entity](Entity.md) Target ) {: .copyable aria-label='Functions' }
???- info "Amount"

    饰品**鱼尾**将始终将此函数添加的苍蝇数量加倍。

___
### Add·Blue·Spider () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) AddBlueSpider ( [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' }

???- example "Example Code"

    This code spawns 3 blue spiders at the player's position.

    ```lua
    local player = Isaac.GetPlayer()
    for _ = 1, 3 do
	player:AddBlueSpider(player.Position)
    end
    ```

___
### Add·Bombs () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddBombs ( int Amount ) {: .copyable aria-label='Functions' }

给玩家添加炸弹。用负数移除它们。

???- example "Example Code"

    This code removes 1 bomb from the player.

    ```lua
    Isaac.GetPlayer():AddBombs(-1)
    ```

___
### Add·Bone·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddBoneHearts ( int Hearts ) {: .copyable aria-label='Functions' }

给玩家添加骨心。1个单位是单颗骨心。用负数移除它们。

???- example "Example Code"

    This code adds 1 bone heart to the player.

    ```lua
    Isaac.GetPlayer():AddBoneHearts(1)
    ```

___
### Add·Broken·Hearts () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddBrokenHearts ( int BrokenHearts ) {: .copyable aria-label='Functions' }

给玩家添加碎心。1个单位是单颗碎心。用负数移除它们。

???- example "Example Code"

    This code adds 1 broken heart to the player, then takes it away.

    ```lua
    Isaac.GetPlayer():AddBrokenHearts(1)
    Isaac.GetPlayer():AddBrokenHearts(-1)
    ```
___
### Add·Cache·Flags () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddCacheFlags ( [CacheFlag](enums/CacheFlag.md) CacheFlag ) {: .copyable aria-label='Functions' }

在下一次缓存重新计算中，将重新计算提供的缓存标志。

???- example "Example Code"

    This code will add several cacheflags.

    ```lua
    Isaac.GetPlayer():AddCacheFlags(CacheFlag.CACHE_DAMAGE | CacheFlag.CACHE_FIREDELAY | CacheFlag.CACHE_LUCK)
    ```
___
### Add·Card () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddCard ( [Card](enums/Card.md) ID ) {: .copyable aria-label='Functions' }

___
### Add·Coins () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddCoins ( int Amount ) {: .copyable aria-label='Functions' }

给玩家添加金币。用负数移除它们。

???- example "Example Code"

    This code adds 1 coin to the player.

    ```lua
    Isaac.GetPlayer():AddCoins(1)
    ```

___
### Add·Collectible () {: aria-label='Functions' }
[ ](#){: .rep .tooltip .badge }
#### void AddCollectible ( [CollectibleType](enums/CollectibleType.md) Type, int Charge = 0, boolean FirstTimePickingUp = true, [ActiveSlot](enums/ActiveSlot.md) Slot = ActiveSlot.SLOT_PRIMARY, int VarData = 0) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddCollectible ( [CollectibleType](enums/CollectibleType.md) Type, int Charge = 0, boolean FirstTimePickingUp = true, [ActiveSlot](enums/ActiveSlot.md) Slot = ActiveSlot.SLOT_PRIMARY, int VarData = 0, [ItemPoolType](enums/ItemPoolType.md) PoolType ) {: .copyable aria-label='Functions' }


设置 **FirstTimePickingUp** 为false 将不会添加物品的消耗品（钥匙、炸弹等），并且不会计入套装。

- Slot 0 是默认值 (normal active item)
- Slot 1 是 Schoolbag 使用的
- Slot 2 是用于口袋主动物品的

???- note "Notes"

	Slot 2 不能被用于开始时没有口袋主动物品的角色

VarData is used for the storage of a persistent context-sensitive value

???- note "Notes"

    这是一个使用 VarData 的所有物品的列表：

    - 魂火罐: 魂火会在下一次使用时生成 (最大12)
	- 无限骰, 空白卡, 透明符文, 安慰剂: 当前最大充能 (任何大于0的值)
	- Hold: 存储的便便
	    - 便便类型:
	    - [0] 无
	    - [1] 普通
	    - [2] 苍蝇
	    - [3] 火焰
	    - [4] 石化
	    - [5] 有毒
	    - [6] 黑色
	    - [7] 神圣
	    - [8] X-Lax
	    - [9] Fart
	    - [10] Bomb
	    - [11] Explosive Diarrhea
	    - [12+] Empty

___
### Add·Controls·Cooldown () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddControlsCooldown ( int Cooldown ) {: .copyable aria-label='Functions' }

___
### Add·Costume () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddCostume ( [ItemConfigItem](ItemConfig_Item.md) Item, boolean ItemStateOnly ) {: .copyable aria-label='Functions' }

___
### Add·Curse·Mist·Effect () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddCurseMistEffect ( ) {: .copyable aria-label='Functions' }

___
### Add·Dead·Eye·Charge () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddDeadEyeCharge ( ) {: .copyable aria-label='Functions' }

___
### Add·Dollar·Bill·Effect () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddDollarBillEffect ( ) {: .copyable aria-label='Functions' }

___
### Add·Eternal·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddEternalHearts ( int EternalHearts ) {: .copyable aria-label='Functions' }

给玩家添加永恒之心。1个单位是半颗心。用负数移除它们。

（注意，当你拥有超过一个时，永恒之心会自动变为完整的心。）

???- example "Example Code"

    This code adds 1 eternal heart to the player.

    ```lua
    Isaac.GetPlayer():AddEternalHearts(1)
    ```

___
### Add·Friendly·Dip () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddFriendlyDip ( int Subtype, [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' }

???- note "Dip Subtypes"

    ```lua
    0: normal
    1: red
    2: corny
    3: golden
    4: rainbow
    5: black
    6: holy
    12: stone
    13: flaming
    14: poison
    20: brownie
    ```
___
### Add·Giga·Bombs () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddGigaBombs ( int GigaBombs ) {: .copyable aria-label='Functions' }

???- note "Notes"

    巨型炸弹不会增加炸弹计数，请确保提前增加炸弹数量！
	你不能添加超过玩家当前炸弹数量的巨型炸弹。

___
### Add·Golden·Bomb () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddGoldenBomb ( ) {: .copyable aria-label='Functions' }

___
### Add·Golden·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddGoldenHearts ( int Hearts ) {: .copyable aria-label='Functions' }

给玩家添加金心。1个单位是单颗金心。用负数移除它们。

???- example "Example Code"

    This code adds 1 golden heart to the player.

    ```lua
    Isaac.GetPlayer():AddGoldenHearts(1)
    ```

___
### Add·Golden·Key () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddGoldenKey ( ) {: .copyable aria-label='Functions' }

___
### Add·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddHearts ( int Hearts ) {: .copyable aria-label='Functions' }

给玩家添加红心。如果有空的心容器，则添加红心。1个单位是半颗心。用负数移除生命值。

???- example "Example Code"

    This code adds 1 full red heart to the player.

    ```lua
    Isaac.GetPlayer():AddHearts(2)
    ```

___
### Add·Item·Wisp () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityFamiliar](EntityFamiliar.md) AddItemWisp ( [CollectibleType](enums/CollectibleType.md) Collectible, [Vector](Vector.md) Position, boolean AdjustOrbitLayer = false ) {: .copyable aria-label='Functions' }

___
### Add·Jar·Flies () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddJarFlies ( int Flies ) {: .copyable aria-label='Functions' }

___
### Add·Jar·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddJarHearts ( int Hearts ) {: .copyable aria-label='Functions' }

___
### Add·Keys () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddKeys ( int Amount ) {: .copyable aria-label='Functions' }

给玩家添加钥匙。用负数移除它们。

???- example "Example Code"

    This code adds 1 key to the player.

    ```lua
    Isaac.GetPlayer():AddKeys(1)
    ```

___
### Add·Max·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddMaxHearts ( int MaxHearts, boolean IgnoreKeeper ) {: .copyable aria-label='Functions' }

给玩家添加心容器。2个单位是一个完整的心容器。用负数移除它们。

???- note "Notes"

    可以添加半颗心容器到玩家身上。这将显示为常规心容器，但只能填充一半。

???- example "Example Code"

    This code adds 1 heart container to the player.

    ```lua
    Isaac.GetPlayer():AddMaxHearts(2, true)
    ```


???+ bug "Bugs"

    对店长无效。IgnoreKeeper 参数似乎无法按预期工作。

    最大心容器可以添加或移除到店长身上，而不管这个布尔值是什么。

    如果店长拥有贪婪的胃袋，而这个布尔值被设置为false，则无法添加最大心容器到店长身上，但可以正常移除。

    如果店长拥有贪婪的胃袋，而这个布尔值被设置为true，则可以正常添加或移除最大心容器到店长身上。

___
### Add·Minisaac () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityFamiliar](EntityFamiliar.md) AddMinisaac ( [Vector](Vector.md) Position, boolean PlayAnim = true ) {: .copyable aria-label='Functions' }

___
### Add·Null·Costume () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddNullCostume ( [NullItemID](enums/NullItemID.md) NullId ) {: .copyable aria-label='Functions' }

___
### Add·Pill () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddPill ( [PillColor](enums/PillColor.md) Pill ) {: .copyable aria-label='Functions' }

___
### Add·Player·Form·Costume () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddPlayerFormCostume ( [PlayerForm](enums/PlayerForm.md) Form ) {: .copyable aria-label='Functions' }

添加给定变身的服装。

___
### Add·Poop·Mana () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddPoopMana ( int Num ) {: .copyable aria-label='Functions' }

添加（或移除）粪便消耗品。

___
### Add·Pretty·Fly () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddPrettyFly ( ) {: .copyable aria-label='Functions' }

___
### Add·Rotten·Hearts () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddRottenHearts ( int RottenHearts ) {: .copyable aria-label='Functions' }

添加腐烂的心。1个单位是半颗心。用负数移除腐烂的心。

???- example "Example Code"

    This code adds 1 full rotten heart to the player.

    ```lua
    Isaac.GetPlayer():AddRottenHearts(2)
    ```

___
### Add·Soul·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddSoulCharge ( int Amount ) {: .copyable aria-label='Functions' }

添加灵魂充能到玩家身上。灵魂充能对除了伯大妮以外的角色没有任何作用。

___
### Add·Soul·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddSoulHearts ( int SoulHearts ) {: .copyable aria-label='Functions' }

添加魂心到玩家。1个单位是半颗心。用负数移除它们。

???- example "Example Code"

    This code adds 1 full soul heart to the player.

    ```lua
    Isaac.GetPlayer():AddSoulHearts(2)
    ```

___
### Add·Swarm·Fly·Orbital () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityFamiliar](EntityFamiliar.md) AddSwarmFlyOrbital ( [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' }

___
### Add·Trinket () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddTrinket ( [TrinketType](enums/TrinketType.md) Type, boolean FirstTimePickingUp = true ) {: .copyable aria-label='Functions' }

- 如果玩家没有任何空的饰品槽，这个函数将不做任何事情。

- 如果玩家有一个空的饰品槽但已经有一个饰品，新饰品将进入第一个槽，现有饰品将被推回到第二个槽。

- 如果提供的参数为0或其他无效的饰品ID，游戏将崩溃。

- 将**FirstTimePickingUp**设置为false将不会为该物品生成或添加拾取物，也不会导致其计入变身。

???- example "Example Code"

    This code adds the golden variant of the Swallowed Penny trinket to the player.

    ```lua
    Isaac.GetPlayer():AddTrinket(TrinketType.TRINKET_SWALLOWED_PENNY | TrinketType.TRINKET_GOLDEN_FLAG)
    ```

___
### Add·Wisp () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityFamiliar](EntityFamiliar.md) AddWisp ( [CollectibleType](enums/CollectibleType.md) Collectible, [Vector](Vector.md) Position, boolean AdjustOrbitLayer = false, boolean DontUpdate = false ) {: .copyable aria-label='Functions' }

魂火的类型可以通过Collectible来定义。如果ID与具有特殊魂火的主动物品不对应，则默认为常规蓝色魂火。

要访问特殊魂火变体，例如Delirious形式，您需要将`65536` (1 << 16)添加到ID。例如：Delirious Monstro的`id = s14`，因此魂火的ID为`65550`。

___
### Animate·Appear () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimateAppear ( ) {: .copyable aria-label='Functions' }
播放在关卡开始时通常播放的动画。
___
### Animate·Card () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AnimateCard ( [Card](enums/Card.md) ID, string AnimName = "Pickup" ) {: .copyable aria-label='Functions' }

___
### Animate·Collectible () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AnimateCollectible ( [CollectibleType](enums/CollectibleType.md) Collectible, string AnimName = "Pickup", string SpriteAnimName = "PlayerPickupSparkle" ) {: .copyable aria-label='Functions' }

`AnimName` 指 `001.000_player.anm2` 中的动画名称（例如 `Pickup` 或 `UseItem`）。 `SpriteAnimName` 指 `005.100_collectible.anm2` 中的动画名称（例如 `PlayerPickup` 或 `PlayerPickupSparkle`）。

___
### Animate·Happy () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimateHappy ( ) {: .copyable aria-label='Functions' }

播放高兴动画，当服用正面药丸时播放。

???- example "Example Code"

    This code plays the happy animation.

    ```lua
    Isaac.GetPlayer():AnimateHappy()
    ```

### Animate·Light·Travel () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimateLightTravel ( ) {: .copyable aria-label='Functions' }

播放在上升时进入光柱或进入大教堂时播放的动画。

???- example "Example Code"

	Plays the animation.

	```lua
	Isaac.GetPlayer():AnimateLightTravel()
	```

___
### Animate·Pickup () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AnimatePickup ( [Sprite](Sprite.md) sprite, boolean HideShadow = false, string AnimName = "Pickup" ) {: .copyable aria-label='Functions' }

播放拾取动画，使用任何提供的Sprite对象

HideShadow通常在渲染具有自定义阴影层的精灵时设置为true

___
### Animate·Pill () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AnimatePill ( [PillColor](enums/PillColor.md) Pill, string AnimName = "Pickup" ) {: .copyable aria-label='Functions' }

___
### Animate·Pitfall·In () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimatePitfallIn ( ) {: .copyable aria-label='Functions' }

造成1/2心的伤害并播放掉入陷阱的动画。

___
### Animate·Pitfall·Out () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimatePitfallOut ( ) {: .copyable aria-label='Functions' }

跳出陷阱的动画。

___
### Animate·Sad () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimateSad ( ) {: .copyable aria-label='Functions' }

播放悲伤动画，当服用负面药丸时播放。

???- example "Example Code"

    Plays the sad animation.

	```lua
	Isaac.GetPlayer():AnimateSad()
	```
___
### Animate·Teleport () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimateTeleport ( boolean Up ) {: .copyable aria-label='Functions' }

当传送到另一个房间时播放的动画。

___
### Animate·Trapdoor () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimateTrapdoor ( ) {: .copyable aria-label='Functions' }

播放跳下陷阱门的动画。

???- example "Example Code"

	Plays the animation of jumping down a trapdoor.

	```lua
	Isaac.GetPlayer():AnimateTrapdoor()
	```

___
### Animate·Trinket () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AnimateTrinket ( [TrinketType](enums/TrinketType.md) Trinket, string AnimName = "Pickup", string SpriteAnimName = "PlayerPickupSparkle" ) {: .copyable aria-label='Functions' }

___
### Are·Controls·Enabled () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean AreControlsEnabled ( ) {: .copyable aria-label='Functions' }

___
### Are·Opposing·Shoot·Directions·Pressed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean AreOpposingShootDirectionsPressed ( ) {: .copyable aria-label='Functions' }

返回最近的移动输入中非零的摇杆方向，但在玩家停止后变为零。
___
### Can·Add·Collectible () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean CanAddCollectible ( [CollectibleType](enums/CollectibleType.md) Type = CollectibleType.COLLECTIBLE_NULL ) {: .copyable aria-label='Functions' }

___
### Can·Pick·Black·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanPickBlackHearts ( ) {: .copyable aria-label='Functions' }

返回 true 如果玩家有容纳更多黑心的空间
___
### Can·Pick·Bone·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanPickBoneHearts ( ) {: .copyable aria-label='Functions' }

返回 true 如果玩家有容纳更多骨心的空间
___
### Can·Pick·Golden·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanPickGoldenHearts ( ) {: .copyable aria-label='Functions' }

返回 true 如果玩家有容纳更多金心的空间
___
### Can·Pick·Red·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanPickRedHearts ( ) {: .copyable aria-label='Functions' }

___
### Can·Pick·Rotten·Hearts () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean CanPickRottenHearts ( ) {: .copyable aria-label='Functions' }

返回 true 如果玩家有容纳更多腐心的空间
___
### Can·Pick·Soul·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanPickSoulHearts ( ) {: .copyable aria-label='Functions' }

返回 true 如果玩家有容纳更多魂心的空间
___
### Can·Pickup·Item () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanPickupItem ( ) {: .copyable aria-label='Functions' }

返回 true 如果玩家现在可以拾取物品
___
### Can·Shoot () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanShoot ( ) {: .copyable aria-label='Functions' }

___
### Can·Turn·Head () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanTurnHead ( ) {: .copyable aria-label='Functions' }

返回 true 如果头部应该对按键做出反应，否则返回 false
___
### Change·Player·Type () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void ChangePlayerType ( [PlayerType](enums/PlayerType.md) PlayerType ) {: .copyable aria-label='Functions' }

被用于改变一个玩家的类型。例如将该隐变成抹大拉。

在 MC_POST_PLAYER_INIT 中更改玩家类型将导致玩家获得该角色的默认物品。例如，抹大拉将获得她的美味的心，而无需您显式添加它。这里的例外包括可解锁物品（例如，以撒的 D6）和默认数量的心脏/钥匙/炸弹/硬币。您可以在初始化后更改玩家类型，但通常需要负责添加与该角色相关的任何物品。

将玩家类型更改为雅各布也会生成以扫。
___
### Check·Familiar () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void CheckFamiliar ( [FamiliarVariant](enums/FamiliarVariant.md) FamiliarVariant, int TargetCount, [RNG](RNG.md) rng, [ItemConfigItem](ItemConfig_Item.md) SourceItemConfigItem = nil, int FamiliarSubType = -1 ) {: .copyable aria-label='Functions' }

访问这个方法以生成与自定义可收集物品相关的适当数量的随从。

- 如果指定的目标数量少于当前的随从数量，它将生成更多，直到达到目标数量。

- 如果指定的目标数量大于当前的随从数量，它将去除随从，直到达到目标数量。

这意味着它应该在 EvaluateCache 回调中调用（当缓存标志等于 `CacheFlag.CACHE_FAMILIARS` 时）。

在大多数情况下，[:material-language-typescript:IsaacScript](https://isaacscript.github.io/) 用户应该使用 [`checkFamiliarFromCollectibles`](https://isaacscript.github.io/isaacscript-common/modules/functions_familiars.html#checkFamiliarFromCollectibles) 辅助函数，而不是直接使用此方法，因为它会自动计算适当的目标数量。

**FamiliarVariant**: 大多数情况下, 使用随从变体作为自定义随从的基础。

**TargetCount**: 期望该实体玩家应该拥有的此随从变体的数量。此参数可以简单地是当前实体玩家拥有的某个物品的数量。但是，如果您希望您的随从与怪物手册和朋友盒子协同作用，则此参数应为 `EntityPlayer:GetCollectibleNum(collectibleType) + EntityPlayer:GetEffects():GetCollectibleEffectNum(collectibleType)`。

**rng**: 可以是生成随从的可收集物品的 `EntityPlayer.GetCollectibleRNG` 的 RNG 对象。

**SourceItemConfigItem**: 生成此随从的 `ItemConfigItem`。默认情况下为 nil，但应始终指定，以便祭品祭坛正常工作。（它告知游戏如果随从被标记为“cansacrifice”实体标签，则应删除哪个可收集物品。）可以通过以下方式获得：`Isaac.GetItemConfig():GetCollectible(collectibleType)`

**FamiliarSubType**: 要检查的随从子类型。-1 匹配任何子类型。

???- example "Example Code"

    This code spawns 3 "Sister Maggy" familiars.

    ```lua
    local player = Isaac.GetPlayer()
    local sourceCollectibleID = CollectibleType.COLLECTIBLE_SAD_ONION
    local collectibleRNG = player:GetCollectibleRNG(sourceCollectibleID)
    local itemConfig = Isaac.GetItemConfig():GetCollectible(sourceCollectibleID)

    player:CheckFamiliar(FamiliarVariant.SISTER_MAGGY, 3, collectibleRNG, itemConfig)
    ```

___
### Clear·Costumes () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ClearCostumes ( ) {: .copyable aria-label='Functions' }

移除所有服装。
___
### Clear·Dead·Eye·Charge () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ClearDeadEyeCharge ( ) {: .copyable aria-label='Functions' }

___
### Clear·Temporary·Effects () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ClearTemporaryEffects ( ) {: .copyable aria-label='Functions' }

将在玩家退出房间时调用。

___
### Discharge·Active·Item () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void DischargeActiveItem ( [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY ) {: .copyable aria-label='Functions' }

设置您的主动物品的充能为 0，而不触发主动物品效果。

___
### Donate·Luck () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void DonateLuck ( int Luck ) {: .copyable aria-label='Functions' }

不像Luck属性应该在MC_EVALUATE_CACHE中设置，这个方法可以在任何地方使用，并会自动记住添加的任何额外运气。

___
### Do·Zit·Effect () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void DoZitEffect ( [Vector](Vector.md) Direction ) {: .copyable aria-label='Functions' }

发射一个青春痘，效果与“青春痘”物品发射的效果相同。

___
### Drop·Pocket·Item () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void DropPocketItem ( int PocketNum, [Vector](Vector.md) Pos ) {: .copyable aria-label='Functions' }

扔下一个持有的口袋物品（卡片、药丸、符文……）从给定的物品槽在给定的位置。可能的口袋编号是 [0, 1, 2, 3]。扔下口袋主动物品或骰子袋骰子是无效的。

___
### Drop·Trinket () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void DropTrinket ( [Vector](Vector.md) DropPos, boolean ReplaceTick ) {: .copyable aria-label='Functions' }

___
### Evaluate·Items () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void EvaluateItems ( ) {: .copyable aria-label='Functions' }

触发一个缓存重新评估，将会触发 MC_EVALUATE_CACHE 回调。

在使用此函数之前，您需要先设置适当的缓存标志。请参阅下面的示例。

???- example "Example Code"

    This code re-evaluates all of the stats for the player.

    ```lua
    local player = Isaac.GetPlayer()
    player:AddCacheFlags(CacheFlag.CACHE_ALL)
    player:EvaluateItems()
    ```

___
### Fire·Bomb () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityBomb](EntityBomb.md) FireBomb ( [Vector](Vector.md) Position, [Vector](Vector.md) Velocity, Entity Source = nil ) {: .copyable aria-label='Functions' }

___
### Fire·Brimstone () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityLaser](EntityLaser.md) FireBrimstone ( [Vector](Vector.md) Direction, Entity Source = nil, float DamageMultiplier = 1 ) {: .copyable aria-label='Functions' }

___
### Fire·Delayed·Brimstone () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityLaser](EntityLaser.md) FireDelayedBrimstone ( float Angle, [Entity](Entity.md) Parent ) {: .copyable aria-label='Functions' }

___
### Fire·Knife () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityKnife](EntityKnife.md) FireKnife ( [Entity](Entity.md) Parent, float RotationOffset = 0, boolean CantOverwrite = false, int SubType = 0, int Variant = 0 ) {: .copyable aria-label='Functions' }

???- note "Knife Variants"

    ```lua
    0: Mom's Knife
    1: Bone Club
    2: Bone Scythe
    3: Berserk Club
    4: Bag of Crafting
    5: Sumptorium
    9: Notched Axe
    10: Spirit Sword
    11: Tech Sword
    ```

___
### Fire·Tear () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityTear](EntityTear.md) FireTear ( [Vector](Vector.md) Position, [Vector](Vector.md) Velocity, boolean CanBeEye = true, boolean NoTractorBeam = false, boolean CanTriggerStreakEnd = true, Entity Source = nil, float DamageMultiplier = 1 ) {: .copyable aria-label='Functions' }

- `CanBeEye`: 如果玩家拥有邪恶之眼物品，传递 true 允许泪水有机会成为眼泪。
- `NoTractorBeam`: 如果玩家拥有牵引光束物品，传递 true 意味着泪水将免受光束影响。
- `CanTriggerStreakEnd`: 如果玩家拥有死亡之眼物品，传递 false 意味着泪水将免于结束连击。

___
### Fire·Tech·Laser () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityLaser](EntityLaser.md) FireTechLaser ( [Vector](Vector.md) Position, [LaserOffset](enums/LaserOffset.md) OffsetID, [Vector](Vector.md) Direction, boolean LeftEye, boolean OneHit = false, Entity Source = nil, float DamageMultiplier = 1 ) {: .copyable aria-label='Functions' }

???+ bug "Bugs"

    `DamageMultiplier` 变量不影响当提供 [LASER_TECH2_OFFSET](enums/LaserOffset.md) 作为偏移量时。

___
### Fire·Tech·XLaser () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityLaser](EntityLaser.md) FireTechXLaser ( [Vector](Vector.md) Position, [Vector](Vector.md) Direction, float Radius, Entity Source = nil, float DamageMultiplier = 1 ) {: .copyable aria-label='Functions' }

___
### Flush·Queue·Item () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean FlushQueueItem ( ) {: .copyable aria-label='Functions' }

在动画完成后，或在特殊情况下调用以防止错误
___
### Full·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean FullCharge ( [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY, int Force = false ) {: .copyable aria-label='Functions' }

完全充能当前的主动物品。如果物品被完全充能，返回 true；否则返回 false。如果玩家拥有电池，它将首先尝试填充第一个充能槽，然后是电池槽。

**Force**: 如果设置为 true，物品将始终充能，即使它们通常无法通过电池充能

???- info "ActiveSlot"

    将 ActiveSlot 参数设置为 `-1` 将充能所有槽中的物品。

___
### Get·Active·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetActiveCharge ( [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY ) {: .copyable aria-label='Functions' }

获取当前主动物品的充能值。
___
### Get·Active·Item () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [CollectibleType](enums/CollectibleType.md) GetActiveItem ( [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY ) {: .copyable aria-label='Functions' data-altreturn='0' }

返回当前持有的主动物品。如果没有物品被持有，则返回 `0`。

___
### Get·Active·Sub·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetActiveSubCharge ( [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY ) {: .copyable aria-label='Functions' }

获取当前主动物品的副充能值（即第二充能槽）。

???+ bug "Bug"

    这个函数似乎总是返回 0。使用 EntityPlayer:GetActiveCharge() 来获取任何类型的充能值。使用 EntityPlayer:GetBatteryCharge() 来获取第二个充能槽的充能值。

___
### Get·Active·Weapon·Entity () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) GetActiveWeaponEntity ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }

___
### Get·Aim·Direction () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) GetAimDirection ( ) {: .copyable aria-label='Functions' }

___
### Get·Baby·Skin () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [BabySubType](enums/BabySubType.md) GetBabySkin ( ) {: .copyable aria-label='Functions' }

___
### Get·Battery·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetBatteryCharge ( [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY ) {: .copyable aria-label='Functions' }

获取当前主动物品的第二充能槽的充能进度。该槽仅在你拥有可收集物品“电池”时处于激活状态。
___
### Get·Black·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetBlackHearts ( ) {: .copyable aria-label='Functions' }

这个函数并不返回黑心的数量；而是返回一个位掩码，用于表示哪些灵魂心是黑心。

???- example "Example"

    设想我们有以下血量的设置，其中 S 是灵魂心，B 是黑心：

    ```
    B S S B B S S B B
    ```

    Calling the function will return:

    ```lua
    Isaac.GetPlayer():GetBlackHearts() -- returns 409, which is 0001 1001 1001 in binary. Therefore, the read order is right to left.
    ```

    Quick code example to parse soul hearts vs black hearts:

    ```lua
    -- if you setup your hearts as described above then you'll get the following values
    -- GetSoulHearts = 18
    -- GetBlackHearts = 409
    local tbl = {}
    local player = Isaac.GetPlayer()
    -- loop over all the soul hearts
    -- divide by 2 because we need to go from half to whole hearts
    -- math.ceil to make sure we account for a possible half heart at the end
    for i = 0, math.ceil(player:GetSoulHearts() / 2) - 1 do
      -- you can also use BitSet128 here if you want: BitSet128(player:GetBlackHearts(),0):Get(i)
      table.insert(tbl, (player:GetBlackHearts() & (1 << i)) > 0 and 'B' or 'S')
    end
    if player:GetSoulHearts() % 2 ~= 0 then
      tbl[#tbl] = string.lower(tbl[#tbl]) -- lowercase to indicate half heart at end
    end
    print(table.concat(tbl, ' ')) -- prints: B S S B B S S B B
    ```

___
### Get·Blood·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetBloodCharge ( ) {: .copyable aria-label='Functions' }

返回玩家的血量充能值。

___
### Get·Body·Color () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [SkinColor](enums/SkinColor.md) GetBodyColor ( ) {: .copyable aria-label='Functions' }

___
### Get·Bomb·Flags () {: aria-label='Functions' }
[ ](#){: .abp .tooltip .badge }
#### int GetBombFlags ( ) {: .copyable aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetBombFlags ( boolean IsFetus = false ) {: .copyable aria-label='Functions' }

**IsFetus**: 如果设置为true，某些炸弹道具会随机设置flags。
___
### Get·Bomb·Variant () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [BombVariant](enums/BombVariant.md) GetBombVariant ( [TearFlags](enums/TearFlags.md) TearFlags, boolean ForceSmallBomb ) {: .copyable aria-label='Functions' }

通过传递泪弹标签为炸弹视觉效果添加额外效果，例如燃烧 -> 炙热炸弹，即使玩家没有道具炙热炸弹。 ForceSmallBomb 将覆盖 TEAR_PERSISTENT 的大炸弹变体。

___
### Get·Bone·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetBoneHearts ( ) {: .copyable aria-label='Functions' }

返回玩家的骨心数量。这个值并不像 `EntityPlayer.GetMaxHearts` 方法那样翻倍，所以如果例如玩家有 3 个骨心，这个函数将返回 3。

另请参阅 `EntityPlayer.GetEffectiveMaxHearts` 方法，该方法会考虑骨心。

___
### Get·Broken·Hearts () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetBrokenHearts ( ) {: .copyable aria-label='Functions' }

返回玩家的碎心数量。这个值并不像 `EntityPlayer.GetMaxHearts` 方法那样翻倍，所以如果例如玩家有 3 个碎心，这个函数将返回 3。

___
### Get·Card () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Card](enums/Card.md) GetCard ( int SlotId ) {: .copyable aria-label='Functions' data-altreturn='0' }

获取玩家在给定物品槽中持有的卡牌的 ID（0 = 主槽，1 = 副槽，2 或 3）。当槽中没有卡牌时返回 `0`。
___
### Get·Card·RNG () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [RNG](RNG.md) GetCardRNG ( [Card](enums/Card.md) ID ) {: .copyable aria-label='Functions' }

___
### Get·Collectible·Count () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetCollectibleCount ( ) {: .copyable aria-label='Functions' }

___
### Get·Collectible·Num () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetCollectibleNum ( [CollectibleType](enums/CollectibleType.md) Type, boolean OnlyCountTrueItems = false ) {: .copyable aria-label='Functions' }

**OnlyCountTrueItems**: 如果设置为 true，函数仅计算玩家实际拥有的可收集物品，并忽略 莉莉丝的淫魔、3美元 授予的物品等。
___
### Get·Collectible·RNG () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [RNG](RNG.md) GetCollectibleRNG ( [CollectibleType](enums/CollectibleType.md) ID ) {: .copyable aria-label='Functions' }

获取道具的 [RNG](RNG.md) 对象。

???- example "示例代码"

    这段代码将为你提供道具“伤心洋葱”的 RNG 对象。

    ```lua
    local player = Isaac.GetPlayer()
    local collectibleRNG = player:GetCollectibleRNG(CollectibleType.COLLECTIBLE_SAD_ONION)
    ```

___
### Get·Costume·Null·Pos () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetCostumeNullPos ( string NullFrameName, boolean HeadScale, [Vector](Vector.md) Direction ) {: .copyable aria-label='Functions' }

___
### Get·Damage·Cooldown () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetDamageCooldown ( ) {: .copyable aria-label='Functions' }

当玩家受到伤害时，他们会闪烁不同的颜色并获得无敌帧。此方法返回无敌帧的数量。通常，当玩家受到半颗心的伤害时，将获得 60 帧无敌时间；而受到一颗心的伤害时，将获得 120 帧无敌时间。此外，盲目的怒火饰品可以影响无敌帧的授予方式。

请注意，此函数返回的帧是渲染帧，而不是游戏帧。

___
### Get·Effective·Blood·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetEffectiveBloodCharge ( ) {: .copyable aria-label='Functions' }

返回玩家的血量充能。除堕化伯大妮外将返回 `0`。

___
### Get·Effective·Max·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetEffectiveMaxHearts ( ) {: .copyable aria-label='Functions' }

返回玩家在心容器和骨心中可以容纳的红心数量。1 个单位是半颗红心。

**Example：** 你有 3 个红心容器和 1 个骨心。6（红）+ 2（骨）= 8

___
### Get·Effective·Soul·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetEffectiveSoulCharge ( ) {: .copyable aria-label='Functions' }

返回玩家的灵魂充能。除伯大妮外将返回 `0`。

___
### Get·Effects () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [TemporaryEffects](TemporaryEffects.md) GetEffects ( ) {: .copyable aria-label='Functions' }

___
### Get·Eternal·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetEternalHearts ( ) {: .copyable aria-label='Functions' }

返回玩家的永恒之心数量。

___
### Get·Extra·Lives () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetExtraLives ( ) {: .copyable aria-label='Functions' }

返回玩家当前拥有的额外生命数量。

___
### Get·Fire·Direction () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Direction](enums/Direction.md) GetFireDirection ( ) {: .copyable aria-label='Functions' }

___
### Get·Flying·Offset () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetFlyingOffset ( ) {: .copyable aria-label='Functions' }

___
### Get·Golden·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetGoldenHearts ( ) {: .copyable aria-label='Functions' }

返回玩家的金心数量。

___
### Get·Greed·Donation·Break·Chance () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### float GetGreedDonationBreakChance ( ) {: .copyable aria-label='Functions' }

___
### Get·Head·Color () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [SkinColor](enums/SkinColor.md) GetHeadColor ( ) {: .copyable aria-label='Functions' }

___
### Get·Head·Direction () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Direction](enums/Direction.md) GetHeadDirection ( ) {: .copyable aria-label='Functions' }

___
### Get·Heart·Limit () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetHeartLimit ( ) {: .copyable aria-label='Functions' }

___
### Get·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetHearts ( ) {: .copyable aria-label='Functions' }

返回玩家在心容器和骨心中的红心数量。1 个单位是半颗红心。

___
### Get·Item·State () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [CollectibleType](enums/CollectibleType.md) GetItemState ( ) {: .copyable aria-label='Functions' }

___
### Get·Jar·Flies () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetJarFlies ( ) {: .copyable aria-label='Functions' }

___
### Get·Jar·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetJarHearts ( ) {: .copyable aria-label='Functions' }

___
### Get·Laser·Offset () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetLaserOffset ( [LaserOffset](enums/LaserOffset.md) ID, [Vector](Vector.md) Direction ) {: .copyable aria-label='Functions' }

___
### Get·Last·Action·Triggers () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetLastActionTriggers ( ) {: .copyable aria-label='Functions' }

___
### Get·Last·Damage·Flags () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetLastDamageFlags ( ) {: .copyable aria-label='Functions' }

___
### Get·Last·Damage·Source () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [EntityRef](EntityRef.md) GetLastDamageSource ( ) {: .copyable aria-label='Functions' }

___
### Get·Last·Direction () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) GetLastDirection ( ) {: .copyable aria-label='Functions' }

___
### Get·Main·Twin () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityPlayer](EntityPlayer.md) GetMainTwin ( ) {: .copyable aria-label='Functions' }

返回成对角色的主玩家或具有多种形态的角色的主形态。

- 当在雅各布或以扫身上调用时，返回雅各布。
- 当在堕化的遗骸或堕化的遗骸之魂身上调用时，返回堕化的遗骸。
- 当在堕化拉撒路或死亡的堕化拉撒路身上调用时，返回他们自己。如果玩家拥有长子权，则返回堕化的拉撒路。
- 当在任何其他角色上调用时，返回该角色。

___
### Get·Max·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetMaxHearts ( ) {: .copyable aria-label='Functions' }

返回玩家的心之容器数量。1 个单位是半颗心之容器。

___
### Get·Max·Pocket·Items () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetMaxPocketItems ( ) {: .copyable aria-label='Functions' }

获取玩家可以携带的道具数量。（默认 1，拥有多指畸形或类似效果时为 2）

If you have a pocket active, it also increments the number by one.

___
### Get·Max·Poop·Mana () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetMaxPoopMana ( ) {: .copyable aria-label='Functions' }

返回玩家可以持有的最大粪便消耗品数量。

___
### Get·Max·Trinkets () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetMaxTrinkets ( ) {: .copyable aria-label='Functions' }

返回玩家可以携带的最大饰品数量。（默认 1，拥有妈妈的钱包或类似效果时为 2）

___
### Get·Modeling·Clay·Effect () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [CollectibleType](enums/CollectibleType.md) GetModelingClayEffect ( ) {: .copyable aria-label='Functions' }

___
### Get·Movement·Direction () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Direction](enums/Direction.md) GetMovementDirection ( ) {: .copyable aria-label='Functions' }

___
### Get·Movement·Input () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) GetMovementInput ( ) {: .copyable aria-label='Functions' }

___
### Get·Movement·Joystick () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetMovementJoystick ( ) {: .copyable aria-label='Functions' }

___
### Get·Movement·Vector () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetMovementVector ( ) {: .copyable aria-label='Functions' }

___
### Get·Multi·Shot·Params () {: aria-label='Functions' }
[ ](#){: .rep .tooltip .badge }
#### MultiShotParams GetMultiShotParams ( [WeaponType](enums/WeaponType.md) WeaponType = WeaponType.WEAPON_TEARS ) {: .copyable aria-label='Functions' }

???+ bug "Bug"

    自从它返回的 UserData 不能直接编辑，因此此函数的返回值只能与 [GetMultiShotPositionVelocity()](#getmultishotpositionvelocity) 函数结合使用。
___
### Get·Multi·Shot·Position·Velocity () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### [PosVel](PlayerTypes_PosVel.md) GetMultiShotPositionVelocity ( int LoopIndex, [WeaponType](enums/WeaponType.md) Weapon, [Vector](Vector.md) ShotDirection, float ShotSpeed, MultiShotParams params ) {: .copyable aria-label='Functions' }

调用此函数时，请在循环中使用，其中 LoopIndex 是 0 到当前 MultiShotParams 包含的泪水数量之间的数字。由于 MultiShotParams 目前无法通过 modding api 访问，因此您需要找到其他方法来获取该数量。

???+ bug "Removed Function"

    这个函数自忏悔版本 `v1.7.9b.J835` 以来不再存在！

___
### Get·Name () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### string GetName ( ) {: .copyable aria-label='Functions' }

返回玩家的名字(Isaac, Cain, Azazel,...)

___
### Get·NPCTarget () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) GetNPCTarget ( ) {: .copyable aria-label='Functions' }

同样，这个函数通常返回玩家。然而，在某些情况下，NPC 可以被重定向攻击另一个目标，在这种情况下，这个函数将返回替代目标（例如，在使用最好的朋友之后）。
___
### Get·Num·Blue·Flies () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetNumBlueFlies ( ) {: .copyable aria-label='Functions' }

___
### Get·Num·Blue·Spiders () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetNumBlueSpiders ( ) {: .copyable aria-label='Functions' }

___
### Get·Num·Bombs () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetNumBombs ( ) {: .copyable aria-label='Functions' }

___
### Get·Num·Coins () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetNumCoins ( ) {: .copyable aria-label='Functions' }

___
### Get·Num·Giga·Bombs () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetNumGigaBombs ( ) {: .copyable aria-label='Functions' }

___
### Get·Num·Keys () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetNumKeys ( ) {: .copyable aria-label='Functions' }

___
### Get·Other·Twin () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityPlayer](EntityPlayer.md) GetOtherTwin ( ) {: .copyable aria-label='Functions' }

返回双人角色的另一个角色或具有多种形式的角色的另一种形态。

- 当在雅各布身上调用时，返回以扫
- 当在以扫身上调用时，返回雅各布。
- 当在堕化遗骸身上调用时，返回堕化遗骸之魂。
- 当在堕化遗骸之魂上调用时，返回堕化遗骸。
- 当在堕化拉撒路身上调用时，仅当玩家拥有长子权时，它才会返回死亡的堕化拉撒路。否则，它返回 nil。
- 当在任何其他角色上调用时，返回 nil。
___
### Get·Pill () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [PillColor](enums/PillColor.md) GetPill ( int SlotId ) {: .copyable aria-label='Functions' data-altreturn='0' }

获得玩家在给定物品槽中持有的药丸的 ID (0 = 主槽, 1 = 副槽, 2 或 3) 当在给定槽中没有药丸时返回 `0`。
___
### Get·Pill·RNG () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [RNG](RNG.md) GetPillRNG ( [PillEffect](enums/PillEffect.md) ID ) {: .copyable aria-label='Functions' }

___
### Get·Player·Type () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [PlayerType](enums/PlayerType.md) GetPlayerType ( ) {: .copyable aria-label='Functions' }

___
### Get·Pocket·Item () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const PlayerPocketItem GetPocketItem ( int SlotId ) {: .copyable aria-label='Functions' }

获得玩家在给定物品槽中持有的口袋物品 (卡牌、药丸、符文) 的用户数据。

???+ bug "Bugs"

    此函数返回用户数据，无法处理。因此它是损坏的，不应使用！
___
### Get·Poop·Mana () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetPoopMana ( ) {: .copyable aria-label='Functions' }

返回玩家当前持有的粪便数量

___
### Get·Poop·Spell () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [PoopSpellType](enums/PoopSpellType.md) GetPoopSpell ( int Position ) {: .copyable aria-label='Functions' }

返回玩家粪便队列中给定位置的粪便类型

___
### Get·Recent·Movement·Vector () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) GetRecentMovementVector ( ) {: .copyable aria-label='Functions' }

返回驱动玩家移动的摇杆方向，同时考虑到某些修饰符，例如禁用的控制和种子效果。

___
### Get·Rotten·Hearts () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetRottenHearts ( ) {: .copyable aria-label='Functions' }

___
### Get·Shooting·Input () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetShootingInput ( ) {: .copyable aria-label='Functions' }

返回一个向量，表示该玩家正在按下的射击输入方向。

???- info "Shooting Angle diagram"

    ![GetShootingInput diagram](images/infographics/GetShootingInput.png){: width='250' }

___
### Get·Shooting·Joystick () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetShootingJoystick ( ) {: .copyable aria-label='Functions' }

返回一个向量，表示该玩家正在按下的射击输入方向。

可以查看 [GetShootingInput](#getshootinginput) 方法的图像。

___
### Get·Smooth·Body·Rotation () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### float GetSmoothBodyRotation ( ) {: .copyable aria-label='Functions' }

___
### Get·Soul·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### int GetSoulCharge ( ) {: .copyable aria-label='Functions' }

返回玩家当前的魂心充能的量。

___
### Get·Soul·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetSoulHearts ( ) {: .copyable aria-label='Functions' }

返回玩家当前的魂心数量。1 个单位是半颗心。

???- note "Notes"

    黑心计入此总数，因为游戏将其视为魂心。

___
### Get·Sub·Player () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityPlayer](EntityPlayer.md) GetSubPlayer ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }

返回堕化遗骸的另一种形式。

___
### Get·Tear·Hit·Params () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [TearParams](TearParams.md) GetTearHitParams ( [WeaponType](enums/WeaponType.md) WeaponType, float DamageScale = 1, int TearDisplacement = 1, Entity Source = nil ) {: .copyable aria-label='Functions' }

被用于命中时计算的眼泪参数 (例如：严厉的爱，普通感冒)，DamageScale 用于基于伤害的缩放计算

___
### Get·Tear·Movement·Inheritance () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetTearMovementInheritance ( [Vector](Vector.md) ShotDirection ) {: .copyable aria-label='Functions' }

___
### Get·Tear·Poison·Damage () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### float GetTearPoisonDamage ( ) {: .copyable aria-label='Functions' }

___
### Get·Tear·Range·Modifier () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetTearRangeModifier ( ) {: .copyable aria-label='Functions' }

对于实验性疗法，返回 `-1`、`0` 或 `1`，具体取决于范围的掷骰结果。

___
### Get·Total·Damage·Taken () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetTotalDamageTaken ( ) {: .copyable aria-label='Functions' }

___
### Get·Tractor·Beam () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) GetTractorBeam ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }

___
### Get·Trinket () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [TrinketType](enums/TrinketType.md) GetTrinket ( int TrinketIndex ) {: .copyable aria-label='Functions' data-altreturn='0' }

获取玩家在指定饰品槽（0 或 1）中持有的饰品 ID。当指定槽位没有饰品时，返回 `0`。
___
### Get·Trinket·Multiplier () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetTrinketMultiplier ( [TrinketType](enums/TrinketType.md) TrinketID ) {: .copyable aria-label='Functions' }
Gets the multiplier of a given Trinket effect. This is analog to the number of times the trinket effect is applied.

???- info "Multiplier Breakdown"
    * Per normal trinket of this type equipped / gulped : +1
    * Per golden trinket of this type equipped / gulped : +2
    * Mom's Box equipped : +1 (does not stack)
___
### Get·Trinket·RNG () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [RNG](RNG.md) GetTrinketRNG ( [TrinketType](enums/TrinketType.md) TrinketID ) {: .copyable aria-label='Functions' }

___
### Get·Velocity·Before·Update () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) GetVelocityBeforeUpdate ( ) {: .copyable aria-label='Functions' }

___
### Get·Zodiac·Effect () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [CollectibleType](enums/CollectibleType.md) GetZodiacEffect ( ) {: .copyable aria-label='Functions' }

___
### Has·Collectible () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean HasCollectible ( [CollectibleType](enums/CollectibleType.md) Type, boolean IgnoreModifiers = false ) {: .copyable aria-label='Functions' }
**IgnoreModifiers**: If set to true, only counts collectibles the player actually owns and ignores effects granted by items like Zodiac, 3 Dollar Bill and Lemegeton

___
### Has·Curse·Mist·Effect () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean HasCurseMistEffect ( ) {: .copyable aria-label='Functions' }

___
### Has·Full·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasFullHearts ( ) {: .copyable aria-label='Functions' }

___
### Has·Full·Hearts·And·Soul·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasFullHeartsAndSoulHearts ( ) {: .copyable aria-label='Functions' }

___
### Has·Golden·Bomb () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasGoldenBomb ( ) {: .copyable aria-label='Functions' }

___
### Has·Golden·Key () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasGoldenKey ( ) {: .copyable aria-label='Functions' }

___
### Has·Invincibility () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean HasInvincibility ( [DamageFlag](enums/DamageFlag.md) Flags = 0 ) {: .copyable aria-label='Functions' }
returns true when player is in an invincibility state
___
### Has·Player·Form () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasPlayerForm ( [PlayerForm](enums/PlayerForm.md) Form ) {: .copyable aria-label='Functions' }

___
### Has·Timed·Item () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasTimedItem ( ) {: .copyable aria-label='Functions' }
Returns true if you have a timed active item *(such as Brown Nugget)* in the first active slot

___
### Has·Trinket () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean HasTrinket ( [TrinketType](enums/TrinketType.md) Type, boolean IgnoreModifiers = false ) {: .copyable aria-label='Functions' }
**IgnoreModifiers**: If set to true, only counts trinkets the player actually holds and ignores effects granted by other items

___
### Has·Weapon·Type () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasWeaponType ( [WeaponType](enums/WeaponType.md) WeaponType ) {: .copyable aria-label='Functions' }

___
### Init·Baby·Skin () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void InitBabySkin ( ) {: .copyable aria-label='Functions' }

___
### Is·Black·Heart () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsBlackHeart ( int Heart ) {: .copyable aria-label='Functions' }
This can be used instead of GetBlackHearts to figure out which soul hearts are black hearts.

???- example "Example"
    Imagine we have the following setup of hearts, where S is a soul heart and B is a black heart:

    ```
    B S S B B S S B B
    ```

    Each soul heart is composed of two halves. Only the odd numbers seem to trigger this function. Even numbers always return false. The following assumes that the indexing starts at 1 rather than 0, but regardless, it's the odd numbers that work here. The indexing here only applies to your soul/black hearts. It doesn't matter if you have other red/bone/etc hearts.

    ```
    B(1,2) S(3,4) S(5,6) B(7,8) B(9,10) S(11,12) S(13,14) B(15,16) B(17,18)
    ```

    ```lua
    Isaac.GetPlayer():IsBlackHeart(1) -- returns true (black heart)
    Isaac.GetPlayer():IsBlackHeart(2) -- returns false (not useful)
    Isaac.GetPlayer():IsBlackHeart(3) -- returns false (soul heart)
    -- 1,7,9,15,17 all return true (black hearts)
    ```

    Quick code example to parse soul hearts vs black hearts:

    ```lua
    -- if you setup your hearts as described above then you'll get the following value
    -- GetSoulHearts = 18
    local tbl = {}
    local player = Isaac.GetPlayer()
    -- loop over all the soul heart odd indexes
    for i = 1, player:GetSoulHearts(), 2 do
      table.insert(tbl, player:IsBlackHeart(i) and 'B' or 'S')
    end
    if player:GetSoulHearts() % 2 ~= 0 then
      tbl[#tbl] = string.lower(tbl[#tbl]) -- lowercase to indicate half heart at end
    end
    print(table.concat(tbl, ' ')) -- prints: B S S B B S S B B
    ```

___
### Is·Bone·Heart () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsBoneHeart ( int heart ) {: .copyable aria-label='Functions' }
This can be used to figure out the ordering of bone hearts amongst soul/black hearts.

???- example "Example"
    Imagine we have the following setup of hearts:

    ```
    BONE SOUL BONE BLACK BONE
    ```

    The indexing here is for whole hearts, and the index starts at 0. The indexing takes into account bone/soul/black hearts. It doesn't matter if you have other heart types (e.g. red hearts).

    ```lua
    Isaac.GetPlayer():IsBoneHeart(0) -- returns true (bone heart)
    Isaac.GetPlayer():IsBoneHeart(1) -- returns false (soul heart)
    Isaac.GetPlayer():IsBoneHeart(3) -- returns false (black heart)
    -- 0,2,4 all return true (bone hearts)
    ```

    Quick code example to parse soul hearts vs black hearts vs bone hearts:

    ```lua
    -- if you setup your hearts as described above then you'll get the following values
    -- GetSoulHearts = 4
    -- GetBoneHearts = 3
    local tbl = {}
    local player = Isaac.GetPlayer()
    -- first, figure out the soul/black heart order
    for i = 1, player:GetSoulHearts(), 2 do
      table.insert(tbl, player:IsBlackHeart(i) and 'BLACK' or 'SOUL')
    end
    if player:GetSoulHearts() % 2 ~= 0 then
      tbl[#tbl] = string.lower(tbl[#tbl]) -- lowercase to indicate half heart at end
    end
    -- second, figure out where bone hearts fit into the soul/black/bone heart order
    -- divide soul hearts by 2 to get whole hearts, bone hearts are already in whole heart increments
    for i = 0, math.ceil(player:GetSoulHearts() / 2) + player:GetBoneHearts() - 1 do
      if player:IsBoneHeart(i) then
        table.insert(tbl, i + 1, 'BONE')
      end
    end
    print(table.concat(tbl, ' ')) -- prints: BONE SOUL BONE BLACK BONE
    ```

___
### Is·Coop·Ghost () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean IsCoopGhost ( ) {: .copyable aria-label='Functions' }
In a multiplayer game, if a player dies, they will return as a tiny ghost. This method returns true if the player is a co-op ghost.

___
### Is·Extra·Animation·Finished () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsExtraAnimationFinished ( ) {: .copyable aria-label='Functions' }

___
### Is·Full·Sprite·Rendering () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsFullSpriteRendering ( ) {: .copyable aria-label='Functions' }

___
### Is·Held·Item·Visible () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsHeldItemVisible ( ) {: .copyable aria-label='Functions' }

___
### Is·Holding·Item () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsHoldingItem ( ) {: .copyable aria-label='Functions' }
Is Player holding up an item (card/collectible/etc)
___
### Is·Item·Queue·Empty () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsItemQueueEmpty ( ) {: .copyable aria-label='Functions' }

___
### Is·P2Appearing () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsP2Appearing ( ) {: .copyable aria-label='Functions' }

___
### Is·Pos·In·Spot·Light () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsPosInSpotLight ( [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' }
Returns true if the `position` is in the AOE of the **Night Light** item.

___
### Is·Sub·Player () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsSubPlayer ( ) {: .copyable aria-label='Functions' }
Returns true if the player object was returned from the `EntityPlayer.GetSubPlayer` method. (This method is not related to multiplayer.)

Additionally, this also returns true for the player object representing Dead Tainted Lazarus that fires at the beginning of the run in the PostPlayerInit callback. (The PostPlayerInit callback fires first for Dead Tainted Lazarus before firing for the normal Tainted Lazarus.)

___
### Needs·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean NeedsCharge ( [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY ) {: .copyable aria-label='Functions' }

This will always return false for active items that have `chargetype="special"` set in the `items.xml` file, even if they are not fully charged.

___
### Play·Extra·Animation () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void PlayExtraAnimation ( string Animation ) {: .copyable aria-label='Functions' }

___
### Queue·Extra·Animation () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void QueueExtraAnimation ( string Animation ) {: .copyable aria-label='Functions' }

___
### Queue·Item () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void QueueItem ( [ItemConfigItem](ItemConfig_Item.md) Item, int Charge = 0, boolean Touched = false, boolean Golden = false, int VarData = 0 ) {: .copyable aria-label='Functions' }
When the player touches a collectible or trinket, they are not granted it immediately. Instead, the item is queued for the duration of the animation where the player holds the item above their head. When the animation is finished, the item in the queue will be granted. This method adds a new item to the item queue. If the player is not currently playing an animation, then the queued item will simply be awarded instantly.

Also see `FlushQueueItem()`, `IsItemQueueEmpty()`, and `QueuedItem`.
___
### Remove·Black·Heart () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveBlackHeart ( int BlackHeart ) {: .copyable aria-label='Functions' }

___
### Remove·Blue·Fly () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveBlueFly ( ) {: .copyable aria-label='Functions' }

___
### Remove·Blue·Spider () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveBlueSpider ( ) {: .copyable aria-label='Functions' }

___
### Remove·Collectible () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void RemoveCollectible ( [CollectibleType](enums/CollectibleType.md) Type, boolean IgnoreModifiers = false, [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY, boolean RemoveFromPlayerForm = true ) {: .copyable aria-label='Functions' }
**IgnoreModifiers**: Ignores collectible effects granted by other items (i.e. Void)

**Slot**: Sets the active slot this collectible should be removed from

**RemoveFromPlayerForm**: If successfully removed and part of a transformation, decrease that transformation's counter by 1
___
### Remove·Costume () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveCostume ( [ItemConfigItem](ItemConfig_Item.md) Item ) {: .copyable aria-label='Functions' }
Removes a given costume based on its item config entry.

???- example "Example code"
    This code removes the costume of the Spoon Bender collectible.
    ```lua
    local player = Isaac.GetPlayer()
    local itemConfig = Isaac.GetItemConfig()
    local itemConfigItem = itemConfig:GetCollectible(CollectibleType.COLLECTIBLE_SPOON_BENDER)
    player:RemoveCostume(itemConfigItem)
    ```

___
### Remove·Curse·Mist·Effect () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void RemoveCurseMistEffect ( ) {: .copyable aria-label='Functions' }

___
### Remove·Golden·Bomb () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveGoldenBomb ( ) {: .copyable aria-label='Functions' }

___
### Remove·Golden·Key () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveGoldenKey ( ) {: .copyable aria-label='Functions' }

___
### Remove·Skin·Costume () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveSkinCostume ( ) {: .copyable aria-label='Functions' }
Removes player-specific costumes like Magdalene's hair or Cain's eyepatch.

___
### Render·Body () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RenderBody ( [Vector](Vector.md) position ) {: .copyable aria-label='Functions' }

___
### Render·Glow () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RenderGlow ( [Vector](Vector.md) position ) {: .copyable aria-label='Functions' }

___
### Render·Head () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RenderHead ( [Vector](Vector.md) position ) {: .copyable aria-label='Functions' }

___
### Render·Top () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RenderTop ( [Vector](Vector.md) position ) {: .copyable aria-label='Functions' }

___
### Replace·Costume·Sprite () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ReplaceCostumeSprite ( [ItemConfigItem](ItemConfig_Item.md) Item, string SpritePath, int SpriteId ) {: .copyable aria-label='Functions' }

___
### Reset·Damage·Cooldown () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ResetDamageCooldown ( ) {: .copyable aria-label='Functions' }

___
### Reset·Item·State () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ResetItemState ( ) {: .copyable aria-label='Functions' }
[Room](Room.md) transitions call this to prevent lock ups.
___
### Respawn·Familiars () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RespawnFamiliars ( ) {: .copyable aria-label='Functions' }
Respawns all familiars associated to the player.

___
### Revive () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Revive ( ) {: .copyable aria-label='Functions' }
Revives the player.

???+ bug "Bugs"
    Exiting the run at any point after this function is called will make it so that the run can't be continued.
___
### Set·Active·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void SetActiveCharge ( int Charge, [ActiveSlot](enums/ActiveSlot.md) ActiveSlot = ActiveSlot.SLOT_PRIMARY ) {: .copyable aria-label='Functions' }

___
### Set·Blood·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void SetBloodCharge ( int Amount ) {: .copyable aria-label='Functions' }

Sets the amount of Blood Charge the player has. Blood Charge does not do anything on characters besides Tainted Bethany.

___
### Set·Card () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetCard ( int SlotId, [Card](enums/Card.md) ID ) {: .copyable aria-label='Functions' }

Change the card/rune the player is holding in the given itemslot (0 or 1).
___
### Set·Full·Hearts () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetFullHearts ( ) {: .copyable aria-label='Functions' }

___
### Set·Min·Damage·Cooldown () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetMinDamageCooldown ( int DamageCooldown ) {: .copyable aria-label='Functions' }

___
### Set·Pill () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetPill ( int SlotId, [PillColor](enums/PillColor.md) Pill ) {: .copyable aria-label='Functions' }

Change the pill the player is holding in the given itemslot (0 or 1).

___
### Set·Pocket·Active·Item() {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void SetPocketActiveItem ( [CollectibleType](enums/CollectibleType.md) Type, [ActiveSlot](enums/ActiveSlot.md) Slot, boolean KeepInPools ) {: .copyable aria-label='Functions' }

Sets the player's pocket active item to the given active item.
Slot can be either SLOT_POCKET or SLOT_POCKET2.
Items added to SLOT_POCKET2 will always be removed upon being used.
If KeepInPools is set to true, the item will not be removed from the item pools.
Use this to let the player start with a custom active item in their pocket active slot right away.

???+ bug "Bugs"
    Calling this function inside PostPlayerInit callback causes a crash when continuing a saved run after closing and reopening the game, unless KeepInPools argument is set to true.
___
### Set·Shooting·Cooldown () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetShootingCooldown ( int Cooldown ) {: .copyable aria-label='Functions' }

___
### Set·Soul·Charge () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void SetSoulCharge ( int Amount ) {: .copyable aria-label='Functions' }

Sets the amount of Soul Charge the player has. Soul Charge does not do anything on characters besides Bethany.

___
### Set·Target·Trap·Door () {: aria-label='Functions' }
[ ](#){: .abp .tooltip .badge }
#### void SetTargetTrapDoor ( [GridEntity](GridEntity.md) TrapDoor ) {: .copyable aria-label='Functions' }

This function got removed with Repentance.

___
### Shoot·Red·Candle () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ShootRedCandle ( [Vector](Vector.md) Direction ) {: .copyable aria-label='Functions' }
for ghost pepper item + poop and farts
___
### Spawn·Maw·Of·Void () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityLaser](EntityLaser.md) SpawnMawOfVoid ( int Timeout ) {: .copyable aria-label='Functions' }

___
### Stop·Extra·Animation () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void StopExtraAnimation ( ) {: .copyable aria-label='Functions' }

___
### Swap·Active·Items () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SwapActiveItems ( ) {: .copyable aria-label='Functions' }
Swaps active items in the **Schoolbag** activeslot

___
### Throw·Blue·Spider () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) ThrowBlueSpider ( [Vector](Vector.md) Position, [Vector](Vector.md) Target ) {: .copyable aria-label='Functions' }

___
### Throw·Friendly·Dip () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [EntityFamiliar](EntityFamiliar.md) ThrowFriendlyDip ( int Subtype, [Vector](Vector.md) Position, [Vector](Vector.md) Target ) {: .copyable aria-label='Functions' }

???- note "Dip Subtypes"
    ```lua
    0: normal
    1: red
    2: corny
    3: golden
    4: rainbow
    5: black
    6: holy
    12: stone
    13: flaming
    14: poison
    20: brownie
    ```
___
### Throw·Held·Entity () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [Entity](Entity.md) ThrowHeldEntity ( [Vector](Vector.md) Velocity ) {: .copyable aria-label='Functions' }

___
### Trigger·Book·Of·Virtues () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void TriggerBookOfVirtues ( [CollectibleType](enums/CollectibleType.md) Type = CollectibleType.COLLECTIBLE_NULL, int Charge = 0 ) {: .copyable aria-label='Functions' }
Works only if the player has the **Book of Virtues** item, otherwise does nothing

___
### Try·Hold·Entity () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean TryHoldEntity ( [Entity](Entity.md) Entity ) {: .copyable aria-label='Functions' }

___
### Try·Hold·Trinket () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TryHoldTrinket ( [TrinketType](enums/TrinketType.md) Type ) {: .copyable aria-label='Functions' }
Returns true if an active item pickup cooldown is over. returns true if trinket can be added, else false
___
### Try·Remove·Collectible·Costume () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void TryRemoveCollectibleCostume ( [CollectibleType](enums/CollectibleType.md) Collectible, boolean KeepPersistent ) {: .copyable aria-label='Functions' }
Tries to remove a costume of the given collectible. `KeepPersistent` is used to define if persistent costumes should be removed. If its set to `false`, it will only remove temporary costumes.

???- example "Example code"
    This code removes the costume of the Spoon Bender collectible.
    ```lua
    local player = Isaac.GetPlayer()
    player:TryRemoveCollectibleCostume(CollectibleType.COLLECTIBLE_SPOON_BENDER, false)
    ```
___
### Try·Remove·Null·Costume () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void TryRemoveNullCostume ( [NullItemID](enums/NullItemID.md) NullId ) {: .copyable aria-label='Functions' }

___
### Try·Remove·Trinket () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TryRemoveTrinket ( [TrinketType](enums/TrinketType.md) Type ) {: .copyable aria-label='Functions' }

___
### Try·Remove·Trinket·Costume () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void TryRemoveTrinketCostume ( [TrinketType](enums/TrinketType.md) Trinket ) {: .copyable aria-label='Functions' }
Tries to remove a trinket costume
___
### Try·Use·Key () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TryUseKey ( ) {: .copyable aria-label='Functions' }

___
### Update·Can·Shoot () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void UpdateCanShoot ( ) {: .copyable aria-label='Functions' }

___
### Use·Active·Item () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void UseActiveItem ( [CollectibleType](enums/CollectibleType.md) Item, [UseFlags](enums/UseFlag.md) UseFlags = 0, [ActiveSlot](enums/ActiveSlot.md) Slot = -1, int CustomVarData = 0 ) {: .copyable aria-label='Functions' }

#### void UseActiveItem ( [CollectibleType](enums/CollectibleType.md) Item, boolean ShowAnim = false, boolean KeepActiveItem = false, boolean AllowNonMainPlayer = true, boolean ToAddCostume = false, [ActiveSlot](enums/ActiveSlot.md) Slot = -1, int CustomVarData = 0 ) {: .copyable .secondH4 aria-label='Functions' }
**Slot**: The active slot this item was used from (set to -1 if this item wasn't triggered by any active slot)

**CustomVarData**: `UseFlag.USE_CUSTOMVARDATA` needs to be provided in `UseFlags` otherwise this field is ignored

???- note "Notes"
	This method will increment the number of CollectibleEffects (see [Temporary Effects](TemporaryEffects.md)) of the passed item by 1 for the current room, and will trigger any associated MC_USE_ITEM callbacks. As of Repentance, this method can also be used on Passive and Familiar ItemTypes.
___
### Use·Card () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void UseCard ( [Card](enums/Card.md) ID, [UseFlags](enums/UseFlag.md) UseFlags = 0 ) {: .copyable aria-label='Functions' }

___
### Use·Pill () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void UsePill ( [PillEffect](enums/PillEffect.md) ID, [PillColor](enums/PillColor.md) PillColor, [UseFlags](enums/UseFlag.md) UseFlags = 0  ) {: .copyable aria-label='Functions' }

___
### Use·Poop·Spell () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void UsePoopSpell ( [PoopSpellType](enums/PoopSpellType.md) type ) {: .copyable aria-label='Functions' }
Triggers one of Tainted ???'s poop spells (see [PoopSpellType](enums/PoopSpellType.md) enum)

___
### Will·Player·Revive () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean WillPlayerRevive ( ) {: .copyable aria-label='Functions' }
This function will return true if the player has one or more extra lives or if a conditional revival item will work on the next death.

Right now, there are 3 items that grant conditional extra lives:

* Guppy's Collar - This function will successfully predict whether or not the next revive from Guppy's Collar will work or not. (50% chance)
* Broken Ankh - This function will successfully predict whether or not the next revive from Broken Ankh will work or not. (22.22% chance)
* Mysterious Paper - This function will only successfully predict the revive from Missing Poster every 4 frames, because it evaluates only one of its 4 possible item effects each frame.

___
## Variables
### Baby·Skin {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [BabySubType](enums/BabySubType.md) BabySkin  {: .copyable aria-label='Variables' }
P2 Skin section Used to hold the selected skin (in case of glitched baby it will pick a random one)

???+ bug "Bugs"
    This variable actually contains userdata and is not usable within API. Attempt to change it will results in a crash.

___
### Can·Fly {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanFly  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE. Can the player fly over rocks and pits?
___
### Controller·Index {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const int ControllerIndex  {: .copyable aria-label='Variables' }

___
### Controls·Cooldown {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int ControlsCooldown  {: .copyable aria-label='Variables' }
Specifies the number of frames the player's controls should be disabled. Decrements by 1 every frame, until it reaches 0. Used by the paralysis pill effect.

At 0 or less, does not block player control.
___
### Controls·Enabled {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean ControlsEnabled  {: .copyable aria-label='Variables' }

___
### Damage {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Damage  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE.  **This is equal to the Damage Stat.**  How much damage do the players tears or other main weapons do?
___
### Fire·Delay {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float FireDelay  {: .copyable aria-label='Variables' }
How long until the player can spawn their next tear?

???- note "Version Difference"
	In the Afterbirth+ version of the modding api, this variable is an integer

___
### Friend·Ball·Enemy {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const EntityDesc FriendBallEnemy  {: .copyable aria-label='Variables' }

???+ bug "Bugs"
    This function returns userdata that cant be edited or accessed.
___
### Head·Frame·Delay {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int HeadFrameDelay  {: .copyable aria-label='Variables' }
Specifies the number of frames the player's head should be playing the shooting animation. Decrements by 1 every frame, until it reaches -1.

At negative values, the player's head does not play the shooting animation.
___
### IBS·Charge {: aria-label='Variables' }
[ ](#){: .reporplus .tooltip .badge }
#### float IBSCharge  {: .copyable aria-label='Variables' }
Internally used by IBS, increases based on damage dealt, range is 0-1
___
### Item·Hold·Cooldown {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int ItemHoldCooldown  {: .copyable aria-label='Variables' }
Used for avoiding player get stucked between rocks when switching a flying item with other active item.
___
### Laser·Color {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Color](Color.md) LaserColor  {: .copyable aria-label='Variables' }

___
### Luck {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Luck  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE.  **This is equal to the Luck Stat.**  Better luck generally means better random events.
___
### Max·Fire·Delay {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float MaxFireDelay  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE.  **This is equal to the Tears Stat.**  How long between each tear can spawn?

???- note "Version Difference"
	In the Afterbirth+ version of the modding api, this variable is an integer

___
### Move·Speed {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float MoveSpeed  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE.  **This is equal to the Speed Stat.**  How fast can the player move?
___
### Queued·Item {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [QueueItemData](QueueItemData.md) QueuedItem  {: .copyable aria-label='Variables' }

- When Isaac picks up a collectible or a trinket, he holds it above his head for a while. At this point, the collectible/trinket is not actually put into his inventory yet.
- In other words, the item is queued for insertion until the animation completes, at which point the queue is processed and the item is inserted.
- `QueuedItem` holds a object of type `QueueItemData` that describes the item that a player is currently holding above their head.
- `QueuedItem` is never nil, even if the player is not currently holding up any item. (However, `player.QueuedItem.Item` will be nil if they are not currently holding up any item.)
- This only stores data for collectibles and trinkets. It does not store any data for pocket items (even though Isaac plays a similar "holding above head" animation for pocket items).
- Also see `FlushQueueItem()`, `IsItemQueueEmpty()`, and `QueueItem()`.
___
### Samson·Berserk·Charge {: aria-label='Variables' }
[ ](#){: .reporplus .tooltip .badge }
#### int SamsonBerserkCharge  {: .copyable aria-label='Variables' }
Internally used by Tainted Samson, increases based on damage dealt, range is 0-100000
___
### Secondary·Active·Item {: aria-label='Variables' }
[ ](#){: .abp .tooltip .badge }
#### [ActiveItemDesc](PlayerTypes_ActiveItemDesc.md) SecondaryActiveItem  {: .copyable aria-label='Variables' data-altreturn='nil' }

???+ bug "Bug"
    This function does not exist anymore in Repentance. As of right now, there is no other function to get the [ActiveItemDesc](PlayerTypes_ActiveItemDesc.md) of any active item the player holds. Until this is fixed, this info will stay here.
___
### Shot·Speed {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float ShotSpeed  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE.  **This is equal to the ShotSpeed Stat.**

Defines how fast the tear travel when spawned.

The default velocity of a tear shot is 10 times the players ShotSpeed.

___
### Tear·Color {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Color](Color.md) TearColor  {: .copyable aria-label='Variables' }

___
### Tear·Falling·Acceleration {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float TearFallingAcceleration  {: .copyable aria-label='Variables' }

___
### Tear·Falling·Speed {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float TearFallingSpeed  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE. How fast is the tear moving up or down when it spawns? Affects range.
___
### Tear·Flags {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [TearFlags](enums/TearFlags.md) TearFlags {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE. Various [TearFlags](enums/TearFlags.md).

???- example "Example Code"
    This code makes Isaac's tears spectral.
    ```lua

    function mod:OnEvaluateTearFlags(player, flag)
        player.TearFlags = player.TearFlags | TearFlags.TEAR_SPECTRAL
    end
    mod:AddCallback(ModCallbacks.MC_EVALUATE_CACHE, mod.OnEvaluateTearFlags, CacheFlag.CACHE_TEARFLAG)
    ```

___
### Tear·Height {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float TearHeight  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE. How high above the ground is the tear when it spawns?

???- example "Example Code"
    This code gives Isaac a +5 range up.

    ```lua
    function mod:OnEvaluateRange(player, flag)
        -- we give -5 because the TearHeight stat is always negative; the lower the number - the further the tear travels
        player.TearHeight = player.TearHeight - 5
    end
    mod:AddCallback(ModCallbacks.MC_EVALUATE_CACHE, mod.OnEvaluateRange, CacheFlag.CACHE_RANGE)
    ```

___
### Tear·Range {: aria-label='Variables' }
[ ](#){: .reporplus .tooltip .badge }
#### float TearRange  {: .copyable aria-label='Variables' }
Player stat - Only change this in a callback to MC_EVALUATE_CACHE. How far should a tear go when it spawns?

???+ info "Info"
    This stat needs to be multiplied by 40, because it calculates the range based on tile length.

???- example "Example Code"
    This code gives Isaac a +2 range up.

    ```lua
    function mod:OnEvaluateRange(player, flag)
        player.TearRange = player.TearRange + (2 * 40)
    end
    mod:AddCallback(ModCallbacks.MC_EVALUATE_CACHE, mod.OnEvaluateRange, CacheFlag.CACHE_RANGE)
    ```

___
### Tears·Offset {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) TearsOffset  {: .copyable aria-label='Variables' }
