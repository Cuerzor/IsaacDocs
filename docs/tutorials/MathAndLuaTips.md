---
tags:
  - 教程
---
# [教程] 以撒MOD的数学和Lua技巧

## Lua 技巧

## 遍历表

遍历表的最佳方法是使用 `ipairs()` 或 `pairs()` 函数。

### ipairs

`ipairs()` 遍历表，并提供元素的索引和元素值。该函数仅适用于没有任何键的表！

```lua
local exampleTable = {"apple", 69, 1337, -3}
for i, value in ipairs(exampleTable) do
    print(i, value)
end
```

???- example "输出"

    ```txt
    1 apple
    2 69
    3 1337
    4 -3
    ```

### pairs

`pairs()` 遍历表，并提供元素的键和元素值。该函数应该用于已定义键的表！

**注意：** 具有键的表是无序的。

```lua
local exampleTable = {["a"]="apple", [532]=69, ["something"]=1337, ["OwO"]=-3}
for key, value in pairs(exampleTable) do
    print(key, value)
end
```

???- example "输出"
    ```txt
    something 1337
    a apple
    532 69
    OwO -3
    ```

## 数组长度

### 没有键的表
对于没有键的表，可以在表名前面简单地使用 `#` 符号来获取表内元素的数量。
```lua
local exampleTable = {"apple", 69, 1337, -3}
print(#exampleTable) -- 结果：4
```

### 有键的表
对于有键的表，需要使用循环来计算条目数以获取表条目的数量。
```lua
local exampleTable = {["a"]="apple", [532]=69, ["something"]=1337, ["OwO"]=-3}
local counter = 0
for _ in pairs(exampleTable) do
    counter = counter + 1
end
print(counter) -- 结果：4
```

## 0 vs 1 基础索引
0 基础索引的集合，将从 0 到 集合长度-1 的范围内循环。

1 基础索引的集合，将从 1 到 集合长度 的范围内循环。

以撒MOD制作可能会让您感到困惑，因为您可能会在同一个代码文件中遇到这两种情况。

### C++容器 集合
这些集合类型是由游戏生成的，并使用基于 0 的索引。

```lua
local roomEntities = Game():GetRoom():GetEntities() -- c++容器
for i = 0, #roomEntities - 1 do
    local entity = roomEntities:Get(i)
    print(entity.Type, entity.Variant, entity.SubType)
end
```

### Lua 表
没有键的 Lua 表使用基于 1 的索引。您可以创建自己的表，或者它们可以由游戏生成。

**注意：** 这是为了演示目的。在这种情况下使用 `ipairs()` 更简单。

```lua
local roomEntities = Isaac.GetRoomEntities() -- table
for i = 1, #roomEntities do
    local entity = roomEntities[i]
    print(entity.Type, entity.Variant, entity.SubType)
end
```

### 随机性
MOD API中，有多种获取随机数的方法。

`RNG():RandomInt(max)` 将提供 0 到 max-1 的数字。可以给RNG设置种子，以使其在种子相同的情况下结果一致。

`math.random(max)` 将提供 1 到 max 的数字。

`Random()` 将提供 0 到 2^32-1 的数字。可以使用`%`符号进行取模，来限制随机数的范围。

**注意：**

* `math.random(max)` 对于不同机器的结果是不一样的，如果您想做有关于网络联机相关内容，则不应使用该函数。
* `Random()` 会过一个游戏内的随机数，因此在网络联机中，如果因为不同玩家的本地设置不同，而调用了不同次数的`Random()`，则会导致游戏不同步。

```lua
local items = { "item 1", "item 2", "item 3" } -- 表

local rng = RNG()
rng:SetSeed(Random(), 1)
print(items[rng:RandomInt(#items) + 1])

print(items[math.random(#items)])
```




## 数学技巧

## 取模（除法余数）
取模运算符`%`在编程中非常有用，因为它可以帮助你节省大量代码。它基本上返回通过给定数字除法得到的余数。

### 用法
```lua
local remainder = dividend % divisor
```
由于除法余数永远不会是负数或大于被除数，余数的值始终在 0 和 除数-1 之间。

???- example "示例"
    ```lua
    -- ...
    -3 % 3 -- = 0
    -2 % 3 -- = 1
    -1 % 3 -- = 2
    0 % 3 -- = 0
    1 % 3 -- = 1
    2 % 3 -- = 2
    3 % 3 -- = 0
    4 % 3 -- = 1
    5 % 3 -- = 2
    -- ...

    local isOddNumber = 123115 % 2 -- 结果为1。如果是偶数则为0。
    local isDivideableBySeven = 123429292 % 7 -- 结果为0。因此，它可以被7整除。
    ```

## 地板除法
虽然地板除法并不特别有用，而且很容易被使用`math.floor`代替，但它可以帮助简化和组织代码。它的工作方式与常规除法运算符类似，但将结果向下取整到最近的整数。

### 用法
```lua
local floorQuotient = dividend // divisor
```
它可以与模运算符结合使用，以重新创建被除数，如下所示：
```lua
local dividend = (floorQuotient * divisor) + remainder
```
请注意，它总是向等于或小于除法结果的数字四舍五入。这意味着`-11//5`将返回`-3`，而`11//5`将返回2。这使得如果你在使用地板商运算符之前或之后将数字变为负数，可能会生成不同的结果。

???- example "例子"
    ```lua
    -- ...
    -11//2 -- = -6
    11//2 -- = 5
    -11//-2 -- = 5
    -- ...

    local floorRightAngle = 170//90 * 90 -- 结果为90。
    local roundRightAngle = (170+45)//90 - 45 -- 结果为180。
    ```

## 整数 vs 浮点数

如果变量是一个数字，`type(x)` 会返回 "number"，但它不会告诉你它是整数还是浮点数。

`math.type(x)` 会返回 "integer" 或 "float"，如果它不是数字则返回nil。

```lua
local i = 1
local f = 1.0
print(type(i)) -- number
print(type(f)) -- number
print(math.type(i)) -- integer
print(math.type(f)) -- float
```