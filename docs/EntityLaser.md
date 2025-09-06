---
tags:
  - Class
---
# Class "EntityLaser"

???+ info
    You can get this class by using the following function:

    * [Entity.ToLaser()](Entity.md#tolaser)
    * [EntityPlayer.FireBrimstone()](EntityPlayer.md#firebrimstone)
    * [EntityPlayer.FireDelayedBrimstone()](EntityPlayer.md#firedelayedbrimstone)
    * [EntityPlayer.FireTechLaser()](EntityPlayer.md#firetechlaser)
    * [EntityPlayer.FireTechXLaser()](EntityPlayer.md#firetechxlaser)

    ???+ example "Example Code"
        `local brimstoneEntity = Isaac.GetPlayer():FireBrimstone(Vector(1, 0))`

## Class Diagram
--8<-- "docs/snippets/EntityClassDiagram.md"
## Functions
### Add·Tear·Flags () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void AddTearFlags ( [TearFlags](enums/TearFlags.md) Flags ) {: .copyable aria-label='Functions' }

___
### Calculate·End·Point () {: aria-label='Functions' }
[ ](#){: .static .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### static [Vector](Vector.md) CalculateEndPoint ( [Vector](Vector.md) Start, [Vector](Vector.md) Dir, [Vector](Vector.md) PositionOffset, [Entity](Entity.md) Parent, float Margin ) {: .copyable aria-label='Functions' }

___
### Clear·Tear·Flags () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### void ClearTearFlags ( [TearFlags](enums/TearFlags.md) Flags ) {: .copyable aria-label='Functions' }

___
### Get·End·Point () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [Vector](Vector.md) GetEndPoint ( ) {: .copyable aria-label='Functions' }

___
### Get·Non·Optimized·Samples () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [VectorList](CppContainer_Vector_VectorList.md) GetNonOptimizedSamples ( ) {: .copyable aria-label='Functions' }
返回一个向量表（VectorList）用于表达激光的路径。通常会返回沿激光路径均匀分布的51个点，相对于[`GetSamples()`](#getsamples)只返回表示激光路径所需的最少点。

???+ example "Example Usage"
    ```lua
    local samplePoints = laser:GetNonOptimizedSamples()

    for i=0, #samplePoints-1 do
        local pos = samplePoints:Get(i)
        ...
    end
    ```

___
### Get·Render·Z () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetRenderZ ( ) {: .copyable aria-label='Functions' }

___
### Get·Samples () {: aria-label='Functions' }
[ ](#){: .const .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### const [VectorList](CppContainer_Vector_VectorList.md) GetSamples ( ) {: .copyable aria-label='Functions' }

返回一个向量表（VectorList）表示激光的路径。与 [`GetNonOptimizedSamples()`](#getnonoptimizedsamples) 不同，此函数返回尽可能少的点，同时仍然正确表示激光的路径。

例如，对于完全直的激光，[`GetNonOptimizedSamples()`](#getnonoptimizedsamples) 将始终返回 51 个点，但此函数仅返回 2 个。

???+ example "Example Usage"
    ```lua
    local samplePoints = laser:GetSamples()

    for i=0, #samplePoints-1 do
        local pos = samplePoints:Get(i)
        ...
    end
    ```

___
### Has·Tear·Flags () {: aria-label='Functions' }
[ ](#){: .reporplus .tooltip .badge }
#### boolean HasTearFlags ( [TearFlags](enums/TearFlags.md) Flags ) {: .copyable aria-label='Functions' }

___
### Is·Circle·Laser () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsCircleLaser ( ) {: .copyable aria-label='Functions' }

???- note "Note"
    此函数无法区分不同类型的圆形激光，但可以通过其子类型进行识别：

    * 0 - 线性激光（典型的激光，具有起点和终点）
    * 1 - 环形鲁多维科（用于鲁多维科科技协同的受控激光环）
    * 2 - 环形投射物（科技X）
    * 3 - 环形跟随父物体（虚空之喉）
    * 4 - 无碰撞（无碰撞溅射，例如科技零）

___
### Is·Sample·Laser () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsSampleLaser ( ) {: .copyable aria-label='Functions' }

___
### Set·Active·Rotation () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetActiveRotation ( int Delay, float AngleDegrees, float RotationSpd, boolean TimeoutComplete ) {: .copyable aria-label='Functions' }

___
### Set·Black·Hp·Drop·Chance () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetBlackHpDropChance ( float Chance ) {: .copyable aria-label='Functions' }

___
### Set·Homing·Type () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetHomingType ( LaserHomingType Type ) {: .copyable aria-label='Functions' }

___
### Set·Max·Distance () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetMaxDistance ( float Distance ) {: .copyable aria-label='Functions' }

___
### Set·Multidimensional·Touched () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetMultidimensionalTouched ( boolean Value ) {: .copyable aria-label='Functions' }

___
### Set·One·Hit () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetOneHit ( boolean Value ) {: .copyable aria-label='Functions' }

___
### Set·Timeout () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetTimeout ( int Value ) {: .copyable aria-label='Functions' }

___
### Shoot·Angle () {: aria-label='Functions' }
[ ](#){: .static .tooltip .badge } [ ](#){: .alldlc .tooltip .badge }
#### static [EntityLaser](EntityLaser.md) ShootAngle ( int Variant, [Vector](Vector.md) SourcePos, float AngleDegrees, int Timeout, [Vector](Vector.md) PosOffset, [Entity](Entity.md) Source ) {: .copyable aria-label='Functions' }
简单化静态助手以简化激光的生成
___
## Variables
### Angle {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Angle  {: .copyable aria-label='Variables' }

___
### Angle·Degrees {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float AngleDegrees  {: .copyable aria-label='Variables' }

___
### Black·Hp·Drop·Chance {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float BlackHpDropChance  {: .copyable aria-label='Variables' }
For maw of void.
___
### Bounce·Laser {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Entity](Entity.md) BounceLaser  {: .copyable aria-label='Variables' data-altreturn='nil' }

___
### Curve·Strength {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float CurveStrength  {: .copyable aria-label='Variables' }
My Reflection.
___
### Disable·Follow·Parent {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean DisableFollowParent  {: .copyable aria-label='Variables' }
设置为其他激光的子项时使用，例如橡胶胶水的反弹。禁用 m_ParentOffset。
___
### End·Point {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) EndPoint  {: .copyable aria-label='Variables' }
将会保存终点，以便在外部访问时不需要重新计算。
___
### First·Update {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean FirstUpdate  {: .copyable aria-label='Variables' }

___
### Grid·Hit {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean GridHit  {: .copyable aria-label='Variables' }
返回 `true` 如果激光可以被网格实体阻挡，并且在该帧被阻挡。
___
### Homing·Laser {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### HomingLaser HomingLaser  {: .copyable aria-label='Variables' }

___
### Homing·Type {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### LaserHomingType HomingType  {: .copyable aria-label='Variables' }

___
### Is·Active·Rotating {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean IsActiveRotating  {: .copyable aria-label='Variables' }

___
### Laser·Length {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float LaserLength  {: .copyable aria-label='Variables' }

___
### Last·Angle·Degrees {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float LastAngleDegrees  {: .copyable aria-label='Variables' }

___
### Max·Distance {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float MaxDistance  {: .copyable aria-label='Variables' }
Used to trim brimstone for Azazel (0 - off)
___
### One·Hit {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean OneHit  {: .copyable aria-label='Variables' }
Laser hits only once.
___
### Parent·Offset {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [Vector](Vector.md) ParentOffset  {: .copyable aria-label='Variables' }

___
### Radius {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float Radius  {: .copyable aria-label='Variables' }

___
### Rotation·Degrees {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float RotationDegrees  {: .copyable aria-label='Variables' }

___
### Rotation·Delay {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int RotationDelay  {: .copyable aria-label='Variables' }

___
### Rotation·Spd {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float RotationSpd  {: .copyable aria-label='Variables' }

___
### Sample·Laser {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean SampleLaser  {: .copyable aria-label='Variables' }

___
### Shrink {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### boolean Shrink  {: .copyable aria-label='Variables' }

___
### Start·Angle·Degrees {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### float StartAngleDegrees  {: .copyable aria-label='Variables' }

一些激光在旋转时会有随机变化，因此它们需要记住起始点。
___
### Tear·Flags {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### [TearFlags](enums/TearFlags.md) TearFlags  {: .copyable aria-label='Variables' }
___
### Timeout {: aria-label='Variables' }
[ ](#){: .alldlc .tooltip .badge }
#### int Timeout  {: .copyable aria-label='Variables' }

___
