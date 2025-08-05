---
tags:
  - Class
---
# Class "Entity"

???+ info
    首先，请看 [实体介绍](entities/Overview.md).

    可通过以下函数获取 “Entity” 对象:

    ???- info 能获取 “Entity” 对象的列表
        * [EntityList.Get()](CppContainer_EntityList.md#get)
        * [Entity.GetLastChild()](Entity.md#getlastchild)
        * [Entity.GetLastParent()](Entity.md#getlastparent)
        * [Entity.Child](Entity.md#child)
        * [Entity.Parent](Entity.md#parent)
        * [Entity.SpawnerEntity](Entity.md#spawnerentity)
        * [Entity.Target](Entity.md#target)
        * [EntityLaser.BounceLaser()](EntityLaser.md#bouncelaser)
        * [EntityNPC.GetPlayerTarget()](EntityNPC.md#getplayertarget)
        * [EntityNPC.EntityRef](EntityNPC.md#entityref)
        * [EntityPlayer.AddBlueFlies](EntityPlayer.md#addblueflies)
        * [EntityPlayer.AddBlueSpider](EntityPlayer.md#addbluespider)
        * [EntityPlayer.GetActiveWeaponEntity](EntityPlayer.md#getactiveweaponentity)
        * [EntityPlayer.GetNPCTarget](EntityPlayer.md#getnpctarget)
        * [EntityPlayer.GetTractorBeam](EntityPlayer.md#gettractorbeam)
        * [EntityPlayer.ThrowBlueSpider](EntityPlayer.md#throwbluespider)
        * [EntityPlayer.ThrowHeldEntity](EntityPlayer.md#throwheldentity)
        * [EntityPtr](EntityPtr.md#ref)
        * [EntityRef.Entity](EntityRef.md#entity)
        * [EntityTear.StickTarget](EntityTear.md#sticktarget)
        * [Game.Spawn()](Game.md#spawn)
        * [Isaac.Spawn()](Game.md#spawn)

    ???+ example "示例代码"
        `local entity = Isaac.Spawn(EntityType.ENTITY_PICKUP, PickupVariant.PICKUP_COLLECTIBLE, 0, Vector(320,280), Vector(0,0), nil)`

## Class Diagram
--8<-- "docs/snippets/EntityClassDiagram.md"

## Functions
### Add·Burn () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void AddBurn ( [EntityRef](EntityRef.md) Source, int Duration, float Damage ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddBurn ( [EntityRef](EntityRef.md) Source, int Duration, float Damage, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }

为实体添加燃烧效果. `Duration` 是持续帧数（时间）. `Damage` 为每帧造成的伤害.

???- info "持续时间说明"
    `Duration` 至少需要 3 帧才能造成伤害。每次连续的伤害间隔为 20 帧.

    - 2 次伤害 = 23 帧
    - 3 次伤害 = 43 帧
    - 4 次伤害 = 63 帧

    持续时间存在上限：对于玩家实体（EntityPlayer），最大值为 1 个间隔；对于普通实体，最大值为 6 个间隔.

???- example "Example Code"
    This code damages every entity in the room for 1 second with the damage source set to the player. The total damage dealt is 1.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddBurn(EntityRef(player), 30, 1)
    end
    ```

___
### Add·Charmed () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void AddCharmed ( [EntityRef](EntityRef.md) sourceEntity, int Duration ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddCharmed ( [EntityRef](EntityRef.md) sourceEntity, int Duration, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }

为敌人添加魅惑效果。持续时间以帧数为单位。被魅惑的敌人会对玩家友好，并攻击其他敌人.

`:::lua Duration = -1` 效果将永久存在，且敌人会跟随玩家进入不同房间.

???- example "Example Code"
    This code charms every entity in the room for 1 second.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs() do
    	entity:AddCharmed(EntityRef(player), 30)
    end
    ```

___
### Add·Confusion () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddConfusion ( [EntityRef](EntityRef.md) Source, int Duration, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }

为实体添加混乱效果.

???- info "持续时间说明"
    最大持续时间为 5 秒

???- example "Example Code"
    This code confuses every entity in the room for 1 second while ignoring bosses.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddConfusion(EntityRef(player), 30, true)
    end
    ```

___
### Add·Entity·Flags () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddEntityFlags ( int Flags ) {: .copyable aria-label='Functions' }

为实体添加[实体标记](enums/EntityFlag.md)标记用于添加特定效果，如友好状态或对尖刺伤害免疫等。可通过按位拼接同时添加多个标记.

???- example "Example Code"
    This code adds slowing and confusion to the entity.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddEntityFlags(EntityFlag.FLAG_SLOW | EntityFlag.FLAG_CONFUSION)
    end
    ```
___
### Add·Fear () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void AddFear ( [EntityRef](EntityRef.md) Source, int Duration ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddFear ( [EntityRef](EntityRef.md) Source, int Duration, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }

为实体添加恐惧效果.

???- info "持续时间说明"
    最大持续时间为 5 秒

???- example "Example Code"
    This code frightens every entity in the room for 1 second.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddFear(EntityRef(player), 30)
    end
    ```

___
### Add·Freeze () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void AddFreeze ( [EntityRef](EntityRef.md) Source, int Duration ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddFreeze ( [EntityRef](EntityRef.md) Source, int Duration, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }

冻结一个实体，使其无法移动或攻击.

???- info "持续时间说明"
    最大持续时间为 5 秒

???- example "Example Code"
    This code freezes every entity in the room for 1 second.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddFreeze(EntityRef(player), 30)
    end
    ```

___
### Add·Health () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddHealth ( float HitPoints ) {: .copyable aria-label='Functions' }
为实体恢复生命值.
___
### Add·Midas·Freeze () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void AddMidasFreeze ( [EntityRef](EntityRef.md) Source, int Duration ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddMidasFreeze ( [EntityRef](EntityRef.md) Source, int Duration, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }
将实体变为黄金雕像（无法移动、无法攻击，被击杀时掉落硬币）

???- info "持续时间说明"
    最大持续时间为 5 秒

???+ bug
    应用到实体上的金色会在传入函数的整个持续时间内保留，即使冻结效果最多只持续 5 秒.

???- example "Example Code"
    This code turns every entity in the room into gold for 1 second.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddMidasFreeze(EntityRef(player), 30)
    end
    ```
___
### Add·Poison () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void AddPoison ( [EntityRef](EntityRef.md) Source, int Duration, float Damage ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddPoison ( [EntityRef](EntityRef.md) Source, int Duration, float Damage, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }

为实体添加中毒效果.

???- info "持续时间说明"
    持续时间至少需要 3 帧才能造成伤害。每次连续的伤害间隔为 20 帧.

    ```
    - 2 次伤害 = 23 帧
    - 3 次伤害 = 43 帧
    - 4 次伤害 = 63 帧
    ...
    ```

???+ bug
    持续时间存在上限。对于玩家实体（EntityPlayer），仅持续 1 个伤害间隔；对于普通实体，最多持续 6 个伤害间隔.

???- example "Example Code"
    This code applies a poison effect to every entity in the room for 1 second.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddPoison(EntityRef(player), 30, 1)
    end
    ```
___
### Add·Shrink () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void AddShrink ( [EntityRef](EntityRef.md) Source, int Duration ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddShrink ( [EntityRef](EntityRef.md) Source, int Duration, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }

为实体添加缩小效果.

???- info "持续时间说明"
    最大持续时间为 5 秒

???- example "Example Code"
    This code shrinks every entity in the room for 1 second.

    ```lua
    local player = Isaac.GetPlayer()
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddShrink(EntityRef(player), 30)
    end
    ```
___
### Add·Slowing () {: aria-label='Functions' }
[ ](#){: .abrep .tooltip .badge }
#### void AddSlowing ( [EntityRef](EntityRef.md) Source, int Duration, float SlowValue, [Color](Color.md) SlowColor ) {: .copyable aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void AddSlowing ( [EntityRef](EntityRef.md) Source, int Duration, float SlowValue, [Color](Color.md) SlowColor, boolean IgnoreBosses ) {: .copyable aria-label='Functions' }
提高实体的摩擦力，从而有效减缓实体速度.

???- example "Example Code"
    This code slows every entity in the room for 1 second with 0.5 original speed and applies a red color to it.

    ```lua
    local player = Isaac.GetPlayer()
    local slowColor = Color(1, 0, 0, 1, 0, 0, 0)
    local entities = Isaac.GetRoomEntities()
    for i, entity in ipairs(entities) do
    	entity:AddSlowing(EntityRef(player), 30, 0.5, slowColor)
    end
    ```
___
### Add·Velocity () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AddVelocity ( [Vector](Vector.md) Velocity ) {: .copyable aria-label='Functions' }

为实体添加速度。可用于使实体向特定方向移动（例如碰撞后的结果）
___
### Blood·Explode () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void BloodExplode ( ) {: .copyable aria-label='Functions' }
使实体伴随碎块和血液爆炸.
___
### Can·Shut·Doors () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanShutDoors ( ) {: .copyable aria-label='Functions' }
判断敌人是否会保持门关闭状态。返回布尔值
___
### Clear·Entity·Flags () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ClearEntityFlags ( int Flags ) {: .copyable aria-label='Functions' }

从实体中移除所有指定的[实体标记](enums/EntityFlag.md).
___
### Collides·With·Grid () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CollidesWithGrid ( ) {: .copyable aria-label='Functions' }

若实体当前正与有效的网格实体（根据其`Entity.GridCollisionClass`属性）发生碰撞，则返回 true.
___
### Die () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Die ( ) {: .copyable aria-label='Functions' }

杀死实体并触发其死亡动画.
___
### Exists () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean Exists ( ) {: .copyable aria-label='Functions' }

检查实体是否仍在当前房间中生成.

主要用于解包 EntityPtr 时，对应的实体可能已在期间被杀死的情况.

___
### Get·Boss·ID () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetBossID ( ) {: .copyable aria-label='Functions' }
若实体是 Boss，返回其特定的 Boss ID；若不是 Boss，返回 0.

Boss ID 与实体类型（Type）**不同**，它在 entities2.xml 文件的 “bossID” 属性中单独定义。
对于精神错乱（Delirium），此函数返回其当前变形后的 Boss ID.
___
### Get·Color () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Color](Color.md) GetColor ( ) {: .copyable aria-label='Functions' }

返回与该实体关联的颜色对象（Color）.
___
### Get·Data () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### table GetData ( ) {: .copyable aria-label='Functions' }

返回一个包含与实体关联的模组相关数据的 Lua 表。初始时该表为空，模组存储在表中的任何值将保留到实体消失.

GetData is typically used by smaller mods as a quick way to store information about an entity without having to create a dedicated data structure.

???- example "Example Code"
    This code adds custom data to an entity or prints it in the console if it exists.

    ```lua
    function checkAndSetData(entity)
      local data = entity:GetData()
      if data.foo == nil then -- Keys of data should be strings
        data.foo = "bar" -- Values of data can be any data type
        print("Assigned an initial key of: foo --> bar")
      else
        print("Key foo already exists: " .. tostring(data.foo))
      end
    end
    ```

注意事项`GetData`:

1. 数据并非每个模组独有，类似于全局变量，可能被其他模组覆盖，且不利于代码调试.

2. 大多数实体离开房间时会消失，其数据也会被删除（玩家、随从和带有[`EntityFlag.FLAG_PERSISTENT`](./enums/EntityFlag.md)标记的实体除外）.

3. 即使实体离开房间不消失，退出菜单或重启 / 结束 run 时，GetData 中的数据也会被删除，不适合存储需要持久化的状态.

MOD开发者应该考虑使用他们自己MOD的本地数据结构，以避免冲突和之前提出的任何其他问题。此类数据结构的索引通常是指针哈希，借助 `GetPtrHash` 函数，可获取任意实体对应的指针哈希.
___
### Get·Drop·RNG () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [RNG](RNG.md) GetDropRNG ( ) {: .copyable aria-label='Functions' }

返回实体的指定随机数生成器（RNG）对象，用于确定实体死亡时掉落的物品.
___
### Get·Entity·Flags () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetEntityFlags ( ) {: .copyable aria-label='Functions' }

获取实体的[实体标记](enums/EntityFlag.md)返回值为一个用作位掩码的数字.

???- example "Example Code"
    This code prints something in the console, if the entity has a specific [EntityFlags](enums/EntityFlag.md).

    ```lua
    if entity:GetEntityFlags() & EntityFlag.FLAG_CONFUSION == EntityFlag.FLAG_CONFUSION then
        print("This entity is confused!")
    end
    ```
___
### Get·Last·Child () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) GetLastChild ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }

返回该实体的最后一个子实体。对于某些分段敌人，可用于直接获取最底部的 “尾部” 实体.

???+ note "返回行为"
    若未找到子实体，返回 `nil`.
___
### Get·Last·Parent () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) GetLastParent ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }

返回该实体的最后一个父实体。对于某些分段敌人，可用于直接获取最顶部的 “头部” 实体.

???+ note "返回行为"
    若未找到父实体，返回`nil`.
___
### Get·Sprite () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Sprite](Sprite.md) GetSprite ( ) {: .copyable aria-label='Functions' }

返回实体的精灵对象（Sprite）.
___
### Has·Common·Parent·With·Entity () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasCommonParentWithEntity ( [Entity](Entity.md) Other ) {: .copyable aria-label='Functions' }

判断该实体与另一个实体是否有共同的父实体，返回布尔值
___
### Has·Entity·Flags () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasEntityFlags ( int Flags ) {: .copyable aria-label='Functions' }

若实体具有所有指定的[实体标记](enums/EntityFlag.md)，返回 true.

???- example "Example Code"
    This code prints something in the console, if the entity has a specific [EntityFlags](enums/EntityFlag.md).

    ```lua
    if entity:HasEntityFlags(EntityFlag.FLAG_CONFUSION) then
        print("This entity is confused!")
    end
    ```
___
### Has·Full·Health () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasFullHealth ( ) {: .copyable aria-label='Functions' }

判断实体是否处于满血状态，返回布尔值
___
### Has·Mortal·Damage () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean HasMortalDamage ( ) {: .copyable aria-label='Functions' }

判断实体是否受到了致命伤害，返回布尔值

???- note "说明"
    游戏会将受到的伤害添加到伤害缓冲区，并在下一帧应用。若缓冲伤害足以杀死实体，此函数返回 true。调用 TakeDamage () 后，该函数会额外更新.
___
### Is·Active·Enemy () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsActiveEnemy ( boolean includeDead ) {: .copyable aria-label='Functions' }
如果实体是非背景 NPC（例如，除了火焰和店主之外的所有敌人），则返回 true
___
### Is·Boss () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsBoss ( ) {: .copyable aria-label='Functions' }
如果实体是首领（显示生命值条），则返回 true
___
### Is·Dead () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsDead ( ) {: .copyable aria-label='Functions' }

检查实体是否已死亡
___
### Is·Enemy () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsEnemy ( ) {: .copyable aria-label='Functions' }

如果实体是不受玩家控制的 NPC，则返回 true
___
### Is·Flying () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsFlying ( ) {: .copyable aria-label='Functions' }

___
### Is·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsFrame ( int Frame, int Offset ) {: .copyable aria-label='Functions' }
每 X 帧返回 true
___
### Is·Invincible () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsInvincible ( ) {: .copyable aria-label='Functions' }
检查实体是否无敌
___
### Is·Visible () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsVisible ( ) {: .copyable aria-label='Functions' }
检查实体是否可见
___
### Is·Vulnerable·Enemy () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsVulnerableEnemy ( ) {: .copyable aria-label='Functions' }

如果实体是可以被伤害的敌人，则返回 true
___
### Kill () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Kill ( ) {: .copyable aria-label='Functions' }
杀死实体并产生血溅或碎块效果.
___
### Kill·With·Source () {: aria-label='Functions' }
[ ](#){: .repplus .tooltip .badge }
#### void KillWithSource ( [EntityRef](EntityRef.md) Source ) {: .copyable aria-label='Functions' }
___
### Multiply·Friction () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void MultiplyFriction ( float Value ) {: .copyable aria-label='Functions' }
将实体的摩擦力乘以指定的值
___
### Post·Render () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void PostRender ( ) {: .copyable aria-label='Functions' }
将实体的摩擦力乘以指定的值
___
### Remove () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Remove ( ) {: .copyable aria-label='Functions' }
Remove the entity from the game instantly, without doing any additional effects/animations.
___
### Remove·Status·Effects () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void RemoveStatusEffects ( ) {: .copyable aria-label='Functions' }

立即从游戏中移除实体，不执行任何额外的效果或动画.
___
### Render () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Render ( [Vector](Vector.md) Offset ) {: .copyable aria-label='Functions' }
在当前实体位置加上偏移量的位置渲染实体的当前精灵.
___
### Render·Shadow·Layer () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean RenderShadowLayer ( [Vector](Vector.md) Offset ) {: .copyable aria-label='Functions' }

再次渲染阴影 / 阴影层.
___
### Set·Color () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetColor ( [Color](Color.md) Color, int Duration, int Priority, boolean Fadeout, boolean Share ) {: .copyable aria-label='Functions' }

为实体设置颜色掩码。这可用于将精灵染成不同的颜色.

``Share`` 布尔值将颜色应用于子实体.

???- example "Example Code"
    This code changes the color of the sprite to a fully white sprite for 15 frames.

    ```lua
    entity:SetColor(Color(1, 1, 1, 1, 255, 255, 255), 15, 1, false, false)
    ```

___
### Set·Size () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetSize ( float Size, [Vector](Vector.md) SizeMulti, int NumGridCollisionPoints ) {: .copyable aria-label='Functions' }

设置实体的大小(碰撞大小).
___
### Set·Sprite·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetSpriteFrame ( string AnimationName, int FrameNum ) {: .copyable aria-label='Functions' }
设置实体精灵的指定动画的帧
___
### Set·Sprite·Overlay·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetSpriteOverlayFrame ( string AnimationName, int FrameNum ) {: .copyable aria-label='Functions' }
设置实体精灵覆盖层的指定动画的帧号
___
### Take·Damage () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean TakeDamage ( float Damage, [DamageFlag](enums/DamageFlag.md) Flags, [EntityRef](EntityRef.md) Source, int DamageCountdown ) {: .copyable aria-label='Functions' }


???- note "注意"
    游戏会将受到的伤害添加到伤害缓冲区中，该缓冲区会在下一帧应用。因此，调用 TakeDamage() 后，实体的生命值不会立即减少，而是在下一帧更新.
___
### To·Bomb () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityBomb](EntityBomb.md) ToBomb ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将[Entity](Entity.md) 对象转换为 [EntityBomb](EntityBomb.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.
___
### To·Effect () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityEffect](EntityEffect.md) ToEffect ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将 [Entity](Entity.md) 对象转换为 [EntityEffect](EntityEffect.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### To·Familiar () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityFamiliar](EntityFamiliar.md) ToFamiliar ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将 [Entity](Entity.md) 对象转换为 [EntityFamiliar](EntityFamiliar.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### To·Knife () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityKnife](EntityKnife.md) ToKnife ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将 [Entity](Entity.md) 对象转换为 [EntityKnife](EntityKnife.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### To·Laser () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityLaser](EntityLaser.md) ToLaser ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将 [Entity](Entity.md) 对象转换为 [EntityLaser](EntityLaser.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### To·NPC () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityNPC](EntityNPC.md) ToNPC ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将 [Entity](Entity.md) 对象转换为 [EntityNPC](EntityNPC.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### To·Pickup () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityPickup](EntityPickup.md) ToPickup ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将 [Entity](Entity.md) 对象转换为 [EntityPickup](EntityPickup.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### To·Player () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityPlayer](EntityPlayer.md) ToPlayer ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将 [Entity](Entity.md) 对象转换为 [EntityPlayer](EntityPlayer.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### To·Projectile () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityProjectile](EntityProjectile.md) ToProjectile ( ) {: .copyable aria-label='Functions' data-altreturn='nil' }
用于将 [Entity](Entity.md) 对象转换为 [EntityProjectile](EntityProjectile.md) 对象.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### To·Tear () {: aria-label='Functions' data-altreturn='nil' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityTear](EntityTear.md) ToTear ( ) {: .copyable aria-label='Functions' }
用于将 [Entity](Entity.md) 对象转换为 [EntityTear](EntityTear.md) object.

???+ note "返回行为"
    如果转换不成功，此函数返回 `nil`.

___
### Update () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void Update ( ) {: .copyable aria-label='Functions' }

为实体运行一帧的更新后逻辑，这将触发关联的回调。模组通常不需要调用此函数，因为在一帧内多次运行更新后逻辑可能会导致错误.

___
## Variables
### Child {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) Child {: .copyable aria-label='Variables' }

实体的子实体

???- warning "Warning"
    “Sisters visi” Boss 的对应实体互为子实体，但它们都没有父实体（Parent.
___
### Collision·Damage {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float CollisionDamage  {: .copyable aria-label='Variables' }

实体碰撞造成的伤害
___
### Color {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Color](Color.md) Color  {: .copyable aria-label='Variables' }

实体的颜色
___
### Depth·Offset {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float DepthOffset  {: .copyable aria-label='Variables' }

获取 / 设置实体的深度偏移量。该值会添加到实体的 Y 坐标中，用于确定每个实体的渲染顺序。所有实体的默认值为 0.

???- example "Example Code"
    This code explains how this variable works.

    ```lua
    entity1.Position.Y -- => 50
    entity2.Position.Y -- => 45
    -- Entity1 is rendered in front of Entity2

    entity1.DepthOffset = -10
    -- new Entity1 renderYPosition => 40
    -- Entity2 is rendered in front of Entity1
    ```

___
### Drop·Seed {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const int DropSeed  {: .copyable aria-label='Variables' }

获取掉落随机数生成器（RNG）的种子
___
### Entity·Collision·Class {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityCollisionClass](enums/EntityCollisionClass.md) EntityCollisionClass {: .copyable aria-label='Variables' }

实体的碰撞类别
___
### FlipX {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean FlipX  {: .copyable aria-label='Variables' }

实体是否沿 X 轴翻转
___
### Frame·Count {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const int FrameCount  {: .copyable aria-label='Variables' }

___
### Friction {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Friction  {: .copyable aria-label='Variables' }

从实体配置中加载的摩擦力
___
### Grid·Collision·Class {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityGridCollisionClass](enums/EntityGridCollisionClass.md) GridCollisionClass {: .copyable aria-label='Variables' }

实体与网格的碰撞类别

???- note "注意"
    玩家实体（EntityPlayers）只能使用 GRIDCOLL_NONE、GRIDCOLL_WALLS 和 GRIDCOLL_GROUND，其他枚举值的行为与 GRIDCOLL_WALLS 相同.
___
### Hit·Points {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float HitPoints  {: .copyable aria-label='Variables' }


实体的当前生命值
???- note "注意"
    实体受到伤害时，生命值不会立即减少，而是在下一帧更新.
___
### Index {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const int Index  {: .copyable aria-label='Variables' }

___
### Init·Seed {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const int InitSeed  {: .copyable aria-label='Variables' }

实体的初始种子
___
### Mass {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Mass  {: .copyable aria-label='Variables' }

实体的质量

???+ note "注意"
    静止敌人的质量为 100（某些静止非敌人实体如老虎机除外）.
___
### Max·Hit·Points {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float MaxHitPoints  {: .copyable aria-label='Variables' }

实体的最大生命值
___
### Parent {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) Parent  {: .copyable aria-label='Variables' data-altreturn='nil' }

实体的父实体。对于大多数实体，该字段为 nil。在多段实体中，该字段用于指向 “主” 实体（如头部）.

___
### Position {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) Position  {: .copyable aria-label='Variables' }

___
### Position·Offset {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) PositionOffset  {: .copyable aria-label='Variables' }

实体的位置
___
### Render·ZOffset {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int RenderZOffset  {: .copyable aria-label='Variables' }

实体的位置偏移量

???+ bug "Bugs"
    该变量似乎没有任何有用的作用。请改用 DepthOffset.
___
### Size {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Size  {: .copyable aria-label='Variables' }
实体 hitbox（阴影/碰撞箱） 的大小.

___
### Size·Multi {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) SizeMulti  {: .copyable aria-label='Variables' }

以撒中的“Hitbox”并不是盒状，而是胶囊形（或圆圈）。这决定了圆的形状，X值越大，圆越宽，Y值越高，圆越高，反之亦然。

___
### Sorting·Layer {: aria-label='Variables' }
[ ](#){: .reporplus .tooltip .badge }
#### [SortingLayer](enums/SortingLayer.md) SortingLayer  {: .copyable aria-label='Variables' }

Determines when the entity should render over other entities.

___
### Spawner·Entity {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) SpawnerEntity  {: .copyable aria-label='Variables' data-altreturn='nil' }

生成该实体的实体
___
### Spawner·Type {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityType](enums/EntityType.md) SpawnerType  {: .copyable aria-label='Variables' }

生成该实体的实体类型
___
### Spawner·Variant {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int SpawnerVariant  {: .copyable aria-label='Variables' }

生成该实体的实体变种
___
### Spawn·Grid·Index {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const int SpawnGridIndex  {: .copyable aria-label='Variables' }

房间生成时实体生成所在的网格索引.
重新随机生成的物品基座或房间初始生成后再生成的实体，该值为 - 1

___
### Splat·Color {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Color](Color.md) SplatColor  {: .copyable aria-label='Variables' }

实体死亡时碎块的颜色.
该属性的颜色为只读，若要更改，需用新的颜色对象（Color）替换.

___
### Sprite·Offset {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) SpriteOffset  {: .copyable aria-label='Variables' }

精灵的偏移量
___
### Sprite·Rotation {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float SpriteRotation  {: .copyable aria-label='Variables' }

精灵的旋转角度
___
### Sprite·Scale {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) SpriteScale  {: .copyable aria-label='Variables' }
获取 / 设置敌人精灵的缩放比例，也可用于缩放实体的阴影。它还作为玩家属性，可在 MC_EVALUATE_CACHE 回调中使用 CacheFlag.CACHE_SIZE 标记更改，**等同于大小（Size）属性**

大多数 “变大” 效果的物品（如魔法蘑菇、“变大” 药丸等）通过将 SpriteScale 乘以 1.2500623464584（推测为 1.25，存在浮点误差，建议使用 1.25 以保证兼容性）来实现效果；大多数 “变小” 效果的物品（如迷你蘑菇、Binky、“变小” 药丸等）通过乘以 0.79996013641357（推测为 0.8）来实现；冥王星（Pluto）使用自己的乘数 0.5

___
### Sub·Type {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int SubType  {: .copyable aria-label='Variables' }

实体的子类型
___
### Target {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) Target  {: .copyable aria-label='Variables' }

实体的目标实体
___
### Target·Position {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) TargetPosition  {: .copyable aria-label='Variables' }

实体的目标位置
___
### Type {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [EntityType](enums/EntityType.md) Type  {: .copyable aria-label='Variables' }

实体的类型
___
### Variant {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int Variant  {: .copyable aria-label='Variables' }

实体的变种
___
### Velocity {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) Velocity  {: .copyable aria-label='Variables' }

实体的速度
___
### Visible {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean Visible  {: .copyable aria-label='Variables' }

___
