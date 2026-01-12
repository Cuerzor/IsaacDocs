---
tags:
  - Class
---
# Class "Room"

???+ info
    你可以通过以下函数获取此类:

    * [Game:GetRoom()](Game.md#getroom)
    * [Level:GetCurrentRoom()](Level.md#getcurrentroom)

    ???+ example "示例代码"
        ```lua
        local room = Game():GetRoom()
        ```

## 函数
### Check·Line () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### (boolean, [Vector](Vector.md)) CheckLine ( [Vector](Vector.md) Pos1, [Vector](Vector.md) Pos2, LinecheckMode Mode, int GridPathThreshold = 0, boolean IgnoreWalls = false, boolean IgnoreCrushable = false ) {: .copyable aria-label='Functions' }
返回2个值:

- boolean: 如果 `Pos1` 和 `Pos2` 之间没有障碍物则为 `true`,否则为 `false`。

- [Vector](Vector.md): 从 `Pos1` 到 `Pos2` 的第一个命中位置(如果射线没有击中任何东西则返回 `Pos2`)。

???+ note "LinecheckMode 说明"
    LinecheckMode 伪枚举:

    **0** : 使射线检测与任何阻碍地面移动的物体碰撞。

    **1** : 0的简化版本,但不太可靠(例如,如果对角相邻岩石之间可以获得视线,可能返回 `true`)。

    **2** : 用于爆炸,只与墙壁和不可破坏的方块碰撞。

    **3** : 只与可以阻挡抛射物的障碍物碰撞。

???+ note "GridPathThreshold 说明"
    GridPath 值伪枚举:

    **900**  : 由某些敌人在穿过格子时设置。降低该格子对寻路者的优先级。随时间以100为步长衰减。

    **950**  : 由火堆设置。降低该格子对寻路者的优先级。不会衰减。

    **1000** : 由Grid Entity设置。使该格子对寻路者无效。阻碍地面玩家移动。不会衰减。

    **3000** : 由陷阱设置。使该格子对寻路者无效。阻碍地面玩家移动。不会衰减。

    **3999** : 由石像头设置。使该格子对寻路者无效。阻碍地面玩家移动。降至900后随时间以100为步长衰减(石像头每帧重置该值)。
___
### Damage·Grid () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean DamageGrid ( int Index, int Damage ) {: .copyable aria-label='Functions' }
对Grid Entity造成伤害,目前涉及 [GridEntityPoop](GridEntityPoop.md) 和 GridEntity_Fire。如果找到可受伤的实体(并可能造成伤害)则返回true,否则返回false。被眼泪、炸弹、某些NPC等使用。
___
### Damage·Grid·With·Source () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### boolean DamageGridWithSource ( int Index, int Damage, [EntityRef](EntityRef.md) Source ) {: .copyable aria-label='Functions' }
___
### Destroy·Grid () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean DestroyGrid ( int Index, boolean Immediate ) {: .copyable aria-label='Functions' }
内部调用DamageGrid来对Poop/Fire造成伤害,移除岩石并打开隐藏门。
如果有东西被摧毁则返回 `true`。
___
### Destroy·Grid·With·Source () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### boolean DestroyGridWithSource ( int Index, boolean Immediate, [EntityRef](EntityRef.md) Source ) {: .copyable aria-label='Functions' }
___
### Emit·Blood·From·Walls () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void EmitBloodFromWalls ( int Duration, int Count ) {: .copyable aria-label='Functions' }

___
### Find·Free·Pickup·Spawn·Position () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [Vector](Vector.md) FindFreePickupSpawnPosition ( [Vector](Vector.md) Pos, float InitialStep = 0, boolean AvoidActiveEntities = false, boolean AllowPits = false ) {: .copyable aria-label='Functions' }
从 `Pos` 开始,尝试找到一个自由的生成位置,使新生成的拾取物不会与已生成的拾取物或固体Grid元素(如岩石或陷阱)碰撞。返回的位置将对齐到网格。如果找不到自由位置,则返回原始位置(对齐到网格)。
___
### Find·Free·Tile·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) FindFreeTilePosition ( [Vector](Vector.md) Pos, float DistanceThreshold ) {: .copyable aria-label='Functions' }
基于位置查找最近的自由格子。如果采样的格子的平方距离小于 `DistanceThresholdSQ`,则立即停止。
___
### Get·Alive·Bosses·Count () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetAliveBossesCount ( ) {: .copyable aria-label='Functions' }

___
### Get·Alive·Enemies·Count () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetAliveEnemiesCount ( ) {: .copyable aria-label='Functions' }

___
### Get·Award·Seed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetAwardSeed ( ) {: .copyable aria-label='Functions' }

___
### Get·Backdrop·Type () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [BackdropType](enums/BackdropType.md) GetBackdropType ( ) {: .copyable aria-label='Functions' }
返回当前房间的BackdropType。

___
### Get·Boss·ID () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetBossID ( ) {: .copyable aria-label='Functions' }
返回房间中第一个首领的boss ID。否则返回0。

这将返回当前房间的sub-type,因为这个值用于确定进入时显示的boss头像。

boss ID不等于boss的实体类型;它是entities2.xml文件中"bossID"属性里的一个单独的值。

___
### Get·Bottom·Right·Pos () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetBottomRightPos ( ) {: .copyable aria-label='Functions' }
返回房间右下角的位置,在墙边界内部。

___
### Get·Broken·Watch·State () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetBrokenWatchState ( ) {: .copyable aria-label='Functions' }
返回房间是否被减速、加速或均无。

???+ note "说明"
    返回值:

    **0**: 房间既未减速也未加速

    **1**: 房间被减速,可能是因为损坏的怀表或“好困...”药丸

    **2**: 房间被加速,可能是因为损坏的怀表或“好兴奋！！！”药丸

___
### Get·Center·Pos () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetCenterPos ( ) {: .copyable aria-label='Functions' }
返回房间中心位置。

___
### Get·Clamped·Grid·Index () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetClampedGridIndex ( [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' }
返回位于 `Position` 的网格索引。如果 `Position` 超出边界,则锁定到最近的网格索引。

___
### Get·Clamped·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetClampedPosition ( [Vector](Vector.md) Pos, float Margin ) {: .copyable aria-label='Functions' }
返回被锁定在房间墙壁内的 `Pos`,距离边界有 `Margin` 单位的半径。

___
### Get·Decoration·Seed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetDecorationSeed ( ) {: .copyable aria-label='Functions' }

___
### Get·Delirium·Distance () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetDeliriumDistance ( ) {: .copyable aria-label='Functions' }

___
### Get·Devil·Room·Chance () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### float GetDevilRoomChance ( ) {: .copyable aria-label='Functions' }

这给出了当前层的总恶魔房百分比。它不会像在属性显示屏中看到的那样将其拆分为恶魔和天使百分比。它实际上是二元性的百分比。不能生成恶魔房的楼层(例如地下室I)也会有这个值，所以请小心。该值可以大于100%。

???- example "示例代码"
    ```lua
    -- 此代码展示了如何将room:GetDevilRoomChance转换为属性显示屏中显示的单独的恶魔和天使百分比
    -- 此代码截至2024年1月的忏悔版本,其他版本可能有不同的值
    local game = Game()

    -- tainted lazarus is an interesting edge case where you flip between an active and inactive player
    -- the inactive player is not available in repentance's api
    -- if the inactive player picked up certain items (e.g. key pieces with lazarusshared tag) then calling HasCollectible w/ "false" on the active player will still return true
    -- unfortunately, this doesn't work for all items that we care about (eucharist, book of virtues, act of contrition)
    -- repentogon's PlayerManager is able to check against the inactive player's items (via lazarussharedglobal tag)
    -- repentogon is recommended here if you're playing as tainted lazarus and want to make your numbers match what the game is calculating
    local function anyPlayerHasCollectible(collectible)
      if REPENTOGON then
        return PlayerManager.AnyoneHasCollectible(collectible)
      else
        for i = 0, game:GetNumPlayers() - 1 do
          local player = game:GetPlayer(i)

          if player:HasCollectible(collectible, false) then
            return true
          end
        end

        return false
      end
    end

    -- the same tainted lazarus + repentogon logic applies to trinkets (rosary bead)
    local function anyPlayerHasTrinket(trinket)
      if REPENTOGON then
        return PlayerManager.AnyoneHasTrinket(trinket)
      else
        for i = 0, game:GetNumPlayers() - 1 do
          local player = game:GetPlayer(i)

          if player:HasTrinket(trinket, false) then
            return true
          end
        end

        return false
      end
    end

    local function getDevilAngelRoomChance()
      local level = game:GetLevel()
      local room = level:GetCurrentRoom()
      local totalChance = math.min(room:GetDevilRoomChance(), 1.0)

      local angelRoomSpawned = game:GetStateFlag(GameStateFlag.STATE_FAMINE_SPAWNED) -- repurposed
      local devilRoomSpawned = game:GetStateFlag(GameStateFlag.STATE_DEVILROOM_SPAWNED)
      local devilRoomVisited = game:GetStateFlag(GameStateFlag.STATE_DEVILROOM_VISITED)

      local devilRoomChance = 1.0
      if anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_EUCHARIST) then
        devilRoomChance = 0.0
      elseif devilRoomSpawned and devilRoomVisited and game:GetDevilRoomDeals() > 0 then -- devil deals locked in
        if anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_BOOK_OF_VIRTUES) or
           anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_ACT_OF_CONTRITION) or
           level:GetAngelRoomChance() > 0.0 -- confessional, sac room
        then
          devilRoomChance = 0.5
        end
      elseif devilRoomSpawned or anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_BOOK_OF_VIRTUES) or level:GetAngelRoomChance() > 0.0 then
        if not (devilRoomVisited or angelRoomSpawned) then
          devilRoomChance = 0.0
        else
          devilRoomChance = 0.5
        end
      end

      -- https://bindingofisaacrebirth.fandom.com/wiki/Angel_Room#Angel_Room_Generation_Chance
      if devilRoomChance == 0.5 then
        if anyPlayerHasTrinket(TrinketType.TRINKET_ROSARY_BEAD) then
          devilRoomChance = devilRoomChance * (1.0 - 0.5)
        end
        if game:GetDonationModAngel() >= 10 then -- donate 10 coins
          devilRoomChance = devilRoomChance * (1.0 - 0.5)
        end
        if anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_KEY_PIECE_1) then
          devilRoomChance = devilRoomChance * (1.0 - 0.25)
        end
        if anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_KEY_PIECE_2) then
          devilRoomChance = devilRoomChance * (1.0 - 0.25)
        end
        if level:GetStateFlag(LevelStateFlag.STATE_EVIL_BUM_KILLED) then
          devilRoomChance = devilRoomChance * (1.0 - 0.25)
        end
        if level:GetStateFlag(LevelStateFlag.STATE_BUM_LEFT) and not level:GetStateFlag(LevelStateFlag.STATE_EVIL_BUM_LEFT) then
          devilRoomChance = devilRoomChance * (1.0 - 0.1)
        end
        if level:GetStateFlag(LevelStateFlag.STATE_EVIL_BUM_LEFT) and not level:GetStateFlag(LevelStateFlag.STATE_BUM_LEFT) then
          devilRoomChance = devilRoomChance * (1.0 + 0.1)
        end
        if level:GetAngelRoomChance() > 0.0 or
           (level:GetAngelRoomChance() < 0.0 and (anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_BOOK_OF_VIRTUES) or anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_ACT_OF_CONTRITION)))
        then
          devilRoomChance = devilRoomChance * (1.0 - level:GetAngelRoomChance())
        end
        if anyPlayerHasCollectible(CollectibleType.COLLECTIBLE_BOOK_OF_VIRTUES) then
          devilRoomChance = devilRoomChance * (1.0 - 0.25)
        end
        devilRoomChance = math.max(0.0, math.min(devilRoomChance, 1.0))
      end

      local angelRoomChance = 1.0 - devilRoomChance
      return totalChance * devilRoomChance, totalChance * angelRoomChance
    end
    ```
___
### Get·Door () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [GridEntityDoor](GridEntityDoor.md) GetDoor ( [DoorSlot](enums/DoorSlot.md) Slot ) {: .copyable aria-label='Functions' data-altreturn='nil' }
返回给定 [DoorSlot](enums/DoorSlot.md) 位置的 [GridEntityDoor](GridEntityDoor.md)。如果没有门在那里则返回 `nil`。

___
### Get·Door·Slot·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetDoorSlotPosition ( [DoorSlot](enums/DoorSlot.md) Slot ) {: .copyable aria-label='Functions' }

___
### Get·Dungeon·Rock·Idx () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetDungeonRockIdx ( ) {: .copyable aria-label='Functions' }

___
### Get·Enemy·Damage·Inflicted () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### float GetEnemyDamageInflicted ( ) {: .copyable aria-label='Functions' }
返回当前帧内房间中所有敌人损失的总HP数量。

用于根据造成的伤害量充能的道具，例如“狂怒！”。

___
### Get·Entities () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityList](CppContainer_EntityList.md) GetEntities ( ) {: .copyable aria-label='Functions' }
返回一个指向存储当前房间中所有实体的数组的原始指针。因此,迭代返回值将始终迭代当前逻辑帧期间房间中存在的实体,而不管GetEntities最初何时被调用。

这种行为与 [`Isaac.GetRoomEntities()`](Isaac.md#getroomentities) 不同,后者返回的是调用函数时房间中实体的可迭代表。**对于大多数用例,建议使用 [`Isaac.GetRoomEntities()`](Isaac.md#getroomentities)**!

???- example "示例代码"
    此代码打印房间中每个实体的Type、Variant和SubType。

    ```lua
    local room = Game():GetRoom()
    local roomEntities = room:GetEntities()
    for i = 0, #roomEntities - 1 do
        local entity = roomEntities:Get(i)
        print(entity.Type, entity.Variant, entity.SubType)
    end

    ```
___
### Get·Frame·Count () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetFrameCount ( ) {: .copyable aria-label='Functions' }
返回房间活跃的帧数。当玩家离开房间或退出运行时重置为 `0`。

___
### Get·Grid·Collision () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [GridCollisionClass](enums/GridCollisionClass.md) GetGridCollision ( int GridIndex ) {: .copyable aria-label='Functions' }

返回此网格索引处的Grid Entity的 [GridCollisionClass](enums/GridCollisionClass.md)。

___
### Get·Grid·Collision·At·Pos () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [GridCollisionClass](enums/GridCollisionClass.md) GetGridCollisionAtPos ( [Vector](Vector.md) Pos ) {: .copyable aria-label='Functions' }
返回房间中此位置处的Grid Entity的 [GridCollisionClass](enums/GridCollisionClass.md)。

___
### Get·Grid·Entity () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [GridEntity](GridEntity.md) GetGridEntity ( int Index ) {: .copyable aria-label='Functions' data-altreturn='nil' }
返回此网格索引处的 [GridEntity](GridEntity.md)。如果找不到 [GridEntity](GridEntity.md) 则返回 `nil`。

___
### Get·Grid·Entity·From·Pos () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [GridEntity](GridEntity.md) GetGridEntityFromPos ( [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' data-altreturn='nil' }
返回房间中此位置处的 [GridEntity](GridEntity.md)。如果找不到 [GridEntity](GridEntity.md) 则返回 `nil`。

___
### Get·Grid·Height () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetGridHeight ( ) {: .copyable aria-label='Functions' }

___
### Get·Grid·Index () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetGridIndex ( [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' }
返回位于 `Position` 的网格索引。对于无效索引返回 `-1`。
___
### Get·Grid·Path () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetGridPath ( int Index ) {: .copyable aria-label='Functions' }
Grid path是网格方块的一个属性,表示穿过该网格单元的“成本”。它用于寻路算法,该算法搜索到给定位置的最低成本路径。如果网格单元的值大于0,它可以阻止Grid Entity在该方块上生成。因此,您可以通过将Grid path重置为0来绕过它,然后生成Grid Entity。

???+ note "说明"
    GridPath 值伪枚举:

    **900**  : 由某些敌人在穿过格子时设置。降低该格子对寻路者的优先级。随时间以100为步长衰减。

    **950**  : 由火堆设置。降低该格子对寻路者的优先级。不会衰减。

    **1000** : 由Grid Entity设置。使该格子对寻路者无效。阻碍地面玩家移动。不会衰减。

    **3000** : 由陷阱设置。使该格子对寻路者无效。阻碍地面玩家移动。不会衰减。

    **3999** : 由石像头设置。使该格子对寻路者无效。阻碍地面玩家移动。降至900后随时间以100为步长衰减(石像头每帧重置该值)。
___
### Get·Grid·Path·From·Pos () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetGridPathFromPos ( [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' }

???+ note "说明"
    GridPath 值伪枚举:

    **900**  : 由某些敌人在穿过格子时设置。降低该格子对寻路者的优先级。随时间以100为步长衰减。

    **950**  : 由火堆设置。降低该格子对寻路者的优先级。不会衰减。

    **1000** : 由Grid Entity设置。使该格子对寻路者无效。阻碍地面玩家移动。不会衰减。

    **3000** : 由陷阱设置。使该格子对寻路者无效。阻碍地面玩家移动。不会衰减。

    **3999** : 由石像头设置。使该格子对寻路者无效。阻碍地面玩家移动。降至900后随时间以100为步长衰减(石像头每帧重置该值)。
___
### Get·Grid·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetGridPosition ( int GridIndex ) {: .copyable aria-label='Functions' }
返回 `GridIndex` 的世界位置,即使 `GridIndex` 是无效的。
___
### Get·Grid·Size () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetGridSize ( ) {: .copyable aria-label='Functions' }

___
### Get·Grid·Width () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetGridWidth ( ) {: .copyable aria-label='Functions' }

___
### Get·Laser·Target () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetLaserTarget ( [Vector](Vector.md) Pos, [Vector](Vector.md) Dir ) {: .copyable aria-label='Functions' }
返回激光束(科技、机器宝宝)的命中位置。通常这是直线上遇到的第一个大便、火、岩石、TNT或墙壁。

___
### Get·Lava·Intensity () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### float GetLavaIntensity ( ) {: .copyable aria-label='Functions' }
通常返回1,除非熔岩正在被“冲水！”或其他房间洪水效果冷却,在这种情况下它将逐渐减少到0。

___
### Get·Lighting·Alpha () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### float GetLightingAlpha ( ) {: .copyable aria-label='Functions' }

___
### Get·LRoom·Area·Desc () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### LRoomAreaDesc GetLRoomAreaDesc ( ) {: .copyable aria-label='Functions' }

???+ bug "Bug"
    由于它返回UserData,该函数不可用,因此损坏。
___
### Get·LRoom·Tile·Desc () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### LRoomTileDesc GetLRoomTileDesc ( ) {: .copyable aria-label='Functions' }

???+ bug "Bug"
    由于它返回UserData,该函数不可用,因此损坏。
___
### Get·Random·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetRandomPosition ( float Margin ) {: .copyable aria-label='Functions' }
返回房间中的一个随机位置,距离任何障碍物有 `Margin` 单位的半径。此位置不与网格对齐。

___
### Get·Random·Tile·Index () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetRandomTileIndex ( int Seed ) {: .copyable aria-label='Functions' }

___
### Get·Red·Heart·Damage () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean GetRedHeartDamage ( ) {: .copyable aria-label='Functions' }
如果玩家在房间中对红心容器受到非自我造成的伤害,则返回 `true`。如果玩家离开房间或退出运行,则重置为 `false`。

___
### Get·Render·Mode () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [RenderMode](enums/RenderMode.md) GetRenderMode ( ) {: .copyable aria-label='Functions' }
返回RenderMode枚举,可用于根据上下文以不同方式渲染实体(例如自定义水面反射)。
___
### Get·Render·Scroll·Offset () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) GetRenderScrollOffset ( ) {: .copyable aria-label='Functions' }
摄像机滚动偏移和屏幕抖动偏移都在这里表示。
___
### Get·Render·Surface·Top·Left () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) GetRenderSurfaceTopLeft ( ) {: .copyable aria-label='Functions' }
地板和墙壁纹理将被渲染的位置。
___
### Get·Room·Config·Stage () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetRoomConfigStage ( ) {: .copyable aria-label='Functions' }
返回该房间设计所适用的关卡ID。

???- note "Stage IDs (对应stages.xml中的ID)"

	|DLC|ID|关卡|注释|
	|:--|:--|:--|:--|
	|[ ](#){: .alldlc .tooltip .badge }|0 |Special Rooms |  |
	|[ ](#){: .alldlc .tooltip .badge }|1 |Basement |  |
	|[ ](#){: .alldlc .tooltip .badge }|2 |Cellar |  |
	|[ ](#){: .alldlc .tooltip .badge }|3 |Burning Basement |  |
	|[ ](#){: .alldlc .tooltip .badge }|4 |Caves |  |
	|[ ](#){: .alldlc .tooltip .badge }|5 |Catacombs |  |
	|[ ](#){: .alldlc .tooltip .badge }|6 |Flooded Caves |  |
	|[ ](#){: .alldlc .tooltip .badge }|7 |Depths |  |
	|[ ](#){: .alldlc .tooltip .badge }|8 |Necropolis |  |
	|[ ](#){: .alldlc .tooltip .badge }|9 |Dank Depths |  |
	|[ ](#){: .alldlc .tooltip .badge }|10 |Womb |  |
	|[ ](#){: .alldlc .tooltip .badge }|11 |Utero |  |
	|[ ](#){: .alldlc .tooltip .badge }|12 |Scarred Womb |  |
	|[ ](#){: .alldlc .tooltip .badge }|13 |Blue Womb |  |
	|[ ](#){: .alldlc .tooltip .badge }|14 |Sheol |  |
	|[ ](#){: .alldlc .tooltip .badge }|15 |Cathedral |  |
	|[ ](#){: .alldlc .tooltip .badge }|16 |Dark Room |  |
	|[ ](#){: .alldlc .tooltip .badge }|17 |Chest |  |
	|[ ](#){: .abp .tooltip .badge }|18 |Greed Special Rooms |  |
	|[ ](#){: .abp .tooltip .badge }|19 |Greed Basement |  |
	|[ ](#){: .abp .tooltip .badge }|20 |Greed Caves |  |
	|[ ](#){: .abp .tooltip .badge }|21 |Greed Depths |  |
	|[ ](#){: .abp .tooltip .badge }|22 |Greed Womb |  |
	|[ ](#){: .abp .tooltip .badge }|23 |Greed Sheol |  |
	|[ ](#){: .alldlc .tooltip .badge }|24 |The Shop |  |
	|[ ](#){: .alldlc .tooltip .badge }|25 |Ultra Greed |  |
	|[ ](#){: .alldlc .tooltip .badge }|26 |The Void |  |
	|[ ](#){: .reporplus .tooltip .badge }|27 |Downpour |  |
	|[ ](#){: .reporplus .tooltip .badge }|28 |Dross |  |
	|[ ](#){: .reporplus .tooltip .badge }|29 |Mines |  |
	|[ ](#){: .reporplus .tooltip .badge }|30 |Ashpit |  |
	|[ ](#){: .reporplus .tooltip .badge }|31 |Mausoleum |  |
	|[ ](#){: .reporplus .tooltip .badge }|32 |Gehenna |  |
	|[ ](#){: .reporplus .tooltip .badge }|33 |Corpse |  |
	|[ ](#){: .reporplus .tooltip .badge }|35 |Home |Stage ID 34不存在。 |
	|[ ](#){: .reporplus .tooltip .badge }|36 |Backwards |这些房间在Ascent期间使用。 |

___
### Get·Room·Shape () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [RoomShape](enums/RoomShape.md) GetRoomShape ( ) {: .copyable aria-label='Functions' }

___
### Get·Second·Boss·ID () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetSecondBossID ( ) {: .copyable aria-label='Functions' }
返回坏事成双房间中第二个boss的boss ID。否则返回0。

boss ID不等于头目的实体类型;它是entities2.xml文件中"bossID"属性里的一个单独的值。

检查此值并不足以检测坏事成双房间，因为坏事成双房间可能包含两个相同的boss。如果是这种情况,那么第二个boss ID的值将等于0。

___
### Get·Seeded·Collectible () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [CollectibleType](enums/CollectibleType.md) GetSeededCollectible ( int Seed, bool NoDecrease = false ) {: .copyable aria-label='Functions' }
当 `NoDecrease` 为true时,返回的道具将不会从它们来自的道具池中移除。

___
### Get·Shop·Level () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetShopLevel ( ) {: .copyable aria-label='Functions' }

___
### Get·Spawn·Seed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetSpawnSeed ( ) {: .copyable aria-label='Functions' }

___
### Get·Tinted·Rock·Idx () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetTintedRockIdx ( ) {: .copyable aria-label='Functions' }

___
### Get·Top·Left·Pos () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) GetTopLeftPos ( ) {: .copyable aria-label='Functions' }
返回墙壁内部的左上角位置。
___
### Get·Type () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [RoomType](enums/RoomType.md) GetType ( ) {: .copyable aria-label='Functions' }

___
### Get·Water·Current () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### [Vector](Vector.md) GetWaterCurrent ( ) {: .copyable aria-label='Functions' }
返回与房间中任何水流对应的向量。

___
### Has·Curse·Mist () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean HasCurseMist ( ) {: .copyable aria-label='Functions' }
如果玩家在废弃矿井内,则返回 `true`。

___
### Has·Lava () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean HasLava ( ) {: .copyable aria-label='Functions' }
如果房间包含熔岩,则返回 `true`。

???- warning "警告"
    即使没有陷阱使熔岩可见,如果房间包含熔岩,此函数仍将返回 `true`。

___
### Has·Slow·Down () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasSlowDown ( ) {: .copyable aria-label='Functions' }

返回房间当前是否受到“好困”药丸的影响。如果之前调用了 [SetSlowDown](#setslowdown) 且指定的 `Duration` 尚未过期,该函数也将返回 `true`。

请注意,如果“好困”药丸的效果是通过损坏的怀表触发的,此函数将返回 `false`。要检查该场景,请使用 [GetBrokenWatchState](#getbrokenwatchstate) 函数。

如果玩家受到怀表的影响,此函数也将返回 `false`。要检查该场景,请检查玩家是否拥有怀表。

___
### Has·Trigger·Pressure·Plates () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasTriggerPressurePlates ( ) {: .copyable aria-label='Functions' }
如果房间中有一个或多个压力板,则返回 `true`。

???- warning "警告"
    要查看压力板是否被按下,您必须遍历房间中的Grid Entity。

___
### Has·Water () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasWater ( ) {: .copyable aria-label='Functions' }

___
### Has·Water·Pits () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasWaterPits ( ) {: .copyable aria-label='Functions' }
如果房间包含有液体的陷阱(例如矿洞中的熔岩、阴湿深牢中的沥青等),则返回 `true`。

___
### Invalidate·Pickup·Vision () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void InvalidatePickupVision ( ) {: .copyable aria-label='Functions' }
让来自嗝屁猫的眼睛的宝箱预览在下一帧更新。

___
### Is·Ambush·Active () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsAmbushActive ( ) {: .copyable aria-label='Functions' }

___
### Is·Ambush·Done () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsAmbushDone ( ) {: .copyable aria-label='Functions' }

___
### Is·Clear () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsClear ( ) {: .copyable aria-label='Functions' }

___
### Is·Current·Room·Last·Boss () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsCurrentRoomLastBoss ( ) {: .copyable aria-label='Functions' }
如果当前房间是XL楼层上的第二个头目房,则返回 `true`。否则返回 `false`。

___
### Is·Door·Slot·Allowed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsDoorSlotAllowed ( [DoorSlot](enums/DoorSlot.md) Slot ) {: .copyable aria-label='Functions' }
返回提供的门槽对于当前房间是否有效。这取决于STB/XML文件中的房间定义。(Basement Renovator将有效的门显示为棕色,将无效的门显示为白色。)此方法返回的值与给定槽位是否存在门无关。

例如，在楼层的起始房间中，此方法将对 `DoorSlot.LEFT0`、`DoorSlot.UP0`、`Doorslot.RIGHT0` 和 `DoorSlot.DOWN0` 返回true,对所有其他值返回false(无论有哪些门存在)。

例如，洞穴中有一个相对常见的1x1房间，有四只炸弹苍蝇和一座从上门到下门的窄桥。在这个房间中,左右两侧的门被禁用。在这个房间中,此方法将对 `DoorSlot.UP0` 和 `DoorSlot.DOWN0` 返回true,对所有其他值返回false(无论有哪些门存在)。

___
### Is·First·Enemy·Dead () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsFirstEnemyDead ( ) {: .copyable aria-label='Functions' }

___
### Is·First·Visit () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsFirstVisit ( ) {: .copyable aria-label='Functions' }

___
### Is·Initialized () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsInitialized ( ) {: .copyable aria-label='Functions' }

___
### Is·LShaped·Room () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsLShapedRoom ( ) {: .copyable aria-label='Functions' }

___
### Is·Mirror·World () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean IsMirrorWorld ( ) {: .copyable aria-label='Functions' }
如果玩家在镜子维度内,则返回true。

___
### Is·Position·In·Room () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsPositionInRoom ( [Vector](Vector.md) Pos, float Margin ) {: .copyable aria-label='Functions' }
如果给定的位置在房间内,则返回 `true`。`Margin` 用作位置周围的半径,该半径也需要在房间边界内。房间边界是可行走区域和墙壁之间的位置。因此,墙壁内和黑色虚空中的位置确实被计为房间“外部”。

___
### Is·Sacrifice·Done () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsSacrificeDone ( ) {: .copyable aria-label='Functions' }

___
### Keep·Doors·Closed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void KeepDoorsClosed ( ) {: .copyable aria-label='Functions' }

___
### Mama·Mega·Explosion () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void MamaMegaExplosion ( [Vector](Vector.md) Position ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void MamaMegaExplosion ( [Vector](Vector.md) Position = Vector.Zero, [EntityPlayer](EntityPlayer.md) Player = nil ) {: .copyable aria-label='Functions' }

___
### Play·Music () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void PlayMusic ( ) {: .copyable aria-label='Functions' }
播放此房间使用的音乐曲目。在播放不同的曲目后用于重置音乐。

___
### Remove·Door () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveDoor ( [DoorSlot](enums/DoorSlot.md) Slot ) {: .copyable aria-label='Functions' }

___
### Remove·Grid·Entity () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveGridEntity ( int GridIndex, int PathTrail, boolean KeepDecoration ) {: .copyable aria-label='Functions' }

* `GridIndex` 是使用 `debug 11` 控制台命令显示的网格位置。
* `PathTrail` 是要在方块上留下的“成本”。在大多数情况下,您希望为此参数传递 。

请注意,在移除Grid Entity后,在一帧经过之前,您无法在同一格子上生成另一个Grid Entity。如果绝对需要这样做,您可以通过两种不同的方式绕过此限制:

1. 通过在移除旧Grid Entity和生成新Grid Entity之间调用 [`Room:Update()`](#update) 方法,您可以模拟一帧经过。然而,这可能会产生其他不需要的副作用,因此只建议作为最后的手段。具体来说,`Room:Update` 将更新房间中的每个实体,包括玩家,使他们继续沿着已经移动的方向移动。此外,如果在PostNewRoom回调中调用 `Room:Update`,它仍然会导致玩家漂移,即使他们站着不动。(这是因为在回调触发时,他们的速度尚未归零。)
2. 通过在被移除的Grid Entity被移除后调用 [`GridEntity:Update()`](GridEntity.md#update),您将能够立即在同一格子上生成另一个Grid Entity。然而,新的Grid Entity将在帧结束时自动被移除,因此您必须在下一帧再次生成它。此方法也可能导致不需要的副作用,例如爆炸无法正确地摧毁岩石(因为它会在后续帧上被错误地重新生成)。

___
### Render () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Render ( ) {: .copyable aria-label='Functions' }

___
### Respawn·Enemies () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RespawnEnemies ( ) {: .copyable aria-label='Functions' }
用于七面骰道具。
___
### Screen·Wrap·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) ScreenWrapPosition ( [Vector](Vector.md) Pos, float Margin ) {: .copyable aria-label='Functions' }
返回屏幕包裹后的 `Pos` (如果它刚好在房间右侧外面,它将被移动到房间的左侧,依此类推)

???- note "说明"
     这只会包裹点一次,因此如果它跨过了多个包裹平面,它只会在最接近的平面上包裹。对于包裹一个跨过了两个平面的位置(例如在房间左上角外面),请迭代调用此函数。
___
### Set·Ambush·Done () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetAmbushDone ( boolean Value ) {: .copyable aria-label='Functions' }

___
### Set·Broken·Watch·State () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetBrokenWatchState ( int State ) {: .copyable aria-label='Functions' }
加速、减速或从当前房间移除这些状态中的任何一个。有关 `State` 的不同值,请参见 [GetBrokenWatchState](#getbrokenwatchstate) 中的说明部分。

___
### Set·Card·Against·Humanity () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetCardAgainstHumanity ( ) {: .copyable aria-label='Functions' }

___
### Set·Clear () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetClear ( boolean Clear ) {: .copyable aria-label='Functions' }
用于天使房，以便当天使生成时可以将房间清理标志设置为false。

___
### Set·First·Enemy·Dead () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetFirstEnemyDead ( boolean Value ) {: .copyable aria-label='Functions' }

___
### Set·Floor·Color () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetFloorColor ( [Color](Color.md) FloorColor ) {: .copyable aria-label='Functions' }
允许您对当前房间的地板纹理应用颜色修改器。

???- example "示例代码"
    此代码将地板颜色更改为红色。
    ```lua
    Game():GetRoom():SetFloorColor(Color(1,1,1,1,255,0,0))
    ```

___
### Set·Grid·Path () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean SetGridPath ( int Index, int Value ) {: .copyable aria-label='Functions' }
Grid path是网格方块的一个属性,表示穿过该网格单元的“成本”。它用于寻路算法,该算法搜索到给定位置的最低成本路径。如果网格单元的值大于 `0`,它可以阻止Grid Entity在该方块上生成。因此,您可以通过将Grid path重置为0来绕过它,然后生成Grid Entity。

???+ note "说明"
    GridPath 值伪枚举:

    **900**  : 由某些敌人在穿过格子时设置。降低该格子对寻路者的优先级。随时间以100为步长衰减。

    **950**  : 由火堆设置。降低该格子对寻路者的优先级。不会衰减。

    **1000** : 由Grid Entity设置。使该格子对寻路者无效。阻碍地面玩家移动。不会衰减。

    **3000** : 由陷阱设置。使该格子对寻路者无效。阻碍地面玩家移动。不会衰减。

    **3999** : 由石像头设置。使该格子对寻路者无效。阻碍地面玩家移动。降至900后随时间以100为步长衰减(石像头每帧重置该值)。
___
### Set·Red·Heart·Damage () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetRedHeartDamage ( ) {: .copyable aria-label='Functions' }

___
### Set·Sacrifice·Done () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetSacrificeDone ( boolean Done ) {: .copyable aria-label='Functions' }

___
### Set·Slow·Down () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetSlowDown ( int Duration ) {: .copyable aria-label='Functions' }
对 `Duration` 个逻辑帧应用减速效果(每秒30个逻辑帧)。

使用负的 `Duration` 将不会做任何事情,而不是像人们可能期望的那样使减速永久持续。

???+ bug "Bug"
    此函数只会对玩家应用减速效果,而不会对房间的所有实体应用。如果您想对房间中的所有实体应用减速效果,请考虑使用 [SetBrokenWatchState](#setbrokenwatchstate),将 `State` 设置为 `1`,并在您的脚本中添加一个计时器来计算经过的帧数。

___
### Set·Wall·Color () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetWallColor ( [Color](Color.md) WallColor ) {: .copyable aria-label='Functions' }
允许您对当前房间的墙壁纹理应用颜色修改器。

???- example "示例代码"
    此代码将墙壁颜色更改为红色。
    ```lua
    Game():GetRoom():SetWallColor(Color(1,1,1,1,255,0,0))
    ```

___
### Shop·Reshuffle () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ShopReshuffle ( boolean KeepCollectibleIdx, boolean ReselectSaleItem ) {: .copyable aria-label='Functions' }

___
### Shop·Restock·Full () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ShopRestockFull ( ) {: .copyable aria-label='Functions' }
像使用补货机一样，补充商店库存并重新随机物品。

___
### Shop·Restock·Partial () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ShopRestockPartial ( ) {: .copyable aria-label='Functions' }

___
### Spawn·Clear·Award () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SpawnClearAward ( ) {: .copyable aria-label='Functions' }

___
### Spawn·Grid·Entity () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean SpawnGridEntity ( int GridIndex, [GridEntityType](enums/GridEntityType.md) Type, int Variant, int Seed, int VarData ) {: .copyable aria-label='Functions' }

___
### Stop·Rain () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void StopRain ( ) {: .copyable aria-label='Functions' }
停止房间中的任何雨效果。

___
### Trigger·Clear () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void TriggerClear ( boolean Silent = false ) {: .copyable aria-label='Functions' }
触发所有房间清除效果(并不实际清除房间)。
通过将Silent设置为 `true` 可以静音开门声。

___
### Try·Make·Bridge () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TryMakeBridge ( [GridEntity](GridEntity.md) pit, [GridEntity](GridEntity.md) rock ) {: .copyable aria-label='Functions' }
尝试在给定的沟壑上创建一座桥。如果创建成功则返回 `true`。否则返回 `false`。

___
### Try·Place·Ladder () {: aria-label='Functions' }
[ ](#){: .abp .tooltip .badge }
#### void TryPlaceLadder ( [Vector](Vector.md) PlayerPos, [Vector](Vector.md) PlayerVelocity, [Entity](Entity.md) Ladder ) {: .copyable aria-label='Functions' }
此函数在忏悔中被移除。

___
### Try·Spawn·Blue·Womb·Door () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TrySpawnBlueWombDoor ( boolean FirstTime = true, boolean IgnoreTime = false, boolean Force = false ) {: .copyable aria-label='Functions' }
尝试生成一扇通往蓝子宫的门。
如果不在妈妈的心的boss房内，除非将 `Force` 设置为 `true`，否则通常什么都不会发生。

___
### Try·Spawn·Boss·Rush·Door () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TrySpawnBossRushDoor ( boolean IgnoreTime = false, boolean Force = false ) {: .copyable aria-label='Functions' }
尝试生成一扇通往头目车轮战的门。
如果不在妈妈的boss房内，除非将 `Force` 设置为 `true`，否则通常什么都不会发生。

___
### Try·Spawn·Devil·Room·Door () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TrySpawnDevilRoomDoor ( boolean Animate = false, boolean Force = false ) {: .copyable aria-label='Functions' }
尝试生成一扇通往恶魔房或天使房的门。
如果不在头目房内,除非将 `Force` 设置为 `true`，否则通常什么都不会发生。

___
### Try·Spawn·Mega·Satan·Room·Door () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TrySpawnMegaSatanRoomDoor ( boolean Force = false ) {: .copyable aria-label='Functions' }
尝试生成一扇通往超级撒但的门。
如果不在玩具箱/暗室的起始房间内，除非将 `Force` 设置为 `true`，否则通常什么都不会发生。

___
### Try·Spawn·Secret·Exit () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean TrySpawnSecretExit ( boolean Animate = false, boolean Force = false ) {: .copyable aria-label='Functions' }
根据当前楼层，尝试生成一扇通往下水道、矿洞或陵墓的门。
如果不在头目房内，除非将 `Force` 设置为 `true`，否则通常什么都不会发生。

___
### Try·Spawn·Secret·Shop () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean TrySpawnSecretShop ( boolean Force = false ) {: .copyable aria-label='Functions' }
尝试在当前房间内生成一个通往会员商店的活板门。
在商店外或玩家没有持有会员卡时，除非将 `Force` 设置为 `true`，否则通常什么都不会发生。

___
### Try·Spawn·Special·Quest·Door () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean TrySpawnSpecialQuestDoor ( ) {: .copyable aria-label='Functions' }
尝试生成一扇通往下水道中的镜子维度的门，或矿洞中的废弃矿井。

___
### Try·Spawn·The·Void·Door () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TrySpawnTheVoidDoor ( boolean Force = false ) {: .copyable aria-label='Functions' }
尝试生成一扇通往包含虚空传送门的房间的门。
如果在死寂的头目房外，除非将 `Force` 设置为 `true`，否则通常什么都不会发生。

___
### Turn·Gold () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void TurnGold ( ) {: .copyable aria-label='Functions' }
对房间中的所有Grid Entity应用金色色调。这与游戏在击败困难究极贪婪后所做的效果相同。

___
### Update () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Update ( ) {: .copyable aria-label='Functions' }
更新当前房间。

**建议在调用 [Room:RemoveGridEntity()](#removegridentity) 后调用此函数,以正确应用更改。**

???- note "说明"
    需要调用此函数来应用一些更改,例如在已经存在陷阱的位置生成活板门。

    要做到这一点,请移除陷阱,调用Update()函数,然后生成活板门。

???+ bug "Bug"
    如Repentance API Issue Tracker中所述,[作为卡牌功能的一部分调用room:Update()会强制立即使用副手主动物品](https://github.com/Meowlala/RepentanceAPIIssueTracker/issues/211)。

___
### World·To·Screen·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) WorldToScreenPosition ( [Vector](Vector.md) WorldPos ) {: .copyable aria-label='Functions' }

将实体位置转换为可用于渲染到屏幕的位置。
___
