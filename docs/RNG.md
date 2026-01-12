---
tags:
  - Globals
  - Class
---
# Class "RNG"

???+ info
    RNG 类提供了一种生成带种子的随机数的机制。该类被游戏本体和模组广泛使用。

    你可以通过构造函数或以下函数获取该类的实例：

    * [Entity.GetDropRNG()](Entity.md#getdroprng)
    * [EntityPlayer.GetCardRNG()](EntityPlayer.md#getcardrng)
    * [EntityPlayer.GetCollectibleRNG()](EntityPlayer.md#getcollectiblerng)
    * [EntityPlayer.GetPillRNG()](EntityPlayer.md#getpillrng)
    * [EntityPlayer.GetTrinketRNG()](EntityPlayer.md#gettrinketrng)
    * [GridEntity.GetRNG()](GridEntity.md#getrng)
    * [GridEntityPreasurePlate.GreedModeRNG](GridEntityPressurePlate.md#greedmoderng)
    * [Level.GetDevilAngelRoomRNG()](Level.md#getdevilangelroomrng)

    ???+ example "示例代码"
        ```lua
        local myRNG = RNG()
        ```

## 构造函数
### RNG () {: aria-label='Constructors' }
[ ](#){: .alldlc .tooltip .badge }
#### [RNG](RNG.md) RNG ( ) {: .copyable aria-label='Constructors' }

新建的 RNG 对象总是以种子 2853650767 初始化。因此，在调用构造函数后，你必须将新 RNG 对象的种子设置为你想要的初始种子。在某些情况下，这个种子可以是 1 到 4294967295 之间的任意新随机数。此时可用 `Random` 全局函数获取初始种子（但要确保不能为 0，否则会导致游戏崩溃）。然而，在大多数情况下，使用完全随机的种子会导致你的模组出现 bug，因为以撒的所有行为都应当基于开局种子、关卡种子或房间种子等确定性种子。

设置种子时，推荐使用 shift index 35，这是大多数游戏内部函数采用的值。建议将该数字以 SHOUTING_SNAKE_CASE 常量形式记录，避免在程序中出现[魔数](https://en.wikipedia.org/wiki/Magic_number_(programming))。

???+ example "示例代码"
    ```lua
    -- 这是 Blade 在审查游戏内部函数后推荐的 ShiftIdx。
    -- 0 到 80（含）之间的任意值都可以正常工作。
    -- https://www.jstatsoft.org/article/view/v008i14/xorshift.pdf
    local RECOMMENDED_SHIFT_IDX = 35

    local game = Game()
    local seeds = game:GetSeeds()
    local startSeed = seeds:GetStartSeed()
    local rng = RNG()
    rng:SetSeed(startSeed, RECOMMENDED_SHIFT_IDX)
    local myRandomNumber = rng:RandomInt(4) -- 结果为 0、1、2 或 3。
    ```

___
## Functions

### Get·Seed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int GetSeed ( ) {: .copyable aria-label='Functions' }

返回当前 RNG 对象的种子。

___
### Next () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int Next ( ) {: .copyable aria-label='Functions' }

将 RNG 的种子“迭代”到伪随机序列中的下一个随机数。（内部使用的 PRNG 算法为 [Xorshift](https://en.wikipedia.org/wiki/Xorshift)。）

___
### Random·Float () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### float RandomFloat ( ) {: .copyable aria-label='Functions' }
返回一个 0 到 1 之间的数。包含下限 0，不包含上限 1。

注意：调用此方法会自动调用 `RNG.Next`，因此会改变 RNG 对象的状态，需谨慎使用。

???+ example "示例代码"
    ```lua
    -- 这是 Blade 推荐的 ShiftIdx。
    -- 0 到 80（含）之间的任意值都可以正常工作。
    -- https://www.jstatsoft.org/article/view/v008i14/xorshift.pdf
    local RECOMMENDED_SHIFT_IDX = 35
    local MY_ENTITY_CHANCE = 0.3 -- 30%

    function shouldEntityDoThing(entity)
      local rng = RNG()
      rng:SetSeed(entity.InitSeed, RECOMMENDED_SHIFT_IDX)
      local randomChance = myRNG:RandomFloat()
      return randomChance < MY_ENTITY_CHANCE
    end
    ```
___
### Random·Int () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### int RandomInt ( int Max ) {: .copyable aria-label='Functions' }
返回一个 0 到最大值之间的整数。包含下限 0，不包含上限 Max。

注意：调用此方法会自动调用 `RNG.Next`，因此会改变 RNG 对象的状态，需谨慎使用。

???+ example "示例代码"
    ```lua
    local RECOMMENDED_SHIFT_IDX = 35

    function getZeroOneTwoOrThree(seed)
      local rng = RNG()
      rng:SetSeed(seed, RECOMMENDED_SHIFT_IDX)
      return rng:RandomInt(4) -- 结果为 0、1、2 或 3。
    end
    ```
___
### Set·Seed () {: aria-label='Functions' }
[ ](#){: .alldlc .tooltip .badge }
#### void SetSeed ( int Seed, int ShiftIdx ) {: .copyable aria-label='Functions' }
设置指定 RNG 对象的种子。Seed 必须为正整数且**不能为 0**，否则会导致崩溃。ShiftIdx 必须在 0 到 80（含）之间，否则也会导致崩溃。

Shift index 对照表见：https://gist.github.com/bladecoding/17b341ed08ff94d2deb704ebda8ffc5f

???+ bug "Bug"
    如果 RNG 对象的种子被设置为 0，调用 `Next()`、`RandomInt()` 等方法时会导致游戏崩溃。


???+ example "示例代码"
    ```lua
    local myRNG = RNG()
    myRNG:SetSeed(Random(), 1)
    ```

___
