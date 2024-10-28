# 实体概述
## 介绍

以撒的结合里面的每一样东西几乎都是一个*实体*。

这个游戏的模组通常可以添加新的自定义实体，或在特定的时间任意生成实体，或修改现有的实体。

<br>

## 实体和单元格实体

下面是两种不同形式的实体：

### 1) 实体

游戏里大多数的数据都是“普通”实体，这里面包括了玩家、怪物、泪弹、敌弹和其他数据。

普通的实体表示为 `Entity` API 类。

原版实体在 "resources/entities2.xml" 文件中定义。模组可以通过创建 "content/entities2.xml" 文件并添加实体条目来创建自定义实体。

模组可以通过使用 `Isaac.Spawn` 和 `Game.Spawn` 两种方法来生成实体，第一种方法生成一个实体，而不在乎其种子应该如何，第二种方法生成一个实体，并需要指定该实体的种子。

提示：大部分生成的实体都应该设定种子，这样在游玩相同种子的情况下，可以使随机结果和其他随机效果保持一致（原版游戏就是这样运行的）。

### 2) 单元格实体

单元格实体是一种特殊的，可以与单元图格对齐的实体，其中包括了岩石、罐子等。

单元格实体表示为 `GridEntity` API 类。

原版单元格实体并没有 XML 文件中定义，因此模组无法创建自定义单元格实体。

模组可以通过 `Isaac.GridSpawn` 方法来生成单元格实体（但无法生成带有特定种子的单元格实体）。

<br>

## 类型、变种和子类型


一个实体ID由三个整数定义：`EntityType` 、`Variant` 和 `SubType` 。这三个值常用一个以点号为分隔符的字符串表示。

- `EntityType` 对应实体类型。 例如，裂口尸 (10.0.0) 的实体类型与狙击蝇 (14.0.0) 的不同 `EntityType`。
- `Variant` 对应不同变种但有着相同 `EntityType` 的实体。例如，皱眉裂口尸 (10.0.0) 和燃烧裂口尸 (10.2.0) 的变种 `Variant` 不相同。
- `SubType` 对应有着相同 `EntityType` 和 `Variant` 的不同实体。例如悲伤洋葱 (5.100.1) 和内眼 (5.100.2) 有着相同的类型和变种，但子类型 `SubType` 不相同。

`Entity` API 类包含了这三个值，分别为这个类的三个属性。`GridEntity` API类提供了 `GetType` 和 `GetVariant` 方法来获取这两种值（单元格实体通常没有子类型）。

你可以创建一个辅助函数来获得实体的 ID 字符串：

```lua
-- 一个用于获取包含实体的类型、变量和子类型的字符串数据的辅助函数。
local function getEntityID(entity)
  return tostring(entity.Type) .. "." .. tostring(entity.Variant) .. "." .. tostring(entity.SubType)
end
```

```lua
-- 一个用于获取包含单元格实体的类型和变量的字符串数据的辅助函数。
local function getGridEntityID(gridEntity)
  local gridEntityType = gridEntity:GetType()
  local gridEntityVariant = gridEntity:GetVariant()
  return tostring(gridEntityType) .. "." .. tostring(gridEntityVariant)
end
```

如果你正在使用 [IsaacScript](https://isaacscript.github.io/) 库，上述的两个函数已经被包含在其标准库中，因此你无需自建函数。

<br>
