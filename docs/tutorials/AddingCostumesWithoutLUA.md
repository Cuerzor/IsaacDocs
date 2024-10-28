---
tags:
  - 教程
---
# [教程] 在不使用 LUA 的情况下为道具添加外观

#### :fontawesome-solid-code: 您可以在此处找到示例模组和代码：

[→ 下载本教程的示例模组 ←](../customData/costumes%20examplemod.zip)

## 默认的外观类型
### 定义道具

在为道具或饰品添加外观之前，我们需要先定义道具。可以在您的模组的 “content” 文件夹中创建一个空的 **“items.xml”** 文件来完成这个步骤。如果该文件夹尚不存在，请创建它。

然后在您的 items.xml 文件中添加所需数量的道具。它可能会像这样：
```xml
<items gfxroot="gfx/items/" version="1">
	<passive id="1" name="测试道具1" description="某个被动道具" gfx="testitem_1.png" />
    <active id="2" name="测试道具2" description="某个主动道具" gfx="testitem_2.png" />
	<passive id="999" name="测试道具999" description="某个高ID被动道具" gfx="testitem_999.png" />
	<familiar id="3" name="测试跟班3" description="某个跟班" gfx="testitem_3.png" />
	<trinket id="4" name="测试饰品4" description="某个饰品" gfx="testitem_4.png" />
</items>
```
请注意，我们还为每个道具定义了 ID。**这些 ID 用于将道具分配到它们的外观中！**

在 “content/items.xml” 文件中找到的 ID 仅由模组在本地使用。它们不会影响其他模组，也不会覆盖现有的原版道具！它们也不会定义它们在游戏内的ID！

### 定义外观

现在我们已经定义了一些道具，我们可以在 **“costumes2.xml”** 文件中定义我们的外观。

**重要提示：**外观 ID 和外观类型必须等于道具 ID 和道具类型！
```xml
<costumes anm2root="gfx/">
	<!-- 载入顺序是从上到下。不是基于 ID -->
    <costume id="1" anm2path="characters/test_costume_1.anm2" type="passive" />
    <costume id="2" anm2path="characters/test_costume_2.anm2" type="active" />
    <costume id="999" anm2path="characters/test_costume_999.anm2" type="passive" />
    <costume id="3" anm2path="characters/test_costume_3.anm2" type="familiar" />
    <costume id="4" anm2path="characters/test_costume_4.anm2" type="trinket" />
</costumes>
```

### 道具类型对外观的影响：

|道具类型|影响|
|--- |--- |
|**被动(passive)**|当拾取动画播放完毕时，外观会被添加。当道具被移除时，外观会被移除。|
|**主动(active)**|当道具被使用时，外观会被添加。当你改变房间时，外观会被移除。|
|**饰品(trinket)**|当拾取动画播放完毕时，外观会被添加。当饰品被移除时，外观会被移除。|
|**跟班(familiar)**|当拾取动画播放完毕时，外观会被添加。当道具被移除时，外观会被移除。|

#### 更多信息：

* 如果一个外观 ID 不能与一个道具 ID 相关联，游戏将崩溃。
* 类型为 **none** 的外观实际上与一个 Null 道具相关联。这些 Null 外观可以使用 Lua 添加。
* **套装**仍然必须使用 Null 外观方法（基于 Lua）添加。

* * *

## 添加Null外观

Null 外观是没有实际道具附加的外观。因此，它们可以用于添加临时外观，例如套装。

以下代码以两种不同的方式向玩家添加 Null 外观。选择适合你需要的方式。

### :fontawesome-solid-code: costumes2.xml

在 “costumes2.xml” 文件中，通过将类型设置为 “none” 来定义一个 Null 外观。不要设置 ID！

```xml
<costumes anm2root="gfx/">
    <costume anm2path="characters/some_null_costume.anm2" type="none" />
</costumes>
```

### :fontawesome-solid-code: main.lua

获取 Null 外观的自动生成的 ID，然后将其应用于玩家。

```lua
-- 获取内部外观 ID
NullItemID.ID_SOME_NULL_COSTUME = Isaac.GetCostumeIdByPath("gfx/characters/some_null_costume.anm2")

-- 使用 "AddNullCostume" 添加一个 Null 外观（永久，直到其被移除或重新开始一局游戏）
function mod:myFunction1(player)
    print("添加 Null 外观")
    if(somethingHappend) then
        player:AddNullCostume (NullItemID.ID_SOME_NULL_COSTUME)
    end
    -- 移除 Null 外观
    if(somethingDifferentHappend) then
        player:TryRemoveNullCostume(NullItemID.ID_SOME_NULL_COSTUME)
    end
end
mod:AddCallback(ModCallbacks.MC_POST_PLAYER_UPDATE, mod.myFunction1, 0)

-- 使用 "NullEffects" 添加一个 Nullcostume（在当前房间中持续存在，然后被移除）
function mod:myFunction2(player)
    if not player:GetEffects():HasNullEffect(NullItemID.ID_SOME_NULL_COSTUME) then
        print("添加 Null 外观") --每次更换房间时都会触发
        player:GetEffects():AddNullEffect(NullItemID.ID_SOME_NULL_COSTUME, true)
    end
end
mod:AddCallback(ModCallbacks.MC_POST_PLAYER_UPDATE, mod.myFunction2, 0)
```

特别感谢 _**Piber20**_ 和 _**JSG**_ 找出这些方法！