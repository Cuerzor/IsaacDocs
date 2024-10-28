---
tags:
  - 教程
---
# [教程]使用额外的 .lua 文件

如果您想在 main.lua 文件之外加载一个额外的 .lua 文件，您可以使用 “require” 或 “include” 函数。两者都有不同的目的。

### `require`

`require` 是一个内置的 Lua 函数。在Lua程序中，使用 `require` 是将代码拆分为多个文件的传统方式。例如：

#### `main.lua`

```lua
local foo = require("foo") -- 加载 "foo.lua" 文件，并且将其返回值储存在变量 "foo" 中。

foo:bar() -- 调用foo表的 "bar()" 函数。
```

#### `foo.lua`

```lua
local foo = {} -- 创建一个表示此模块的表，稍后将返回该表。

function foo:bar() -- 定义函数 "bar()" 并将其添加到 "foo" 表中。
  print("hello")
end

return foo -- 返回 "foo" 表，以便任何导入该文件的东西都可以访问该表。
```
这里，"foo" 是一个提供变量和方法的 Lua *模块*。也可以返回函数或值，但通常 Lua 模块总是返回一个表。

`require` 的一个重要方面是，当使用它时，它会缓存结果。因此，当一个文件在代码中的两个不同位置被 require 时，它将在第一个要求时正常执行所有代码，然后在第二个要求时直接返回对模块的引用。（这种默认行为是有意义的，因为不需要反复执行相同的代码。）

### 使用文件目录的 `require`

与其他编程语言不同，在 Lua 中，一般使用句点作为路径分隔符。例如，如果您想在名为 "foo" 的子目录中导入名为 “bar.lua” 的文件，则可以使用以下 `require` 语句：

```lua
local bar = require("foo.bar") -- 从路径：./foo/bar.lua导入模块
```

当然，你也可以使用 `/` 作为分隔符。

### `require` 的命名空间问题

与其他编程语言中的导入语句不同，`require` 函数不使用相对路径。相反，它是基于传递给函数的确切字符串。（每个mod目录都被添加到要查看的目录列表中。）

这会给在 `require` 的路径中有重叠的 MOD 带来问题。例如，假设有两个 MOD，mod1和mod2。两个 MOD 都有一个名为"foo.lua"的文件，并且两个 MOD 都使用一个`local foo = require("foo")`的 require 语句。 MOD 1 将正常工作，但当 MOD 2 加载时，其 `require` 语句实际上将从 MOD 1 返回 "foo.lua" 文件。

为了解决这个问题， MOD 通常会将所有 Lua 文件放在与 MOD 名称匹配的目录中。例如， MOD 1 将创建一个名为 `mod1` 的目录，并有一个导入语句，如：`local foo = require("mod1.foo")`

这样，只要没有其他被称为 `mod1` 的 MOD，就永远不会发生冲突。

### `require` 的 `luamod` 问题

`luamod` 是一个控制台命令，它将重新加载一个 MOD。当你正在开发一个 MOD，并且你想立即测试你的更改而不返回主菜单时，这很有帮助。

不幸的是，`require` 的缓存机制会导致 `luamod` 控制台命令无法正常工作。如果模块内部的代码被更新，在使用 `luamod` 命令后，它将不会反映在游戏中，因为对该模块的引用已经被缓存。

### `include`

为了解决命名空间问题和 `luamod` 问题，Kilburn在Repentance补丁v1.06.J818中添加了一个名为 `include` 的以撒特有的API函数。`include` 的工作方式与 `require` 基本相同，只是它永远不会缓存结果，导致每次都执行代码。（它也永远不会从其他人的 MOD 中获取文件，即使路径相同。）

### 共享变量

`include` 仅设计给没有[副作用](https://en.wikipedia.org/wiki/Side_effect_(computer_science))的[纯模块](https://en.wikipedia.org/wiki/Pure_function)。换言之，如果在具有模块级状态变量的模块上使用 `include`，则它们将被实例化N次，每个 `include` 实例化一次。显然，这真的很糟糕，因为文件之间的内部状态将变得不同步。

因此，如果您具有模块级状态或需要在文件之间共享变量，则不能使用 `include`，而必须使用 `require`。

### 解决 require 问题

如果您需要使用 `require` 而不是 `include`，建议您将所有 Lua 代码都放在名称空间目录中，如前所述。如果你还想拥有 `luamod”` 功能，你可以启用 “--luadebug” 启动选项，然后用以下内容修改 `require` 函数：

```lua
--[[ main.lua ]]--

local MOD_NAME = "MyMod" -- 因为代表一个路径，不能拥有空格

-- 玩家可以通过名为“--luadebug”的启动选项启动游戏，这将启用额外的
-- 被认为不安全的功能。有关此选项的更多信息，请参阅wiki:
-- https://bindingofisaacrebirth.fandom.com/wiki/Launch_Options
--
-- 启用此标志后，全局环境将略有不同。不同之处在此处被列出:
-- https://cuerzor.github.io/IsaacDocs/Globals.html
--
-- 此函数使用“package”全局变量作为代理来确定“--luadebug”标志是否已启用。
local function isLuaDebugEnabled()
  return package ~= nil
end

-- 修改过的require使用全局变量来存储为该特定mod缓存的路径。
-- 这不能是局部变量，因为当执行“luamod”命令时，任何局部变量的状态都会丢失。
-- 重命名该变量以与您的mod名称相对应。
local function initGlobalVariable()
  if __MY_MOD_REQUIRED_PATHS == nil then
    __MY_MOD_REQUIRED_PATHS = {} -- 必须是全局变量
  end
end

-- 引用全局变量以重置mod中使用的每个路径的缓存状态。
local function unloadEverything()
  for k, v in pairs(__MY_MOD_REQUIRED_PATHS) do
    package.loaded[k] = nil
  end
end

-- 备份原版的require函数，以便我们稍后可以恢复它。
local vanillaRequire = require

-- 定义一个自定义的require函数，该函数将跟踪需要哪些路径。
local function patchedRequire(file)
  __MY_MOD_REQUIRED_PATHS[file] = true
  return vanillaRequire(file)
end

local function init()
  if isLuaDebugEnabled() then
    initGlobalVariable()
    unloadEverything()
    require = patchedRequire
  end

  -- 我们将所有与mod相关的代码放在一个单独的文件中，以保持与修改过的代码的分离。
  local modInit = require(MOD_NAME .. ".init")
  modInit:init()

  if isLuaDebugEnabled() then
    -- 恢复原版函数。
    require = vanillaRequire
  end
end

init()
```

### 解决 require 问题的替代方法

同样值得注意的是，如果您使用 [:material-language-typescript:IsaacScript framework](https://isaacscript.github.io/) 和 TypeScript 编写 MOD，则上述 `require` 问题不存在。这是因为 transpiler 会自动将所有代码组合到一个 “main.lua” 文件中。这意味着，您不必在使用 `include` 和 `require` 之间左右为难，也不必担心状态问题，也不需要对 `require` 函数进行猴子补丁——您只需编写有效的代码即可。