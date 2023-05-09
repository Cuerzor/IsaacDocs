---
tags:
  - 教程
---
# [教程] Lua中的函数
----

首先，请见[示例项目教程](ExampleProject.md)。

## 局部函数

Lua中最基本的函数类型是局部函数。例如，以下是“示例项目”教程中的代码：

```lua
local mod = RegisterMod("My Custom Tears", 1)

local function postFireTear(_, tear)
  -- MOD代码
end

mod:AddCallback(ModCallbacks.MC_POST_FIRE_TEAR, postFireTear)
```

关于这段代码，一个潜在的奇怪之处是，我们将函数的第一个参数表示为`_`。

按照惯例，未使用的参数以下划线为前缀，如`_foo`。通过在没有任何其他注释的情况下将自变量命名为`_`，这对读者来说是一个标志，表明我们完全忽略了这个变量，它没有任何目的。

我们的本地函数需要一个“空白”的第一个参数的原因是，处理回调的C++代码使用“冒号运算符”调用所提供的函数。冒号运算符[在Lua手册中有介绍](https://www.lua.org/pil/16.html)。基本上，冒号是用`self`参数调用函数的语法糖，该参数包含函数所在的模块。

在我们使用本地函数的情况下，没有模块，因为它只是一个简单的、独立的本地函数。因此，在这种情况下，第一个自变量总是等于nil。

让我们来看看模块函数是什么样子的。

## 模块函数

从`RegisterMod`函数返回的对象是一个Lua表。由于它是一个表，我们可以在表中放入任意函数：

```lua
local mod = RegisterMod("My Custom Tears", 1)

function mod.postFireTear(_, tear)
  -- MOD代码
end

mod:AddCallback(ModCallbacks.MC_POST_FIRE_TEAR, myMod.postFireTear)
```
在这里，“postFireTear”函数现在是“myMod”Lua表的一部分。我们用句点来表示连接。此代码将以与本地函数相同的方式工作。

在声明函数时，我们还可以使用冒号运算符：

```lua
local mod = RegisterMod("My Custom Tears", 1)

function mod:postFireTear(tear)
  -- MOD代码
end

mod:AddCallback(ModCallbacks.MC_POST_FIRE_TEAR, myMod.postFireTear)
```

在这段代码中，冒号运算符指定函数的第一个参数实际上是“self”，第二个参数实际上为“tear”，尽管它没有明确地这样写。和以前一样，它将以与本地函数相同的方式工作。

还要注意，在添加回调时（AddCallback），我们不使用冒号运算符，因为我们需要传递对函数的引用，而不是调用它。

在Lua中，函数通常是模块的一部分，因此使用冒号运算符调用它们被认为是标准的。

## 匿名函数

指定回调函数的第三种方法是使用匿名函数，它是一个没有名称的函数：

```lua
local mod = RegisterMod("My Custom Tears", 1)

mod:AddCallback(ModCallbacks.MC_POST_FIRE_TEAR, function(_, tear)
  -- MOD代码
end)
```

这个函数只存在于AddCallback调用的范围内，这意味着不能从其他任何地方引用或调用它。和以前一样，它将以与本地函数相同的方式工作。

匿名函数很有用，因为它们很容易键入。您可以将它们用于具有明显意义的非常简短的函数。