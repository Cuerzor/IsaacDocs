---
tags:
  - 常见问题
---

# MOD常见问题：疑难解答

### 为什么我的贴图在游戏中显示为黑色或红色方块？ {: .subHeader}

当贴图以错误的位深度保存时会发生这种情况。你需要手动将其设置为32位深度。（不要将其设置为“自动”。）

=== "![paint.net](misc/paintNetIcon.png) **Paint.NET**"

    ![paint.net](misc/32bit_paintNET.png)

=== "![photoshop](misc/photoshopIcon.png) **Photoshop**"

    ![photoshop](misc/32bit_photoshop.png)

### 为什么我制作的角色/跟班/敌人看不见？ {: .subHeader}

文件必须处在正确的目录，不然就没有用。该问题像是你把`.anm2`文件放进了错误的路径。注意在忏悔中，[MOD目录的位置](./GettingStarted.md#where-is-the-directoryfolder-for-mods-located)和胎衣+是不同的。

### 如何对代码进行故障排除？ {: .subHeader}

有一种久经考验的，可以找出几乎所有错误的，叫做“打印调试”的方法。在以撒中，它的意思是将一堆信息打印到log.txt文件，这样您就可以查看它，并查看代码的哪些部分被执行，哪些部分没有执行。所以，去代码中的一些位置，添加`Isaac.DebugString("到这里了1")`，`Isaac.DebugString("到这里了2")`等等输出信息的代码。然后，运行您的代码（即在游戏中各种尝试并触发错误），并研究log.txt文件试着看看发生了什么。

通常情况下，代码不起作用的原因是变量不是您认为的那样。所以，用一些类似于`Isaac.DebugString("到这里了 - FOO是: " .. tostring(foo))`的语句把每一步的变量都打印出来，这样你就可以确认它们是你认为的样子。

[REPENTOGON](https://repentogon.com/)有一个内置的日志查看器。您可能还想使用Zamiel制作的[这个](https://github.com/Zamiell/isaac-log-viewer)，或者pipe01制作的胎衣+版本的[这个](https://github.com/pipe01/abp-log/releases/tag/v0.3)日志查看器。

### 我的MOD导致游戏崩溃。如何找出导致崩溃的代码行？ {: .subHeader}

首先，查看log.txt文件寻找游戏崩溃原因的线索。然而，在绝大多数情况下，当游戏崩溃时，日志不会显示任何有用的信息。

如果你在Lua中编程你的mod，那么你唯一的选择就是插入大量的打印语句，试图缩小崩溃发生的范围。

如果您正在使用:material-language-typescript:TypeScript的[IsaacScript框架](https://isaacscript.github.io/)编程您的mod，您可以使用[崩溃调试插件](https://github.com/IsaacScript/isaacscript/blob/main/src/plugins/addCrashDebugStatements.ts)，这将把mod崩溃的确切行号写在log.txt中，非常方便。