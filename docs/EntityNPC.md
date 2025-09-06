---
tags:
  - Class
---
# Class "EntityNPC"

???+ info
    你可以通过以下函数获取此类：

    * [Entity.ToNPC()](Entity.md#tonpc)
    * [Game.SpawnEntityDesc()](Game.md#spawnentitydesc)

    ???+ example "Example Code"
        `local entity = Isaac.GetRoomEntities()[1]:ToNPC()`

## Class Diagram
--8<-- "docs/snippets/EntityClassDiagram.md"
## Functions
### Anim·Walk·Frame () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void AnimWalkFrame ( string HorizontalAnim, string VerticalAnim, float SpeedThreshold ) {: .copyable aria-label='Functions' }

___
### Calc·Target·Position () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) CalcTargetPosition ( float DistanceLimit ) {: .copyable aria-label='Functions' }

___
### Can·Be·Damaged·From·Velocity () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanBeDamagedFromVelocity ( [Vector](Vector.md) Velocity ) {: .copyable aria-label='Functions' }

___
### Can·Reroll () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanReroll ( ) {: .copyable aria-label='Functions' }

___
### Fire·Boss·Projectiles () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityProjectile](EntityProjectile.md) FireBossProjectiles ( int NumProjectiles, [Vector](Vector.md) TargetPos, float TrajectoryModifier, [ProjectileParams](ProjectileParams.md) Params ) {: .copyable aria-label='Functions' }
发射一系列弹幕，目标可以是玩家，方向会随机化，或者在瞄准玩家时稍微随机化。可以使用 FallingAccelModifier 使弹幕更快落地。返回最后生成的弹幕指针（例如，当 NumProjectiles=1 时很有用）。
___
### Fire·Projectiles () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void FireProjectiles ( [Vector](Vector.md) Pos, [Vector](Vector.md) Velocity, ProjectilesMode Mode, [ProjectileParams](ProjectileParams.md) Params ) {: .copyable aria-label='Functions' }

???- info "ProjectilesMode"
    该参数控制发射弹幕的模式：
    * 0 : 单发弹幕
    * 1 : 双发弹幕（使用 params.Spread）
    * 2 : 三发弹幕（使用 params.Spread）
    * 3 : 三发弹幕（使用 params.Spread，分布更广？）
    * 4 : 四发弹幕（使用 params.Spread）
    * 5 : 五发弹幕（使用 params.Spread）
    * 6 : 四发弹幕（使用 velocity.x 作为速度，呈 + 形状）
    * 7 : 四发弹幕（使用 velocity.x 作为速度，呈 x 形状）
    * 8 : 八发弹幕（使用 velocity.x 作为速度，呈星形）
    * 9 : N 发弹幕（使用 velocity.x 作为速度，velocity.y = N，params.FireDirectionLimit 和 params.DotProductLimit 仅在弧形中发射）
___
### Get·Alive·Enemy·Count () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetAliveEnemyCount ( ) {: .copyable aria-label='Functions' }

用于将近战敌人重定向到任何敌人以供友方 NPC 使用。
___
### Get·Boss·Color·Idx () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetBossColorIdx ( ) {: .copyable aria-label='Functions' }


???- note "Notes"

    这将返回减少 1 的 boss color idx。要获取在 bosscolors.xml 中设置的实际颜色，请在结果上加 1。
___
### Get·Champion·Color·Idx () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [ChampionColorIdx](enums/ChampionColor.md) GetChampionColorIdx ( ) {: .copyable aria-label='Functions' }

返回 NPC 的精英颜色索引。如果 NPC 不是精英怪，则返回 -1。
___
### Get·Player·Target () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) GetPlayerTarget ( ) {: .copyable aria-label='Functions' }
如果没有修饰符（最好的朋友），这将返回玩家
___
### Is·Boss () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsBoss ( ) {: .copyable aria-label='Functions' }

___
### Is·Champion () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsChampion ( ) {: .copyable aria-label='Functions' }

___
### Kill·Unique () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void KillUnique ( ) {: .copyable aria-label='Functions' }
对于具有独特死亡动画的实体，例如 Flush! 与粪便敌人。
___
### Make·Champion () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void MakeChampion ( int Seed, ChampionColor ChampionColorIdx = -1, boolean Init = false ) {: .copyable aria-label='Functions' }
强制非精英怪成为精英怪，重置生命值为最大生命值。

**ChampionColorIdx**: 要将此敌人变为的精英类型（-1 将导致随机精英类型）

**Init**: 在初始化敌人时调用时设置为 true，否则为 false
___
### Make·Splat () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityEffect](EntityEffect.md) MakeSplat ( float Size ) {: .copyable aria-label='Functions' }

___
### Morph () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean Morph ( [EntityType](enums/EntityType.md) type, int Variant, int SubType, int ChampionColorIdx ) {: .copyable aria-label='Functions' }

修改当前实体为另一个实体。可以使用 [ChampionColorIdx](https://bindingofisaacrebirth.gamepedia.com/Monsters#Champions) 将实体变为精英怪。使用 `:::lua -1` 以不添加精英变体。

精英变体索引的列表可以在这里找到 : [ChampionColorIdx](https://bindingofisaacrebirth.gamepedia.com/Monsters#Champions)

???+ bug

    这个函数无法将精英 NPC 转换为普通 NPC！为此，请使用以下代码：

    ```lua
    local previousNPC = entity:ToNPC()
    -- spawn the same entity at the same location as the old one
    Isaac.Spawn(previousNPC.Type, previousNPC.Variant, previousNPC.SubType, previousNPC.Position, previousNPC.Velocity, previousNPC.Parent)
    -- remove old entity
    previousNPC:Remove()
    ```

???- example "Example Code"

    This code turns an entity into a gaper.

    ```lua
    entity:ToNPC():Morph(EntityType.ENTITY_GAPER, 0, 0, -1)
    ```
___
### Play·Sound () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void PlaySound ( [SoundEffect](enums/SoundEffect.md) ID, float Volume, int FrameDelay, boolean Loop, float Pitch ) {: .copyable aria-label='Functions' }

___
### Query·NPCs·Group () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityList](CppContainer_EntityList.md) QueryNPCsGroup ( int GroupIdx ) {: .copyable aria-label='Functions' }

___
### Query·NPCs·Spawner·Type () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityList](CppContainer_EntityList.md) QueryNPCsSpawnerType ( [EntityType](enums/EntityType.md) SpawnerType, [EntityType](enums/EntityType.md) Type, boolean OnlyEnemies ) {: .copyable aria-label='Functions' }

___
### Query·NPCs·Type () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### [EntityList](CppContainer_EntityList.md) QueryNPCsType ( [EntityType](enums/EntityType.md) Type, int Variant ) {: .copyable aria-label='Functions' }

___
### Reset·Path·Finder·Target () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void ResetPathFinderTarget ( ) {: .copyable aria-label='Functions' }

___
### Throw·Spider () {: aria-label='Functions' }
[ ](#){: .static .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### static const [EntityNPC](EntityNPC.md) ThrowSpider ( [Vector](Vector.md) Position, [Entity](Entity.md) Spawner, [Vector](Vector.md) TargetPos, boolean Big, float YOffset ) {: .copyable aria-label='Functions' }

___
## Variables
### Can·Shut·Doors {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean CanShutDoors  {: .copyable aria-label='Variables' }

___
### Child·NPC {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [EntityNPC](EntityNPC.md) ChildNPC  {: .copyable aria-label='Variables' data-altreturn='nil' }

___
### Entity·Ref {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) EntityRef {: .copyable aria-label='Variables' }

___
### Group·Idx {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int GroupIdx  {: .copyable aria-label='Variables' }
Used to identify multichunks groups.
___
### I1 {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int I1  {: .copyable aria-label='Variables' }

通常用于 AI 特定操作的通用用法 int。每个实体的效果和用法是手动定义的。对于某些实体，它也可能根本无法使用。

**Example**: 脆皮虫进入第二阶段时将 I2 设置为 1。
___
### I2 {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int I2  {: .copyable aria-label='Variables' }

通常用于 AI 特定操作的通用用法 int。每个实体的效果和用法是手动定义的。对于某些实体，它也可能根本无法使用。

**Example**: 脆皮虫进入第二阶段时将 I2 设置为 1。
___
### Parent·NPC {: aria-label='Variables' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [EntityNPC](EntityNPC.md) ParentNPC  {: .copyable aria-label='Variables' data-altreturn='nil' }

父实体，用于像 Larry Jr. 这样的多实体 NPC。
___
### Pathfinder {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [PathFinder](PathFinder.md) Pathfinder  {: .copyable aria-label='Variables' }

___
### Projectile·Cooldown {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int ProjectileCooldown  {: .copyable aria-label='Variables' }

当 projectileCooldown 达到 0 时，弹幕可以再次发射
___
### Projectile·Delay {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int ProjectileDelay  {: .copyable aria-label='Variables' }
&gt;0: projectile will be fired in n frames
___
### Scale {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Scale  {: .copyable aria-label='Variables' }

___
### State {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [NpcState](enums/NpcState.md) State  {: .copyable aria-label='Variables' }

___
### State·Frame {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int StateFrame  {: .copyable aria-label='Variables' }

___
### V1 {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) V1  {: .copyable aria-label='Variables' }

通常用于 AI 特定操作的通用用法 Vector。初始化为 Vector(0,0)。每个实体的效果和用法是手动定义的。对于某些实体，它也可能根本无法使用。
___
### V2 {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) V2  {: .copyable aria-label='Variables' }

通常用于 AI 特定操作的通用用法 Vector。初始化为 Vector(0,0)。每个实体的效果和用法是手动定义的。对于某些实体，它也可能根本无法使用。
___
