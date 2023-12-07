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

## 疑难解答

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

### Why isn't my code working? How do I know when errors occur? Where is the log.txt 文件 located? {: .subHeader}

Lua is an interpreted language，which means that if you make a typo or have otherwise bad code，you will only be able to discover it once the program actually runs. If the Lua interpreters encounters an error，it will write it to the game's log.txt 文件.

By default，this 文件 is located at:

```
文档\My Games\Binding of Isaac 忏悔\log.txt
```

Open this 文件 and search it carefully for Lua-related errors. (Ctrl + f for "error" is a good start.) This will often tell you the line number that you messed up on.

It is also recommended to set `FadedConsoleDisplay=1` in the options.ini 文件 so that it is a little bit more easy to discover errors while you play. By default，the options.ini 文件 is located at:

```
文档\My Games\Binding of Isaac 忏悔\options.ini
```

For people comfortable with command-line applications，use Zamiel's [isaac-log-viewer](https://github.com/Zamiell/isaac-log-viewer) and have it running on a second monitor as you code & test.

### When is the log.txt cleared? {: .subHeader}

Every time that you open the game，all of the contents of the log.txt is deleted. Thus，if you need information from the log after a bug occurs，make sure that you do not re-launch the game.

### How do I troubleshoot my code? {: .subHeader}

When you write programs，they may not work right away. Your first reaction should not be to paste a bunch of code into Discord and ask "why doesn't this work?". Doing that means you aren't putting forth very much effort to try and solve the problem on your own.

The tried-and-true method to figure out almost any bug is called "print debugging". In Isaac，this means printing out a bunch of messages to the log.txt 文件 so that you can view it and see which parts of your code are being executed，and which are not. So，go to a bunch of places in your code and add `Isaac.DebugString("GETTING HERE 1")`，`Isaac.DebugString("GETTING HERE 2")`，and so on. Then，run your code (i.e. walk around in-game and trigger the bug)，and study the log.txt 文件 to try and see what is happening.

Often times，the reason that your code is not working is that your variables are not what you think they are. So，print out what the variables are at each step of the way so that you can confirm that they are what you think they are. Use something along the lines of: `Isaac.DebugString("GETTING HERE - FOO IS: " .. tostring(foo))`

You might also want to use a log viewer like [this one](https://github.com/Zamiell/isaac-log-viewer).

### I modified an XML 文件 and the game crashes when I open it or when I go into a new run. {: .subHeader}

A crash means that the XML 文件 is invalid，meaning that you messed up somewhere while editing the 文件. Start over from scratch and make tiny edits one at a time until you find the exact part that crashes the game.

Another helpful troubleshooting tool is validators like [xmlvalidation.com](https://www.xmlvalidation.com/).

### I 启用 a mod and now my game is crashing. How can I fix this? {: .subHeader}

You can try looking through the log.txt 文件 to see if anything interesting is there. However，in the vast majority of cases，the log will not show any helpful information when the game crashes.

Instead，you can find the problem by disabling your mods one by one until you find the exact mod that is causing the crash. Then，you can report it to the developer of the mod，or try to manually fix the code yourself.

Note that whenever you enable or disable a mod，you should completely close and re-open the game (because the game does not load resources properly when you enable/disable a mod via the in-game menu).

### My mod is causing the game to crash. How do I figure out which line of code is causing the crash? {: .subHeader}

First，check out the log.txt 文件 for clues as to why the game is crashing. However，in the vast majority of cases，the log will not show any helpful information when the game crashes.

If you are programming your mod in Lua，then your only option is to insert a lot of print statements to try and narrow down where the crash is occurring.

If you are programming your mod in :material-language-typescript:TypeScript using the [IsaacScript framework](https://isaacscript.github.io/)，then you can use [this crash debug plugin](https://github.com/IsaacScript/isaacscript/blob/main/src/plugins/addCrashDebugStatements.ts) that will put the exact line that the mod is crashing at in the log.txt，which is extremely handy.

## Coding

### How do I do X? How do I code X? {: .subHeader}

The fastest way to figure out how to do something is to download a few mods that provide similar functionality to what you want to do，and then study the code.

### What is a callback? {: .subHeader}

Mods affect the game by putting code inside of *callbacks*. Each callback fires when a particular event happens in the game. There are 72 different callbacks to choose from，so you have to choose the right one depending on what you want to do.

For example，the most basic callback is `MC_POST_GAME_STARTED`，which fires once at the beginning of a new run. You would put code in here to do something custom at the beginning of every run.

Another common callback that mods use is `MC_POST_UPDATE`，which fires on every single update frame (i.e. 30 times per second). You would put code in this callback for custom items that have constant effects.

Go through the [ModCallbacks page](../enums/ModCallbacks.md) and read what all of the callbacks do so that you can get familiar with them.

### How do I understand the docs? {: .subHeader}

![img](../images/docs_reading_guide.png)

### What is Single Line Responsibility (SLR)? {: .subHeader}

When writing code，put some effort into making it look nice and be easy to read for others，especially if you are showing it to other people or asking for help. In this vein，it is a good idea to follow the "single line responsibility" rule - meaning that **one line** should only do **one thing**. Read [this blog](https://midu.dev/single-line-responsability-haz-una-cosa-por-linea/) for more details about why SLR is great.

### How do I apply a costume to my character? {: .subHeader}

This is called a "null costume" and it is accomplished via the `EntityPlayer.AddNullCostume()` method. For more information，see [Lytebringr's 8th video](https://www.youtube.com/watch?v=R1CdCyGL1DQ&list=PLMZJyHSWa_My5DDoTQcKCgs475xIpQHSF&index=9).

???- example "Example code"
    The follow is an example of a mod adding a null costume:

    ```lua
    local MOD_NAME = "My Mod"

    -- For EntityType.ENTITY_PLAYER (1)
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

    local mod = RegisterMod(MOD_NAME，1)

    function mod:postPlayerInit(player)
      local character = player:GetPlayerType()

      if (
        player.Variant == PlayerVariant.PLAYER
        and character == PlayerTypeCustom.FOO
      ) then
        player:AddNullCostume(NullItemIDCustom.BAR)
      end
    end
    mod:AddCallback(ModCallbacks.MC_POST_PLAYER_INIT，mod.postPlayerInit)
    ```

### How do I make the costume on my custom character persistent? {: .subHeader}

Use [Sanio's "Character Costume Protector" library](https://steamcommunity.com/sharedfiles/filedetails/?id=2541362255) for this，or study the source code and re-implement it yourself.

For a reference implementation，see [Andrew the Bunny Knight](https://steamcommunity.com/sharedfiles/filedetails/?id=2531089854).

### How do I create a new floor/level/stage? {: .subHeader}

Unfortunately，Isaac does not natively support modded custom floors. BudJMT and DeadInfinity have built a custom system called [StageAPI](https://github.com/Meowlala/BOIStageAPI15) that allows mods to add custom floors in a hacky way. However，StageAPI is not easy to use，so unless you are already an experienced Isaac modder & coder，you should stick to more simple projects.

### How do I modify the Devil Room / Angel Room chances? {: .subHeader}

There is no built-in way to do this，so you will have to get inventive. For the most control，you can delete all vanilla Devil/Angel doors and completely re-implement the system from scratch. Otherwise，you can temporarily give items to the player such as Goat Head or Rosary Bead，or use things like [Game.SetLastDevilRoomStage()](../Level.md#setlastdevilroomstage) or [Level.SetRedHeartDamage()](../Level.md#setredheartdamage). You also might want to use [LevelStateFlags](../enums/LevelStateFlag.md).

### How do I get a familiar to follow the player like Brother Bobby does? {: .subHeader}

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

### How do you use StageAPI to add new bosses? {: .subHeader}

This is an example code snippet from Xalum:

```lua
mod.StageAPIBosses = {
    StageAPI.AddBossData("The Baron"，{
        Name = "The Baron",
        Portrait = "gfx/bosses/baron/portrait_baron.png",
        Bossname = "gfx/bosses/baron/name_baron.png",
        Rooms = StageAPI.RoomsList("BaronBossRooms"，include("resources.luarooms.boss_baron"))
    }),

    StageAPI.AddBossData("High Amon"，{
        Name = "High Amon",
        Portrait = "gfx/bosses/amon/portrait_amon.png",
        Bossname = "gfx/bosses/amon/name_amon.png",
        Rooms = StageAPI.RoomsList("AmonBossRooms"，include("resources.luarooms.boss_amon"))
    }),
}

StageAPI.AddBossToBaseFloorPool({BossID = "The Baron"，Weight = 1.5}，LevelStage.STAGE3_1，StageType.STAGETYPE_胎衣)
StageAPI.AddBossToBaseFloorPool({BossID = "High Amon"，AlwaysReplaceSubtype = 83，OnlyReplaceSubtype = 83}，LevelStage.STAGE2_1，StageType.STAGETYPE_忏悔_B)
```

### How do I make my custom character start with a smelted / gulped trinket? {: .subHeader}

You cannot do this via editing the XML 文件. Thus，you must accomplish this via Lua or TypeScript code.

### How do I know when a player has picked up a collectible item? {: .subHeader}

There is no vanilla callback for this. As a workaround，you can check `EntityPlayer.IsItemQueueEmpty()` on every PostUpdate frame，and then check `EntityPlayer.QueuedItem` when it is not empty. Obviously，this will not work for items that never get queued.

For :material-language-typescript:[IsaacScript](https://isaacscript.github.io/) users，you can use the provided [:material-language-typescript:MC_POST_ITEM_PICKUP](https://isaacscript.github.io/docs/function-signatures-custom#mc_post_item_pickup) callback.

If you want to implement this callback yourself，the source code / algorithm is provided [here](https://github.com/IsaacScript/isaacscript-common/blob/main/src/callbacks/itemPickup.ts).

### How do you tell what the entity type，variant，or subtype of a particular entity is? {: .subHeader}

You can:

1. Type "spawn x" into the in-game console. For example，"spawn confessional" would show that the Confessional entity has an identifier of 6.17. This means that it has an entity type of 6 and a variant of 17.
2. Or，you can ctrl+f in the "resources-dlc3/entities2.xml" 文件 for the entity you want.

### How do I blindfold the player? {: .subHeader}

=== ":material-language-lua: Lua"
    ```lua
    --- Written by Zamiel，technique created by im_tem
    -- @param player EntityPlayer
    -- @param 启用 boolean
    -- @param modifyCostume boolean
    function setBlindfold(player，启用，modifyCostume)
      local game = Game()
      local character = player:GetPlayerType()
      local challenge = Isaac.GetChallenge()

      if 启用 then
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
    If you are using [:material-language-typescript:IsaacScript](https://isaacscript.github.io/)，then all you have to do is call the `setBlindfold` function，like so:

    ```ts
    const player = Isaac.GetPlayer();
    setBlindfold(player，true);
    ```

### What is the 区别 between an API and a library? {: .subHeader}

Some mods on the workshop package functionality together as an abstraction for other people to use. In software，this is what is typically known as a "library". As a programmer，it is usually a lot easier to leverage other people's battle-tested libraries than to roll your own from scratch.

On the other hand，an API is short for application programming interface，and it is exactly what it sounds like. An application might want to expose some functionality to external users and software，and it would do that through an explicitly defined interface. Libraries expose an API so that end-users can consume them. But note that *any* software can have an API，not just a library. For example，the Revelations Mod is a popular mod that adds new floors，bosses，and items to the game. But it also exposes an API so that it can be made compatible with other mods.

Historically，Isaac libraries have labeled themselves as "APIs"，but this is a misnomer. Some examples of this include [StageAPI](https://github.com/Meowlala/BOIStageAPI15) and [MinimapAPI](https://github.com/TazTxUK/MinimapAPI). On the other hand，an example of a library that is correctly named is Sanio's [Character Costume Protector](https://steamcommunity.com/sharedfiles/filedetails/?id=2541362255).

If you are creating a new library，please use the correct terminology to name your project，which helps prevent confusion for newcomers to the Isaac modding scene.

### What is a micro-optimization? Should I optimize my mod? {: .subHeader}

#### Definition

As programmers，we are often concerned with the speed of our programs.

When beginner programmers start to think about "performance"，they often make bad adjustments to their code in the hopes that it will speed it up. These are called [micro-optimizations (or premature optimizations)](https://wiki.c2.com/?PrematureOptimization). For example，a beginner might start with some code that is neatly organized into separate functions，like this:

```lua
local function main()
  -- Do some stuff with foo
  foo()

  -- Do some stuff with bar
  bar()
end

local function foo()
  -- TODO
end

local function bar()
  -- TODO
end
```

In the previous code，we have two functions that are small，named well (theoretically)，and are easy to read and understand. But a beginner might be tempted to transform the code to this:

```lua
local function main()
  -- Do some stuff with foo
  -- TODO

  -- Do some stuff with bar
  -- TODO
end
```

The idea here is that since we got rid of two function calls，the program should *theoretically* speed up. (Because under the hood，what functions do when they are called is put values on the stack，and then pop them back off of the stack when they are done.)

But in reality，compilers can often optimize the code to perform this speed-up automatically (without the programmer having to actually modify their source code). So in this case，the beginner programmer is making their source code worse in exchange for byte-code that will run identically. Bad!

Furthermore，even if the compiler does not optimize the function call automatically，the simple act of calling a function can happen in few short nanoseconds. You would never be able to meaningfully measure a 区别 in the run-time performance of the program with a few extra function calls. So it's still the same as before: the beginner programmer is making their source code worse for no measurable benefit.

Micro-optimziation is a trap that many beginners fall into. The time spent on performing micro-optimizations should instead be spent on measuring *real* bottlenecks in the code，and then optimizing those. Or fixing real bugs! Or adding real features!

This is the reason why programmers have the maxim: "Premature optimization is the root of all evil." It comes from [Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth)，who is one of the most renown computer scientests of all time. In his paper "[Structured Programming with go to Statements](https://pic.plover.com/knuth-GOTO.pdf)"，he famously writes:

> Programmers waste enormous amounts of time thinking about，or worrying about，the speed of noncritical parts of their programs，and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget about small efficiencies，say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%.

#### Measuring

In the example above，the beginner programmer assumed that removing function calls would speed up the program. But these kinds of assumptions could be about any type of code，not just function calls. You might "know" that coding in a certain way will be faster than in another way.

But in real life programs，it is **extremely difficult** to predict what kinds of code transformations will actually affect the performance of the program. Sometimes，you can make a change that you think will speed up the program，but it really makes it slower! And sometimes，you can make a change that you think will make the program slower，but it really speeds it up! The compiler does all kinds of crazy things under-the-hood.

This is why when we talk about optimization，the most important thing to discuss is **measuring**. Measuring the run-time of a piece of code is calling profiling. (It can also be called benchmarking.)

Memorize the **[three rules of optimization](https://wiki.c2.com/?RulesOfOptimization)** from the C2 wiki:

1. Don't.
2. Don't... yet.
3. Pro文件 before optimization.

The idea behind these 3 rules is that in real life programs，you almost never need to optimize. But if you really do，you **must** measure both before and after. Based on what you measure，it will tell you if the code change is worth the costs of making the code longer，more complicated，or harder to understand. Sometimes，it will be worth it. But often，it won't.

#### Code Clarity

So，if you should not generally be concerned with performance，what should you be concerned with? The answer is code clarity.

First and foremost，the goal of code is to make it neat and easy to read for others. (And even if you are writing code that is never going to be read by anyone else，you should still make it neat and easy to read for future-you，who might have to read this code months or years from now and have to figure out what it does in order to fix some bug.)

You might think it is silly to rank "code clarity" as being more important than having "code that works". And that's certainly debatable. But consider this:

- Code that doesn't work，but is easy to understand，can be modified to be made to work.
- Code that works，but is indecipherable，is going to be very difficult to modify. And this means that we probably can't fix any bugs or add new features.

One of the key insights of [Guido van Rossum](https://en.wikipedia.org/wiki/Guido_van_Rossum)，the creator of the [Python](https://www.python.org/) programming language，was that [code is read much more often than it is written](https://www.python.org/dev/peps/pep-0008/). Python was designed to be concise，clean，and readable. It had standard ways of doing things and recommends that everyone follow the [PEP-8 coding standard](https://www.python.org/dev/peps/pep-0008/). Now，Python is the [most popular programming language in the world](https://pypl.github.io/PYPL.html). The readability of the code isn't the *only* reason for Python's rise，but it is one of the more important ones.

## Lua

### How do I iterate over a list object from the API? {: .subHeader}

For example，in Lua:

=== ":material-language-lua: Lua"

    ```lua
    local game = Game()
    local level = game:GetLevel()
    local rooms = level:GetRooms()
    for i = 0，rooms.Size - 1 do
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

for key，value in pairs(map) do
  print(key) -- Prints foo，baz
  print(value) -- Prints bar，123
end
```

```lua
local array = {
  123,
  456,
  789,
}

for i，element in ipairs(array) do
  print(i) -- Prints 1，2，3
  print(element) -- Prints 123，456，789
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
foo.bar(foo，arg1，arg2)
foo:bar(arg1，arg2)
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
