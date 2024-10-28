---
tags:
  - 教程
---
# [教程] 示例项目
----

## 示例 MOD

要制作新的 MOD，请在以下目录中创建一个新的子目录：

```
C:\Program Files (x86)\Steam\steamapps\common\The Binding of Isaac Rebirth\mods
```

（这与您的 Steam 安装目录相对应。如果您将游戏安装到自定义位置，那么路径可能会有所不同。）

使用你的 MOD 名称命名子目录。例如：

```
C:\Program Files (x86)\Steam\steamapps\common\The Binding of Isaac Rebirth\mods\customTears
```

接下来，在新创建的文件夹中创建一个新的 `main.lua` 文件。这个文件将包含 Lua 代码，它将告诉游戏你的 MOD 应该如何响应游戏中的事件。

以下是一个示例 MOD，它会改变玩家的泪弹，使其能够减速敌人，并具有暗物质的视觉效果：

```lua
-- 注册mod，它可以添加与游戏中事件相对应的代码（即“回调”）。
local mod = RegisterMod("Custom Tears", 1)

local function postFireTear(_, tear)
  -- 使用“二进制或”操作符为泪弹添加减速效果。
  tear.TearFlags = tear.TearFlags | TearFlags.TEAR_SLOW

  -- 更改泪弹的外观。（泪弹的“Variant”被游戏用来决定如何绘制外观。）
  tear:ChangeVariant(TearVariant.DARK_MATTER)
end

 -- 指定当玩家发射泪弹时，应执行“onTear”函数。
mod:AddCallback(ModCallbacks.MC_POST_FIRE_TEAR, postFireTear)
```

从这里，您可以更改代码以执行任何您想要的操作。简而言之，您必须添加适当的回调（以便在所需的特定事件内运行代码），然后必须使用适当的 API 方法（根据你想要做的事情，改变游戏中的事物）。

首先浏览 `ModCallbacks` 枚举的文档，了解所有不同的回调选项是什么。然后，浏览 API 文档的其余部分，了解哪些内容可以读取和更改。