---
tags:
  - 常见问题
---
# 《以撒的结合：忏悔》MOD常见问题

## 基本

### MOD禁用成就吗？ {: .subHeader}

**Mod不禁用成就**，但至少需要你的存档先不开启MOD和控制台击杀一次妈妈（即深牢II的头目）。在挑战或者每日挑战中击杀妈妈不算。

### 如何安装MOD？ {: .subHeader}

简单地点击Steam创意工坊页面上的“**订阅**”按钮即可，这会自动下载并安装MOD。只需要安装完毕后重启你的游戏，你安装的MOD就会被列在主界面的“模组”菜单中，并且可以将其启用/禁用。

### 我使用MOD需要安装所有DLC吗？ {: .subHeader}

要使用MOD，你必须至少安装游戏本体（重生），第一个DLC（胎衣），以及第二个DLC（胎衣+）。

第三个DLC（忏悔）并不强制要求，但因为其具有新的MOD特性，推荐安装。许多新的MOD都不与之前的胎衣+兼容。

### 重生/胎衣的MOD能在胎衣+/忏悔上玩吗？ {: .subHeader}

看你的MOD是什么，但是大部分情况下都不行。

### 怎么开启控制台？ {: .subHeader}

在胎衣+中，控制台在你启用至少一个MOD时会自动启用。

在忏悔中，控制台的启用基于options.ini文件中的"EnableDebugConsole"设置。默认情况下，它被设置为"0"，所以如果你想使用控制台，你必须把它从"0"改成"1"。（默认情况下，options.ini文件位于`文档\My Games\Binding of Isaac Repentance\options.ini`.）

要打开控制台，在一局游戏内按下**波浪号(~)**键。如果你不是英文键盘，详见[wiki的控制台页面](https://isaac.huijiwiki.com/wiki/%E6%8E%A7%E5%88%B6%E5%8F%B0)。

该wiki同时拥有一个[控制台命令的列表](https://isaac.huijiwiki.com/wiki/%E6%8E%A7%E5%88%B6%E5%8F%B0).

### 我要怎么开始做以撒的MOD？（新手入门） {: .subHeader}

如果你能够访问Youtube并且可以听懂英文，推荐观看[Youtube上的Lytebringr的教程视频系列](https://www.youtube.com/playlist?list=PLMZJyHSWa_My5DDoTQcKCgs475xIpQHSF)。这些视频是在胎衣+DLC发布之后制作的，但与忏悔DLC之间没有太大变化，所以它们仍然是你学习诀窍的最佳选择。

如果你不具备查看外网视频的条件，可以去视频网站上搜索一些以撒的MOD制作教程。

胎衣+和忏悔的一个主要区别是，[MOD目录的位置](#where-is-the-directoryfolder-for-mods-located)发生了改变。

其他资源：

- [项目实例教程](../tutorials/ExampleProject.md)
- [一些有用的工具](../tutorials/Tools.md)
- [AgentCucco的视频教程（Youtube）](https://www.youtube.com/playlist?list=PLUYzSIp7NO8cEer2FmtxSXlXoMFirvYDN) （播放列表）
- [:material-language-typescript:IsaacScript的“绿蜡烛”教程](https://isaacscript.github.io/main/example-mod)

### 我正在尝试制作一个基本的mod，但它不起作用。我试图制造一个角色/跟班/敌人，但贴图看不见。 {: .subHeader}

文件必须处在正确的目录，不然就没有用。注意在忏悔中，[MOD目录的位置](#where-is-the-directoryfolder-for-mods-located)和胎衣+是不同的。

即使您知道要正确地放在“mods”目录下，它们的内部文件也必须处于正确的特定位置。因此您可能没有将文件放在正确的地方。

首先，请遵循视频教程，或者其他人的指导，这大致对应于你想做的东西（例如角色/跟班/敌人/其他什么）。一步一步来，一旦你验证了你做的的角色/跟班/敌人/其他东西的工作方式与指导中的完全相同，然后开始一件一件地做出改变，直到你要做的东西开始不起作用。然后，你就会看到问题在哪里，如果需要，你可以继续问一些更具体的问题。

### 我在哪儿看[某些原版道具]或者[某些原版机制]？ {: .subHeader}

你不能。游戏是用C++编程语言编写的，源代码不开源。

这意味着，如果你想制作一个与原版道具类似的自定义道具，你必须从头开始完全重新实现它。（您可以经常使用wiki作为实现参考。）

这也意味着，如果你想改变一个原版道具的工作方式，你通常必须从头开始重新实现这个道具。

### 我可以雇佣/委托谁为我编程以撒MOD？ {: .subHeader}

社区的一些成员可以被雇佣来创建mod。有关具体建议，您可以在一些以撒相关群聊中询问。

## 资源

### <span id="where-is-the-directoryfolder-for-mods-located">MOD的目录/文件夹在哪里？</span> {: .subHeader}

所有MOD都在这个位置内：

=== ":fontawesome-brands-windows: **Windows**"

    ```
    忏悔:
    [以撒游戏目录]\mods\

    胎衣+:
    文档\My Games\Binding of Isaac Afterbirth+ Mods\
    ```

=== ":fontawesome-brands-apple: **Mac OS**"

    ```
    胎衣+:
    /Users/[username]/Library/Application Support/Binding of Isaac Afterbirth+ Mods
    ```

=== ":fontawesome-brands-linux: **Linux**"

    ```
    胎衣+:
    /Steam/steamapps/compatdata/250900/pfx/drive_c/users/steamuser/Documents/My Games/Binding of Isaac Afterbirth+ Mods
    ```

### 我要怎么解包文件？我要怎么用资源提取器？ {: .subHeader}

默认情况下，游戏资源在：

```
[以撒游戏目录]\resources
```

但是，除非您运行所提供的资源提取器，否则此目录将大部分为空。资源提取器位于此处：

```
[以撒游戏目录]\tools\ResourceExtractor\ResourceExtractor.exe
```

运行提取器后，resources目录将被游戏使用的所有XML文件、ANM2文件、图像和其他各种文件充满。

请注意，每次出现原版补丁时，您还必须重新运行资源提取器。

### [某个音效]的ID是什么？ {: .subHeader}

使用[这个MOD](misc/sounds-display.lua)，它会告诉你当前播放的任何音效的ID是什么。

### 我要怎么覆盖原版音乐？ {: .subHeader}

- 对于正常的音乐替换，您可以直接在MOD文件夹里替换相应的原版资源文件。
- 对于动态的音乐替换，请使用Taz的[音乐MOD回调MOD](https://steamcommunity.com/sharedfiles/filedetails/?id=2491006386).

### anm2文件在哪儿？ {: .subHeader}

- 在以撒中，贴图动画由位于`resources/gfx`文件夹中的anm2文件表示。
- 游戏中的每个实体都有一个相关的anm2文件。
- 此外，UI元素使用各种anm2文件进行渲染（位于`resources/gfx/ui`文件夹中）。
- anm2文件只是一种有不同文件扩展名的XML文件。
- 要编辑原版动画或添加新动画，您可以：
  - 直接使用文本编辑器编辑文件。（以撒前制作人员Kilburn就是这么做的。）
  - 使用提供的以撒动画编辑器编辑文件，该编辑器位于：`[以撒游戏目录]\tools\IsaacAnimationEditor\IsaacAnimationEditor.exe`

### 我要怎么编辑房间？ {: .subHeader}

官方房间编辑器伴随着游戏本体一起提供，位于：

```
[以撒游戏目录]\tools\RoomEditor\RoomEditor.exe
```

这是Edmund用来为《重生》和《胎衣》创建所有房间的工具。然而，官方编辑器用起来不是很好，也不能用于任何忏悔的房间。

2014年，Chronometrics制作了一个名为[Basement Renovator](https://github.com/Basement-Renovator/Basement-Renovator)的第三方房间编辑器，以提高官方编辑的水平。它是开源的，位于GitHub上。由于Basement Renovator比官方房间编辑好用得多，即使是官方开发商现在也使用Basement Renovator。（这就是为什么忏悔房间不能用官方编辑器编辑。）

Basement Renovator是用Python编写的，因此您可以从源代码运行它，也可以从[发布页面](https://github.com/basement-renovator/basement-renovator/releases)下载exe文件。

## 故障排除

### 为什么我的贴图在游戏中显示为黑色或红色方块？ {: .subHeader}

当贴图以错误的位深度保存时会发生这种情况。你需要手动将其设置为32位深度。（不要将其设置为“自动”。）

=== "![paint.net](misc/paintNetIcon.png) **Paint.NET**"

    ![paint.net](misc/32bit_paintNET.png)

=== "![photoshop](misc/photoshopIcon.png) **Photoshop**"

    ![photoshop](misc/32bit_photoshop.png)


### 为什么我订阅的mod在“mods”菜单中不可见？ {: .subHeader}

如果您即使在Steam创意工坊上订阅了MOD，MOD在mods文件夹中也不可见，这可能是由以下原因引起的：

1. 你不拥有胎衣和胎衣+。所有Steam创意工坊的MOD都需要安装这两个DLC才能正常工作。

2. （仅适用于胎衣+）您的Windows/Mac用户名包含不属于标准英文字母表的字符。由于游戏无法正确解析这些内容，因此无法找到mods文件夹。为了解决此问题，您必须在计算机上创建一个名称仅包含英文字符的新用户。

### MOD没效果。 {: .subHeader}

1. 检查MOD是否已列出启用在主界面“模组”菜单中。
2. 按照[这个问题](#a-mod-has-invisible-enemies-or-other-missing-content)中的步骤清理mod。
3. 检查log.txt是否包含任何错误消息。（默认情况下，log.txt位于`文档\My Games\Binding of Isaac Repentance\log.txt`）如果您在日志中看到了类似于`... attempt to call a nil value (global 'RegisterMod')`的提示，说明您的游戏文件可能已损坏，您需要验证游戏的完整性（见下文）。
4. 禁用你安装的所有其他mod，看看它们是否会导致任何错误。
5. 使用Steam“验证游戏文件的完整性”。有关更多信息，请参阅[本指南](https://inxile.zendesk.com/hc/en-us/articles/115004662908-Verify-game-cache-文件s-Steam-)。

### <span id="a-mod-has-invisible-enemies-or-other-missing-content">MOD有看不见的敌人或其他缺失的内容。</span> {: .subHeader}

这很可能是Steam没有下载所有的MOD文件造成的。您可以通过执行以下步骤清理mod：

1. 关闭游戏。
2. 取消订阅Steam创意工坊的mod。
3. 接下来，删除“mods”目录中的真实mod目录。（默认情况下，它位于`[以撒游戏目录]\mods`。）
4. 删除Steam缓存的MOD目录中的“mod”目录。（默认情况下，它位于`[Steam目录]\userdata\[Steam ID]\250900\remote`。）
5. 打开游戏。
6. 在介绍过场开始播放后关闭游戏。
7. 在Steam Workshop上重新订阅mod。
8. 再次打开游戏。当游戏看上去未响应时，**不要**关闭游戏。

### 为什么我的代码不起作用？我怎么知道哪里发生错误了？log.txt文件在哪里？ {: .subHeader}

Lua是一种解释型语言，这意味着如果你犯了拼写错误或有其他错误的代码，你只有在程序真正运行后才能发现它。如果Lua解释器遇到错误，它会将其写入游戏的log.txt文件.

默认情况下，该文件处于：

```
文档\My Games\Binding of Isaac Repentance\log.txt
```

打开这个文件并仔细搜索与Lua相关的错误。（Ctrl+F查找单词“error”是一个好方法。）这通常会告诉你写错的代码的的行号。

还建议在options.ini文件中设置`FadedConsoleDisplay=1`，这样在一局游戏中中发现错误就更容易了。默认情况下，options.ini文件位于：

```
文档\My Games\Binding of Isaac Repentance\options.ini
```

对于熟悉命令行应用程序的用户，请使用Zamiel的[以撒日志查看器](https://github.com/Zamiell/isaac-log-viewer)并在编写代码和测试时让它在第二个监视器上运行。

### 为什么log.txt文件里面什么都没有？ {: .subHeader}

每次打开游戏时，log.txt的所有内容都会被删除。因此，如果您在错误发生后需要日志中的信息，请确保不要重新启动游戏。

### 如何对代码进行故障排除？ {: .subHeader}

当你编写程序时，它们可能无法立即工作。你首先要做的不应该是把一堆代码粘贴到群聊里，然后问“为什么没用？”。这样做意味着你不会花太多精力试图独立解决问题。

有一种久经考验的，可以找出几乎所有错误的，叫做“打印调试”的方法。在以撒中，它的意思是将一堆信息打印到log.txt文件，这样您就可以查看它，并查看代码的哪些部分被执行，哪些部分没有执行。所以，去代码中的一些位置，添加`Isaac.DebugString("到这里了1")`，`Isaac.DebugString("到这里了2")`等等输出信息的代码。然后，运行您的代码（即在游戏中各种尝试并触发错误），并研究log.txt文件试着看看发生了什么。

通常情况下，代码不起作用的原因是变量不是您认为的那样。所以，用一些类似于`Isaac.DebugString("到这里了 - FOO是: " .. tostring(foo))`的语句把每一步的变量都打印出来，这样你就可以确认它们是你认为的样子。

您可能还想使用类似[这个](https://github.com/Zamiell/isaac-log-viewer)的日志查看器。

### 我修改了一个XML文件，但当我打开游戏或开始新的一局时会崩溃。 {: .subHeader}

崩溃意味着XML文件无效，这意味着您在编辑文件时写错了某个地方。从头开始，一次做一个小编辑，直到你找到导致游戏崩溃的确切部分。

另一个有用的故障排除工具是类似[xmlvalidation.com](https://www.xmlvalidation.com/)的XML验证器。

### 我启用一个MOD，现在我的游戏崩溃了。我该怎么解决这个问题？ {: .subHeader}

您可以尝试浏览log.txt文件看看有没有什么有趣的东西。然而，在绝大多数情况下，当游戏崩溃时，日志不会显示任何有用的信息。

相反，你可以通过逐个禁用你的mod来找到问题，直到你找到导致崩溃的确切mod。然后，你可以将其报告给mod的开发者，或者尝试自己手动修复代码。

请注意，无论何时启用或禁用mod，都应完全关闭并重新打开游戏（因为当您通过游戏内菜单启用/禁用mod时，游戏无法正确加载资源）。

### 我的MOD导致游戏崩溃。如何找出导致崩溃的代码行？ {: .subHeader}

首先，查看log.txt文件寻找游戏崩溃原因的线索。然而，在绝大多数情况下，当游戏崩溃时，日志不会显示任何有用的信息。

如果你在Lua中编程你的mod，那么你唯一的选择就是插入大量的打印语句，试图缩小崩溃发生的范围。

如果您正在使用:material-language-typescript:TypeScript的[IsaacScript框架](https://isaacscript.github.io/)编程您的mod，您可以使用[崩溃调试插件](https://github.com/IsaacScript/isaacscript/blob/main/src/plugins/addCrashDebugStatements.ts)，这将把mod崩溃的确切行号写在log.txt中，非常方便。

## 代码

### 我要怎么做X？ 我要怎么写X的代码？ {: .subHeader}

找出如何做某事的最快方法是下载一些提供与你想做的类似功能的mod，然后研究代码。

### 回调是什么？ {: .subHeader}

Mod通过将一些代码放入*回调*来修改游戏。当游戏中发生特定事件时，每个回调都会触发。有72种不同的回调可供选择，所以你必须根据你想做的事情选择正确的回调。

例如，最基本的回调是`MC_POST_GAME_STARTED`，它在一局新游戏开始时触发一次。您可以将代码放在这里，以在每局游戏开始时进行自定义操作。

Mod使用的另一个常见回调是`MC_POST_UPDATE`，它在每个更新帧上触发（即每秒30次）。您可以将具有固定效果的自定义道具的代码放入此回调中。

浏览[ModCallbacks页面](../enums/ModCallbacks.md)并阅读所有回调的作用，以便熟悉它们。

### <span id="how-do-i-understand-the-docs">我要怎么理解文档?</span> {: .subHeader}

![img](../images/docs_reading_guide.png)

### 什么是单行职责(SLR)？ {: .subHeader}

在编写代码时，要努力使其看起来美观，便于他人阅读，尤其是当你向他人展示或寻求帮助时。在这种情况下，遵循“单行职责”规则是一个好主意，这意味着**一行代码**应该只做**一件事**。阅读[此博客](https://midu.dev/single-line-responsability-haz-una-cosa-por-linea/)了解更多细节，你会明白为什么SLR伟大。

### 如何将人物外观应用于我的角色？ {: .subHeader}

这被称为“Null Costume”（空外观），它是通过`EntityPlayer.AddNullCostume()`方法来完成的。有关更多信息，请参阅[Lytebringr的第8个视频](https://www.youtube.com/watch?v=R1CdCyGL1DQ&list=PLMZJyHSWa_My5DDoTQcKCgs475xIpQHSF&index=9)。

???- example "示例代码"
    以下是一个使用MOD添加空外观的示例：

    ```lua
    local MOD_NAME = "My Mod"

    -- 用于EntityType.ENTITY_PLAYER (1)
    local PlayerVariant = {
      PLAYER = 0,
      COOP_BABY = 1,
    }

    local PlayerTypeCustom = {
      FOO = Isaac.GetPlayerTypeByName("Foo"),
    }

    local NullItemIDCustom = {
      BAR = Isaac.GetCostumeIdByPath("gfx/characters/bar.anm2"),
    }

    local mod = RegisterMod(MOD_NAME, 1)

    function mod:postPlayerInit(player)
      local character = player:GetPlayerType()

      if (
        player.Variant == PlayerVariant.PLAYER
        and character == PlayerTypeCustom.FOO
      ) then
        player:AddNullCostume(NullItemIDCustom.BAR)
      end
    end
    mod:AddCallback(ModCallbacks.MC_POST_PLAYER_INIT, mod.postPlayerInit)
    ```

### 如何使自定义角色的人物外观永久存在？ {: .subHeader}

使用[Sanio的“角色外观保护器”库](https://steamcommunity.com/sharedfiles/filedetails/?id=2541362255)，或者研究源代码并自己重新实现它。

有关参考实现，请参见[Andrew the Bunny Knight](https://steamcommunity.com/sharedfiles/filedetails/?id=2531089854)。

### 如何创建新的层？ {: .subHeader}

不幸的是，以撒并不支持MOD自定义楼层。BudJMT和DeadConfinity搭建了一个名为[StageAPI](https://github.com/Meowlala/BOIStageAPI15)的自定义系统，这允许Mod以一种巧妙的方式添加自定义楼层。然而，StageAPI并不容易使用，所以除非你已经是一个经验丰富的以撒MOD制作者和程序员，否则你应该坚持制作更简单的项目。

### 如何修改恶魔房/天使房的开启率？ {: .subHeader}

没有内置的方法可以做到这一点，所以您必须有些创造力。为了获得开启率的最大控制权，您可以删除所有原版的恶魔房/天使房门，并从头开始完全重新实现系统。或者，您可以临时将道具给予玩家，如山羊头或念珠段，或使用[Game.SetLastDevilRoomStage()](../Level.md#setlastdevilroomstage)或[Level.SetRedHeartDamage()](../Level.md#setredheartdamage)方法。您还可能需要使用[LevelStateFlags](../enums/LevelStateFlag.md)。

### 我该如何让一个跟班像波比兄弟那样跟随玩家？ {: .subHeader}

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

### 如何使用StageAPI添加新头目？ {: .subHeader}

这是一段来自于Xalum的示例代码:

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

### 如何使我的自定义角色开局自带熔炼/吞下的饰品？ {: .subHeader}

没有办法通过编辑XML文件来完成此操作。因此，您必须通过Lua或TypeScript代码来实现这一点。

### 我要怎么知道玩家什么时候捡到了道具？ {: .subHeader}

对此没有原版的回调。作为一种变通方法，您可以在PostUpdate回调中使用`EntityPlayer.IsItemQueueEmpty()`检查玩家是否没有在举起道具，然后在举起道具的时候通过`EntityPlayer.QueuedItem`获取道具ID。显然，这对直接添加的不起作用。

对于:material-language-typescript:[IsaacScript](https://isaacscript.github.io/)使用，您可以使用IsaacScript提供的[:material-language-typescript:MC_POST_ITEM_PICKUP](https://isaacscript.github.io/docs/function-signatures-custom#mc_post_item_pickup)回调。

如果你想自己实现这个回调，[这里](https://github.com/IsaacScript/isaacscript-common/blob/main/src/callbacks/itemPickup.ts)提供了源代码/算法。

### 如何得知某个实体的实体类型、变种或子类型？ {: .subHeader}

您可以：

1. 在游戏控制台中输入“spawn x”。例如，“spawn Confessional”将显示忏悔室的ID为6.17。这意味着它的实体类型是6，变种是17。
2. 或者，您可以在“resources-dlc3/entities2.xml”文件中使用ctrl+f搜索您想要的实体。

### 如何让角色蒙眼？ {: .subHeader}

=== ":material-language-lua: Lua"
    ```lua
    --- Zamiel编写代码，im_tem创建该机制
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

        -- The costume is applied automatically
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
    如果你正在使用[:material-language-typescript:IsaacScript](https://isaacscript.github.io/)，你完全可以直接调用`setBlindfold`函数，如：

    ```ts
    const player = Isaac.GetPlayer();
    setBlindfold(player, true);
    ```

### API和库之间的区别是什么？ {: .subHeader}

创意工坊上的一些MOD将功能打包在一起，作为抽象供其他人使用。在软件中，这就是通常所说的“库”。作为一名程序员，利用别人经过实际测试的库通常比从头开始使用自己的库容易得多。

另一方面，API是“应用程序编程接口”的缩写，这正是它听起来的样子。应用程序可能希望向外部用户和软件公开一些功能，并且它将通过显式定义的接口来实现这一点。库公开了API，以便最终用户可以使用它们。但请注意，*任何*软件都可以有一个API，而不仅仅是一个库。例如，启示录MOD是一个流行的MOD，它为游戏添加了新的楼层、头目和道具。但它也公开了一个API，这样它就可以与其他MOD兼容。

从历史上看，以撒的一些库将自己标记为“API”，但这是一个用词不当的说法。这方面的一些例子包括[StageAPI](https://github.com/Meowlala/BOIStageAPI15)和[MinimapAPI](https://github.com/TazTxUK/MinimapAPI)。另一方面，一个正确命名的库的例子是Sanio的[角色外观保护器](https://steamcommunity.com/sharedfiles/filedetails/?id=2541362255)。

如果你正在创建一个新的库，请使用正确的术语来命名你的项目，这有助于防止以撒MOD制作新手感到困惑。

### 什么是微观优化？我应该优化我的MOD吗？ {: .subHeader}

#### 定义

作为程序员，我们经常关心程序的运行速度如何。

当新手程序员开始考虑“性能”时，他们可能会对代码进行糟糕的调整，希望它能加快速度。这些被称为[微观优化（或过早优化）](https://wiki.c2.com/?PrematureOptimization)。例如，新手可能会从一些整齐地组织成单独函数的代码开始，如下所示：


```lua
local function main()
  -- 使用foo做点什么
  foo()

  -- 使用bar做点什么
  bar()
end

local function foo()
  -- TODO
end

local function bar()
  -- TODO
end
```

在上面的代码中，我们有两个小函数，命名良好（理论上），易于阅读和理解。但是新手可能会想把代码转换成这样：

```lua
local function main()
  -- 使用foo做点什么
  -- TODO

  -- 使用bar做点什么
  -- TODO
end
```

这里的想法是，既然我们去掉了两个函数调用，那么程序在理论上应该会加快速度。（因为在后台，函数在被调用时所做的是将值放在堆栈上，然后在完成后将它们从堆栈中弹出。）

但实际上，编译器通常可以优化代码以自动执行这种加速（而无需程序员实际修改其源代码）。因此，在这种情况下，新手程序员获得了运行效率完全一样的字节码，代价是源代码变得更糟。太差劲了！

此外，即使编译器没有自动优化函数调用，调用函数的简单操作也可以在几纳秒内完成。你永远无法有意义地衡量程序的运行时性能中，使用一些额外的函数调用所产生的区别。所以还是和以前一样：新手程序员正在使他们的源代码变得更糟，而没有可衡量的好处。

微观优化是许多新手陷入的陷阱。花在执行微观优化上的时间应该花在测量代码中的实际瓶颈上，然后对这些瓶颈进行优化。或者修复真正的bug！或者添加真正的功能！

这就是为什么程序员有这样一句格言：“过早的优化是万恶之源。”，出自[唐纳德·克努特](https://en.wikipedia.org/wiki/Donald_Knuth)，是有史以来最著名的计算机科学家之一。在他的论文“[Structured Programming with go to Statements](https://pic.plover.com/knuth-GOTO.pdf)”中，他写了这样一句著名的话：

> 程序员浪费了大量的时间去考虑或担心程序中非关键部分的速度，而当考虑到调试和维护时，这些对效率的尝试实际上会产生强烈的负面影响。我们应该忘记这种微小的效率，比如说因为过早优化而浪费的大约97%的时间。然而，我们不应该放弃那关键的 3% 的机会

#### 测量性能

在上面的例子中，新手认为删除函数调用会加快程序的速度。但这些假设可以是关于任何类型的代码，而不仅仅是函数调用。您可能“知道”以某种方式进行编码会比以另一种方式更快。

但在实际生活中的程序中，要预测哪种代码形式实际上会影响程序的性能是**极其困难**的。有时，你可以做出一个你认为会加快程序的变更，但却会让程序变慢！有时，你可以做出一个你认为会让程序变慢的变更，但它却加快了速度！编译器一直在引擎盖下做各种摸不着头脑的事情。

这就是为什么当我们谈论优化时，最需要讨论的是**测量性能**。测量一段代码的运行时间的行为叫做性能分析。（也可以称为基准测试。）

记住来自于C2 wiki的**[优化的三条准则](https://wiki.c2.com/?RulesOfOptimization)**：

1. 别这么做。
2. 现在先别这么做。
3. 优化前先做性能分析。

这3条规则背后的理念是，在实际生活中的程序中，你几乎从不需要优化。但如果你真的这么做了，你**必须**在之前和之后都测量性能。根据你的衡量标准，它会告诉你代码更改是否值得让代码变得更长、更复杂或更难理解。有时候，这是值得的，但往往不会。

#### 代码清晰度

那么，如果你一般不应该关心性能，你应该关心什么呢？答案是代码清晰度。

首先也是最重要的一点，代码的目标是使其简洁易读。（即使你正在编写的代码永远不会被其他人阅读，你仍然应该让它整洁易读，以供未来的你阅读，因为你可能需要在几个月或几年后阅读这些代码，并且必须弄清楚它能做什么来修复一些错误。）

您可能会认为将“代码清晰度”列为比拥有“能跑的代码”更重要这个做法很蠢。这当然有争议。但考虑一下：

- 不能跑但易于理解的代码可以被修改，让它能跑。
- 能跑但无法破译的代码将很难修改。这意味着我们可能无法修复任何错误或添加新功能。

[吉多·范罗苏姆](https://en.wikipedia.org/wiki/Guido_van_Rossum)，编程语言[Python](https://www.python.org/)的创建者，他的关键见解之一就是[代码读起来比写起来频繁得多](https://www.python.org/dev/peps/pep-0008/)。Python被设计为简洁、干净和可读的语言，它有标准的做事方式，并建议每个人都遵循[PEP-8编码标准](https://www.python.org/dev/peps/pep-0008/)。现在，Python是[世界上最流行的编程语言](https://pypl.github.io/PYPL.html)。代码的可读性并不是Python崛起的*唯一*原因，但它仍是重要的原因之一。

## Lua

### How do I iterate over a list object from the API? {: .subHeader}

For example，in Lua:

=== ":material-language-lua: Lua"

    ```lua
    local game = Game()
    local level = game:GetLevel()
    local rooms = level:GetRooms()
    for i = 0, rooms.Size - 1 do
      local room = rooms:Get(i)
      -- Do something with the room
    end
    ```

=== ":material-language-typescript: TypeScript"

    In IsaacScript，you could implement the code on the Lua tab in the exact same way. However，for this specific case，you can simply use a helper function to iterate over the rooms directly:

    ```ts
    for (const roomDescriptor of getRooms()) {
      // Do something with the room
    }
    ```

### What is the 区别 between `require` and `include`? {: .subHeader}

See the [tutorial on using additional Lua 文件s](../tutorials/Using-Additional-Lua-文件s.md).

### What is the 区别 between `pairs` and `ipairs`? {: .subHeader}

- `pairs` is for iterating over Lua tables that represent a [map](https://en.wikipedia.org/wiki/Associative_array). In other words，something with key/value associations.
- `ipairs` is for iterating over Lua tables that represent an [array](https://en.wikipedia.org/wiki/Array_data_structure). In other words，something that contains a list of elements.

Code speaks louder than words:

```lua
local map = {
  foo = "bar",
  baz = 123,
}

for key, value in pairs(map) do
  print(key) -- Prints foo, baz
  print(value) -- Prints bar, 123
end
```

```lua
local array = {
  123,
  456,
  789,
}

for i, element in ipairs(array) do
  print(i) -- Prints 1, 2, 3
  print(element) -- Prints 123, 456, 789
end
```

Since Lua is [untyped](https://www.tutorialspoint.com/What-are-the-differences-between-untyped-and-dynamically-typed-programming-languages) and uses tables to represent multiple different data structures，`pairs` and `ipairs` serve as a flag to tell the reader what the underlying data structure really is.

### What does the colon operator in Lua do? {: .subHeader}

In Lua，you can invoke module functions (i.e. functions that are attached to a table) in two different ways:

```lua
foo.bar()
foo:bar()
```

A period invokes the function in the "normal" way. A colon invokes the function in a special way that is syntactic sugar for passing the module as the first argument. For example，the following two function calls are equivalent:

```lua
foo.bar(foo, arg1, arg2)
foo:bar(arg1, arg2)
```

The point of using the colon is that it is a convenience to save you from typing out the longer function call，at the cost of some obfuscation for those not familiar with Lua. This feature is included in the language since doing this is such a common task. (Lua modules are often used to emulate Java-style classes.)

It is idiomatic in Lua to invoke any function that is part of a module with a colon，and you should follow this convention when writing your own code. Additionally，most API class methods should be invoked with a colon. However，there are exceptions; methods marked as "static"，or from object-independant classes (e.g. `Isaac`，`Input`，`Options`)，are not invoked with a colon.

```lua
-- This is the normal case，illustrated with the `EntityPlayer` class.
local player = Isaac.GetPlayer()
player.AddCollectible(CollectibleType.COLLECTIBLE_SAD_ONION) -- Fails because the method expects the class as the first argument.
player:AddCollectible(CollectibleType.COLLECTIBLE_SAD_ONION) -- Works.

-- This is the special case，illustrated with the `Isaac` class.
Isaac.DebugString("foo") -- Works.
Isaac:DebugString("foo") -- Fails because the method does not expect the class as the first argument.

-- Another special case is with static methods.
-- Imagine that we have a laser already，provided by the `MC_POST_LASER_UPDATE` callback.
-- Like most classes，we are supposed to use a colon.
laser.SetMaxDistance(50) -- Fails because the method expects the class as the first argument.
laser:SetMaxDistance(50) -- Works.
-- But static methods are different.
laser.ShootAngle(...) -- Works (because `ShootAngle` is a static method).
laser:ShootAngle(...) -- Fails because the method does not expect the class as the first argument.
-- Obviously，you can also invoke static methods without an instantiated class. (That's the point of them being static.)
EntityLaser.ShootAngle(...) -- Works.
EntityLaser:ShootAngle(...) -- Fails because the method does not expect the class as the first argument.
```

It can be pretty annoying to swap back and forth between using periods and colons. If this part of Lua bothers you，you can try programming mods in TypeScript using the [:material-language-typescript:IsaacScript](https://isaacscript.github.io/) framework. (In TypeScript，you invoke every function with a period，which is consistent and impossible to mess up.)

### What does the "[INFO] - [warn] item pool ran out of repicks" message mean in the "log.txt" 文件?  {: .subHeader}

This message means that the game attempted to get a new random collectible type from an item pool，but the item pool was all out of items. When an item pool is depleted like this，the game reverts to getting a random collectible from the Treasure Room pool instead，since that is the default pool. In the case that the Treasure Room pool itself was depleted，then the game will return `CollectibleType.COLLECTIBLE_BREAKFAST` instead.

If your mod is causing this message，it is likely a sign that you have a problem in your logic somewhere. Perhaps you are spawning a ton of random collectibles by accident，which would subsequently deplete the room's item pool. You might also want to examine the logic in any `MC_PRE_GET_COLLECTIBLE` or `MC_POST_GET_COLLECTIBLE` callbacks.

## Communication

These are some tips on how to improve communication.

### Read the Docs

A lot of basic questions about Isaac modding can be answered by "reading the manual". In this case，the "manual" is the unofficial community documentation website，created by famous Isaac modder Wofsauge. (The community documentation website is much better than the "normal" documentation that comes included with the game，which is incomplete，hard to search，and buggy.)

In fact，the website you are on right now is the community docs. Welcome! Use the search bar in the top right hand corner to easily look up the information you need. For example，if you wanted to know how to get the soul hearts of a player，you could search for "soul hearts"，and then you would find the `EntityPlayer.GetSoulHearts` method.

Now that you know about the docs，please remember to search the docs before asking a question in the Isaac community Discord server. By asking questions that can be easily answered by searching the docs，it is not being very respectful to the volunteers who spend their time answering questions.

### Use Discord Syntax Highlighting {: .subHeader}

When pasting code into Discord，make sure to paste it in a "code block" by using triple backticks. And make sure to use syntax highlighting for the language，by typing the name of the language next to the backticks.

=== ":material-language-lua: Lua Example"
    ````
    ```lua
    local foo = "bar"
    Isaac.DebugString(foo)
    ```
    ````

=== ":material-language-typescript: TypeScript Example"
    ````
    ```ts
    const foo = "bar";
    Isaac.DebugString(foo);
    ```
    ````

### Format Code {: .subHeader}

When asking for help，it is common to post a code-snippet. Before posting code，**please format it with an auto-formatter** so that it can be easily understood by others.

- In :material-language-lua: Lua，use [Lua Beautifier](https://goonlinetools.com/lua-beautifier/)，[LuaFormatter](https://github.com/Koihik/LuaFormatter)，or [lua-fmt](https://github.com/trixnz/lua-fmt).
- In :material-language-typescript: TypeScript，use [Prettier](https://prettier.io/).

### Avoid Posting Screenshots {: .subHeader}

When asking for help，it is common to post a screenshot of your code. **Don't do this**，because it isn't editable，or copy-pasteable，or searchable. Instead，post the actual text of the code. Also see the section on [Discord syntax highlighting](#use-discord-syntax-highlighting).

### Use Minimal，Reproducible Examples {: .subHeader}

When asking for help，it is common to post a bunch of code that is unrelated to the problem. This makes questions hard to understand and usually means that the person asking the question is putting forth very little effort.

Please read [this StackOverflow post on how to create minimal，reproducible examples](https://stackoverflow.com/help/minimal-reproducible-example).

### Avoid Using Link Previews {: .subHeader}

Link previews can clutter the conversion，turning a tiny message into a massive wall of text. It is courteous to enclose all links in <>，which will disable the feature.

For example:

```
Here's a link to my code: <https://github.com/IsaacScript/isaacscript-common/blob/main/src/functions/array.ts#L3-L16>
```
