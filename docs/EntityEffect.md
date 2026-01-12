---
tags:
  - Class
---
# Class "EntityEffect"

???+ info
    You can get this class by using the following function:

    * [Entity.ToEffect()](Entity.md#toeffect)
    * [EntityNPC.MakeSplat()](EntityNPC.md#makesplat)

    ???+ example "Example Code"
        `local entity = Isaac.GetRoomEntities()[1]:ToEffect()`

## Class Diagram
--8<-- "docs/snippets/EntityClassDiagram.md"
## Functions
### Follow·Parent () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void FollowParent ( [Entity](Entity.md) Parent ) {: .copyable aria-label='Functions' }

___
### Is·Player·Creep () {: aria-label='Functions' }
[ ](#){: .static .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### static boolean IsPlayerCreep ( [EffectVariant](enums/EffectVariant.md) Variant ) {: .copyable aria-label='Functions' }

___
### Set·Damage·Source () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetDamageSource ( [EntityType](enums/EntityType.md) DamageSource ) {: .copyable aria-label='Functions' }

___
### Set·Radii () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetRadii ( float min, float max ) {: .copyable aria-label='Functions' }
用于冲击波（shockwaves）。
___
### Set·Timeout () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetTimeout ( int Timeout ) {: .copyable aria-label='Functions' }

___
## Variables
### Damage·Source {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int DamageSource  {: .copyable aria-label='Variables' }

___
### Falling·Acceleration {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float FallingAcceleration  {: .copyable aria-label='Variables' }

___
### Falling·Speed {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float FallingSpeed  {: .copyable aria-label='Variables' }

___
### Is·Following {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsFollowing  {: .copyable aria-label='Variables' }

___
### Life·Span {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int LifeSpan  {: .copyable aria-label='Variables' }

___
### m_Height {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float m_Height  {: .copyable aria-label='Variables' }
用于粒子的 .dy

___
### Max·Radius {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float MaxRadius  {: .copyable aria-label='Variables' }

___
### Min·Radius {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float MinRadius  {: .copyable aria-label='Variables' }
用于冲击波（shockwaves）。

___
### Parent·Offset {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) ParentOffset  {: .copyable aria-label='Variables' }
可能很快就会被淘汰，取而代之的是 m_SpriteOffset

___
### Rotation {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Rotation  {: .copyable aria-label='Variables' }

___
### Scale {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Scale  {: .copyable aria-label='Variables' }

___
### State {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int State  {: .copyable aria-label='Variables' }
状态变量，可在 Init() 中随意使用，初始化为 0

___
### Timeout {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int Timeout  {: .copyable aria-label='Variables' }

该值在每一帧都会递减，即使是自定义效果也是如此。自定义效果将此值初始化为 -1。

___
