---
tags:
  - 常见问题
---

# MOD常见问题：Lua

## Lua里的冒号操作符是做什么的？ {: .subHeader}

在 Lua 中，你可以一两种方法调用模块函数（即附加在表上的函数）:

```lua
foo.bar()
foo:bar()
```

点号会以“正常”方式调用函数，而冒号会以一个特殊的语法糖方法调用函数——把模块当作函数的第一个参数。例如，以下两个函数调用是等价的：

```lua
foo.bar(foo, arg1, arg2)
foo:bar(arg1, arg2)
```

使用冒号的目的是为了方便输入较长的函数调用，但对于那些不熟悉 Lua 的人来说，这会带来一些混淆。此功能包含在 Lua 语言中，因为这么做很常见。（Lua 模块通常用于模拟 Java 风格的类。）

在 Lua 中，用冒号调用模块中的函数非常惯用，在编写自己的代码时应该遵循这个约定。此外，大多数 API 类方法都应该使用冒号进行调用。然而，也有例外；标记为“静态”或来自独立于对象的类（例如`Isaac`、`Input`、`Options`）的方法不会用冒号调用。

```lua
-- 正常情况，用`EntityPlayer`类说明。
local player = Isaac.GetPlayer()
player.AddCollectible(CollectibleType.COLLECTIBLE_SAD_ONION) -- 出错，因为该函数接受`EntityPlayer`类作为第一个参数。
player:AddCollectible(CollectibleType.COLLECTIBLE_SAD_ONION) -- 有效。

-- 特殊情况，用`Isaac`类说明。
Isaac.DebugString("foo") -- 有效。
Isaac:DebugString("foo") -- 出错，因为该函数不接受 `Isaac` 类作为第一个参数。

-- 另一个静态函数的特殊情况。
-- 假如我们有一个激光实体，它通过 `MC_POST_LASER_UPDATE` 回调传入。
-- 就像大多数类，应该用冒号。
laser.SetMaxDistance(50) -- 出错，因为该函数接受 `EntityLaser` 类作为第一个参数。
laser:SetMaxDistance(50) -- 有效。
-- 但是静态函数又不一样了：
laser.ShootAngle(...) -- 有效（因为`ShootAngle`是静态函数）。
laser:ShootAngle(...) -- 出错，因为该函数不接受 `EntityLaser` 类作为第一个参数。
-- 显然，你也可以不通过类的实例来调用一个静态方法。（这也是为什么他们是静态的）
EntityLaser.ShootAngle(...) -- 有效。
EntityLaser:ShootAngle(...) -- 出错，因为该函数不接受 `EntityLaser` 类作为第一个参数。
```

## `pairs` 和 `ipairs` 的区别是什么？ {: .subHeader}

- `pairs` 用于遍历以[映射](https://en.wikipedia.org/wiki/Associative_array)形式表示的表。换句话说，他包括一组键/值对。
- `ipairs` 用于遍历以[数据](https://en.wikipedia.org/wiki/Array_data_structure)形式表示的表。换句话说，他包括一组元素。

代码胜于言语：

```lua
local map = {
  foo = "bar",
  baz = 123,
}

for key, value in pairs(map) do
  print(key) -- 打印foo, baz
  print(value) -- 打印bar, 123
end
```

```lua
local array = {
  123,
  456,
  789,
}

for i, element in ipairs(array) do
  print(i) -- 打印1, 2, 3
  print(element) -- 打印123, 456, 789
end
```

由于Lua是[无类型](https://www.tutorialspoint.com/What-are-the-differences-between-untyped-and-dynamically-typed-programming-languages)语言，并且使用表来代表多个不同的数据结构，因此  `pairs` 和 `ipairs` 作为一个标志，告诉读者底层数据结构到底是什么。

## 如何防止角色随意发射泪弹？ {: .subHeader}

你可以在XML文件里将角色的 `canShoot` 属性设置为 `false` 。如果你想任意切换他们的射击能力，你可以使用 REPENTOGON 的 [`EntityPlayer.SetCanShot`](https://repentogon.com/EntityPlayer.html#setcanshoot) 函数，或者可以使用以下代码：

=== ":material-language-lua: Lua"
    ```lua
    --- Zamiel编写，im_tem发现的技巧
    -- @param player EntityPlayer
    -- @param enabled boolean
    -- @param modifyCostume boolean
    function setBlindfold(player, enabled, modifyCostume)
      local game = Game()
      local character = player:GetPlayerType()
      local challenge = Isaac.GetChallenge()

      if enabled then
        game.Challenge = Challenge.CHALLENGE_SOLAR_SYSTEM -- This challenge has a blindfold
        player:ChangePlayerType(character)
        game.Challenge = challenge

        -- 自动应用角色外观。
        if not modifyCostume then
          player:TryRemoveNullCostume(NullItemID.ID_BLINDFOLD)
        end
      else
        game.Challenge = Challenge.CHALLENGE_NULL
        player:ChangePlayerType(character)
        game.Challenge = challenge

        if modifyCostume then
          player:TryRemoveNullCostume(NullItemID.ID_BLINDFOLD)
        end
      end
    end
    ```

=== ":material-language-typescript: TypeScript"
   如果你在使用 [:material-language-typescript:IsaacScript](https://isaacscript.github.io/)，那你需要做的只是调用 `setBlindfold` 函数，就像：

    ```ts
    const player = Isaac.GetPlayer();
    setBlindfold(player, true);
    ```

## 如何将人物外观应用于我的角色？ {: .subHeader}

这被称为 “Null Costume”（空外观），它是通过 `EntityPlayer.AddNullCostume()` 方法来完成的。有关更多信息，请参阅 [Lytebringr 的第8个视频](https://www.youtube.com/watch?v=R1CdCyGL1DQ&list=PLMZJyHSWa_My5DDoTQcKCgs475xIpQHSF&index=9)。

以下是一个添加空外观的实体代码：

???- example "示例代码"
    以下是一个使用 MOD 添加空外观的示例：

    ```lua
    local mod = RegisterMod("My Mod", 1)
    local MY_NULL_COSTUME_ID = Isaac.GetCostumeIdByPath("gfx/characters/bar.anm2")

    -- For EntityType.ENTITY_PLAYER (1)
    local PlayerVariant = {
      PLAYER = 0,
      COOP_BABY = 1,
    }

    function mod:postPlayerInit(player)
      if player.Variant == PlayerVariant.PLAYER then
        player:AddNullCostume(MY_NULL_COSTUME_ID)
      end
    end

    mod:AddCallback(ModCallbacks.MC_POST_PLAYER_INIT, mod.postPlayerInit)
    ```

## 我该如何让一个跟班像波比兄弟那样跟随玩家？ {: .subHeader}

=== ":material-language-lua: Lua"
    ```lua
    function postFamiliarInitMyFamiliar(familiar)
      familiar:AddToFollowers()
    end

    function postFamiliarUpdateMyFamiliar(familiar)
      familiar:FollowParent()
    end
    ```

=== ":material-language-typescript: TypeScript"
    ```ts
    function postFamiliarInitMyFamiliar(familiar: EntityFamiliar) {
      familiar.AddToFollowers();
    }

    function postFamiliarUpdateMyFamiliar(familiar: EntityFamiliar) {
      familiar.FollowParent();
    }
    ```

## 我要怎么遍历 API 提供的列表对象？ {: .subHeader}

有时，API 中会为您提供列表对象，这些对象储存元素列表，但并不是表，如 [Level](../Level.md) 的 [GetRooms](../Level.md#getrooms) 函数。

下面是一个如何在 Lua 中遍历列表对象的示例：

=== ":material-language-lua: Lua"

    ```lua
    local game = Game()
    local level = game:GetLevel()
    local rooms = level:GetRooms()
    for i = 0, rooms.Size - 1 do
      local room = rooms:Get(i)
      -- 根据这个房间做些什么
    end
    ```

=== ":material-language-typescript: TypeScript"

    在 IsaacScript 中，可以以和 Lua 完全相同的方式实现代码。不过对于这种特定情况，可以简单地使用辅助函数直接迭代房间：

    ```ts
    for (const roomDescriptor of getRooms()) {
      // 根据这个房间做些什么
    }
    ```

## 如何使用 StageAPI 添加新头目？ {: .subHeader}

这是一段来自于 Xalum 的示例代码:

```lua
mod.StageAPIBosses = {
    StageAPI.AddBossData("The Baron", {
        Name = "The Baron",
        Portrait = "gfx/bosses/baron/portrait_baron.png",
        Bossname = "gfx/bosses/baron/name_baron.png",
        Rooms = StageAPI.RoomsList("BaronBossRooms", include("resources.luarooms.boss_baron"))
    }),

    StageAPI.AddBossData("High Amon", {
        Name = "High Amon",
        Portrait = "gfx/bosses/amon/portrait_amon.png",
        Bossname = "gfx/bosses/amon/name_amon.png",
        Rooms = StageAPI.RoomsList("AmonBossRooms", include("resources.luarooms.boss_amon"))
    }),
}

StageAPI.AddBossToBaseFloorPool({BossID = "The Baron", Weight = 1.5}, LevelStage.STAGE3_1, StageType.STAGETYPE_REPENTANCE)
StageAPI.AddBossToBaseFloorPool({BossID = "High Amon", AlwaysReplaceSubtype = 83, OnlyReplaceSubtype = 83}, LevelStage.STAGE2_1, StageType.STAGETYPE_REPENTANCE_B)
```