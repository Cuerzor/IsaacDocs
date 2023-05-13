---
tags:
  - 教程
---
# [教程] 使用自定义回调

忏悔1.79b更新中加入了一些供回调使用的函数，使用它们可以为mod中的自定义回调添加优先级与兼容性。

## 基本回调

你可以将任意代表回调ID的值与 `mod:AddCallback` (或者 `Isaac.AddCallback`, 但我们更推荐使用mod表，即前者)搭配使用。这些值可以是任意类型，包括字符串。

```Lua
MOD:AddCallback("TEST", function(_, a, b, c)
    print("test callback triggered", a, b, c)
end)
```

就实际情况而言，我们更推荐使用字符串而非数字作为自定义回调的ID. 虽然原版游戏提供的mod API中回调有对应的数字ID, 但使用字符串可以避免与其他mod所添加的自定义回调产生冲突。

但仅仅输入这串代码不会起到任何作用，因为游戏中（或者mod里）没有任何事件可以触发"test"回调使其执行。为了使这一回调执行，你应该输入：

```Lua
Isaac.RunCallback("TEST", 1, 2, 3)
```

这条代码会按优先级和添加的先后顺序（首先判断优先级，然后判断先后）执行所有ID为"test"的自定义回调。

注意一点：在这一过程中我们不必“定义”添加的回调。mod可以仅通过使用自定义回调对应的ID的值来将其执行，无需任何前置定义。

## 返回值

通过`Isaac.RunCallback`执行回调时，若回调返回了任意值，该函数将在首个返回了值的回调处终止执行，并返回该值。
示例如下：

```Lua
MOD:AddCallback("TEST_RETURN", function(_, a, b)
    return a + b
end)
MOD:AddCallback(ModCallbacks.MC_POST_GAME_STARTED, function()
    local ret = Isaac.RunCallback("TEST_RETURN", 1, 2)
    print(ret)
end)
```

输入这串代码后，控制台和日志文件应当在每次游戏开始时显示"3".

## 实体类型/参数对应

游戏mod API中提供的回调有部分需要特定参数才会执行，我们也可以如此对自定义回调加以限制。任意你设想的情景中所必须的值都可以作为特定参数，如实体类型或实体变种等。

```Lua
-- 添加自定义回调
MOD:AddCallback("TEST_ENTITY", function(_, entity, a, b, c)
    print("test callback triggered", entity.Type, a, b, c)
end)

-- 为自定义回调添加限制参数
MOD:AddCallback("TEST_ENTITY", function(_, entity, a, b, c)
    print("tears only callback triggered", entity.Variant, a, b, c)
end, EntityType.ENTITY_TEAR)

-- 执行有限制参数的自定义回调

-- 此函数将执行所有自定义回调，无视限制参数
Isaac.RunCallback("TEST_ENTITY", 1, 2, 3)
-- 此函数将不执行“仅眼泪”（限制参数为EntityType.ENTITY_TEAR）的自定义回调
Isaac.RunCallbackWithParam("TEST_ENTITY", EntityType.ENTITY_PLAYER, entity, 1, 2, 3)
-- 此函数将执行“仅眼泪”回调，而非一个ID不同的回调
Isaac.RunCallbackWithParam("TEST_ENTITY", EntityType.ENTITY_TEAR, entity, 4, 5, 6)
```

正如前文所说，特定参数可以是任意值，不必局限于实体类型。`Isaac.RunCallbackWithParam` 函数会逐个检查所有回调的限制参数是否为nil（无限制），若不为nil则检查其是否与该函数的第二个变量相对应。

## Mod兼容

之前讨论过，自定义回调不必先“定义”后使用。创建自定义回调只需要`Isaac.RunCallback` 执行至少一次且与`AddCallback`搭配。 

这使得mod可以十分轻松地为其他mod提供自己的API: 依赖该mod运行的其他mod无需等待主mod完全加载便可使用其API.
假如有这么一个小地图mod，暂且称其为MinimapLibrary（小地图库）。现在这个mod希望其他依赖其运行的mod能够在小地图变换大小后执行特定代码。
MinimapLibrary中的代码如下：

```Lua
-- ... 小地图变换大小时执行的回调
Isaac.RunCallback("MINIMAPLIB_POST_MINIMAP_ENLARGE", nil, currentSize)
```

依赖其运行的mod（Mod 2）代码如下：

```Lua
MOD2:AddCallback("MINIMAPLIB_POST_MINIMAP_ENLARGE", function(_, currentSize)
    print("Minimap size has changed!", currentSize)
    -- 以currentSize为变量做些事情
end)
```

可以看出Mod 2在使用MinimapAPI提供的mod方法时，完全不需要检查MinimapAPI是否加载。原因很简单：前置mod已加载则执行，尚未加载则不执行。完全不需要等到前置库/API mod完全加载才执行——前置mod定义了对外提供的mod方法时才需要先加载再使用。

## 执行模式

通常情况下`Isaac.RunCallback`会在首个返回了值的回调处中断并返回该值，但如果你需要别的方法处理回调的执行与返回模式，那你需要通过`Isaac.GetCallbacks`手动修改。

如果你想让回调继续执行，并且用最后得出的返回值覆盖其首个参数，可以这么做：

```Lua
MOD:AddCallback("TEST_GETCALLBACKS", function(_, arg) 
    return arg + 2
end)
MOD:AddCallback("TEST_GETCALLBACKS", function(_, arg) 
    return arg * 2
end)

local thisArg = 10
local callbacks = Isaac.GetCallbacks("TEST_GETCALLBACKS")
for _, callback in ipairs(callbacks) do
    local ret = callback.Function(callback.Mod, thisArg)
    if ret ~= nil then
        thisArg = ret
    end
end

print(thisArg) -- 显示 24
```

`Isaac.GetCallbacks`会返回一张包含所有回调的表，并按回调优先级与添加的先后顺序自动进行排序，所以无需担心循序问题（除非你想改）。表中元素结构如下所示：

```
{
    Mod = <mod table>,
    Function = function(mod, callback args),
    Priority = integer (default 0),
    Param = entity id / other param (default -1),
}
```

若该回调尚不存在，向`Isaac.GetCallbacks`的第二参数中传入true值可以为其分配一张空表。

## 进阶参数

既然通过`Isaac.GetCallbacks`可以得到该回调对应的表，那自然可以为其分配一张元表。此过程中，游戏不再使用默认方式（使用==的判定方式）进行检验，而是特别使用一个新函数，传递一个不同的参数并进行判断。

```Lua
--使用带自定义参数的函数初始化自定义回调
--在Isaac.GetCallbacks中传入true作为其第二个参数，若该回调不存在则为其分配一张空表
--参数可以是任意类型，但在此例中我们将表作为参数
--若任意参数为nil则总是匹配
setmetatable(Isaac.GetCallbacks("TEST_PARAMS_2", true), {
    __matchParams = function(a, b)
        return not a or not b or (type(a) == "table" and type(b) == "table" and a[1] == b[1] and a[2] == b[2])
    end
})

--该回调无参数，每次都会触发
MOD:AddCallback("TEST_PARAMS_2", function()
    print("hi!")
end)

--这些回调有参数，只会在参数与提供给Isaac.RunCallbackWithParam的一致时触发
--使用__matchParams这一元方法检测参数是否匹配
MOD:AddCallback("TEST_PARAMS_2", function()
    print("hello world")
end, {"hello", "world"})

MOD:AddCallback("TEST_PARAMS_2", function()
    print("greetings earth")
end, {"greetings", "earth"})

MOD:AddCallback("TEST_PARAMS_2", function()
    print("howdy globe")
end, {"howdy", "globe"})

--这样做应该只会显示“hi!”，然后显示“hello world”
Isaac.RunCallbackWithParam("TEST_PARAMS_2", {"hello", "world"})
```

*(案例提供： _Kilburn)*

## 唯一回调ID

强烈推荐在自定义回调的ID中添加独特前缀，最好与你的mod相关。这样可以避免与其他mod的自定义回调重名，导致冲突。例如，如果mod名叫AchievementLibrary，自定义回调应该取名为ACHLIB_TEST_CALLBACK，或其他类似的命名。

若想让自定义回调即使重名也具有唯一的ID，比方说存在于其他mod中的库mod，且该回调基于其逻辑应当运行不止一次，那就可以使用表引用作为其ID（使用字符串ID会导致其他同名回调也运行不止一次）。示例如下：

```Lua
MyLibrary.Callbacks.TEST_CALLBACK = {}
MyLibrary.Callbacks.TEST_CALLBACK_2 = {}

MOD:AddCallback(MyLibrary.Callbacks.TEST_CALLBACK, function
() 
    print("TEST 1")
end)
MOD:AddCallback(MyLibrary.Callbacks.TEST_CALLBACK_2, function()
    print("TEST 2")
end)

Isaac.RunCallback(MyLibrary.Callbacks.TEST_CALLBACK)
Isaac.RunCallback(MyLibrary.Callbacks.TEST_CALLBACK_2)
```

由于每个表引用都是唯一的，因此每张表都会被视作不同的ID，进而避免冲突。这么做有个优点：每个回调都具有唯一的局部定义ID，不会与可能重名的字符串共享全局空间。


