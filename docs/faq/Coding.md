---
tags:
  - 常见问题
---

# MOD常见问题：代码

## 我要怎么理解文档?</span> {: .subHeader}

以下是一个文档中的函数的分析。

![img](../images/docs_reading_guide.png)

```lua
local player = Isaac.GetPlayer(0)
local hasTrinket = player:HasTrinket(TrinketType.TRINKET_SWALLOWED_PENNY) -- 注意，第二个参数是可选的，默认值在等号后面。
print(hasTrinket) -- 角色拥有该饰品时打印"true"，没有时打印"false"。
```

## 我要怎么做 X ？ 我要怎么写 X 的代码？ {: .subHeader}

最快的方法是下载一些提供与你想做的类似功能的 MOD，然后研究代码。在自己图复制这些小国之前，先尝试理解为什么事情会这样。

## 我在哪儿看 [某些原版道具] 或者 [某些原版机制] ？ {: .subHeader}

你不能。游戏是用 C++ 编程语言编写的，源代码不开源。

这意味着，如果你想制作一个与原版道具类似的自定义道具，你必须从头开始完全重新实现它。（您可以经常使用 wiki 作为实现参考。）

这也意味着，如果你想改变一个原版道具的工作方式，你通常必须从头开始重新实现这个道具。

## 回调是什么？ {: .subHeader}

MOD 通过将一些代码放入*回调*来修改游戏。当游戏中发生特定事件时，每个回调都会触发。有72种不同的回调可供选择，所以你必须根据你想做的事情选择正确的回调。

例如，最基本的回调是 `MC_POST_GAME_STARTED` ，它在一局新游戏开始时触发一次。您可以将代码放在这里，以在每局游戏开始时进行自定义操作。

MOD 使用的另一个常见回调是 `MC_POST_UPDATE` ，它在每个更新帧上触发（即每秒30次）。您可以将具有固定效果的自定义道具的代码放入此回调中。

浏览 [ModCallbacks 页面](../enums/ModCallbacks.md)并阅读所有回调的作用，以便熟悉它们。

## `require` 和 `include` 是什么？ {: .subHeader}

参见[使用额外 Lua 文件的教程](../tutorials/Using-Additional-Lua-Files.md).

## 我要怎么知道玩家什么时候捡到了道具？ {: .subHeader}

如果你在使用代码扩展器 [REPENTOGON](https://repentogon.com/) ，你可以使用 [MC_POST_ADD_COLLECTIBLE](https://repentogon.com/enums/ModCallbacks.html#mc_post_add_collectible) 回调。

如果你没有在使用 REPENTOGON，那么原版没有这个回调。作为一种变通方法，您可以在 PostUpdate 回调中使用 `EntityPlayer.IsItemQueueEmpty()` 检查玩家是否没有在举起道具，然后在举起道具的时候通过 `EntityPlayer.QueuedItem` 获取道具 ID。显然这对直接添加的道具不起作用。

对于 :material-language-typescript:[IsaacScript](https://isaacscript.github.io/) 使用，您可以使用 IsaacScript 提供的 [:material-language-typescript:MC_POST_ITEM_PICKUP](https://isaacscript.github.io/docs/function-signatures-custom#mc_post_item_pickup) 回调。

如果你想自己实现这个回调，[这里](https://github.com/IsaacScript/isaacscript-common/blob/main/src/callbacks/itemPickup.ts)提供了源代码/算法。

## [某个音效] 的 ID 是什么？ {: .subHeader}

如果你安装了 [REPENTOGON](https://repentogon.com/) ，你可以使用[这个 MOD](https://steamcommunity.com/sharedfiles/filedetails/?id=3190950157) ，它会显示正在播放的音效的详细信息，还有一个将他们复制到剪贴板的复制按钮。
如果你没有安装，[这个 MOD](misc/sounds-display.lua) ，它会告诉你当前播放的任意音效的 ID 是什么。


## 如何使我的自定义角色开局自带熔炼/吞下的饰品？ {: .subHeader}

如果你安装了[REPENTOGON](https://repentogon.com/)，你可以使用[角色的这个函数](https://repentogon.com/EntityPlayer.html?h=add#addsmeltedtrinket)。
没有办法通过编辑 XML 文件来完成此操作。因此，您必须手动用 Lua 代码实现这一点。


## 如何修改恶魔房/天使房的开启率？ {: .subHeader}

如果使用 [REPENTOGON](https://repentogon.com) ，你可以查看[多种恶魔房/天使房概率回调](https://repentogon.com/examples/DealChance.html).

如果没有使用，没有内置的方法可以做到这一点，所以您必须有些创造力。为了最大程度地控制开启率，你可以删除所有原版的恶魔房/天使房门，并从头开始完全重新实现恶魔房系统。或者，您可以临时将道具给予玩家，如山羊头或念珠段，或使用 [Game.SetLastDevilRoomStage()](../Level.md#setlastdevilroomstage) 或 [Level.SetRedHeartDamage()](../Level.md#setredheartdamage) 方法。您还可能需要使用 [LevelStateFlags](../enums/LevelStateFlag.md) 。

## 如何创建新的层？ {: .subHeader}

不幸的是，以撒并不支持 MOD 自定义楼层。BudJMT 和 DeadConfinity 搭建了一个名为 [StageAPI](https://github.com/Meowlala/BOIStageAPI15) 的自定义系统，这允许 MOD 以一种巧妙的方式添加自定义楼层。然而，StageAPI 并不容易使用，所以除非你已经是一个经验丰富的以撒 MOD 制作者和程序员，否则你应该坚持制作更简单的项目。

## 如何使自定义角色的人物外观永久存在？ {: .subHeader}

使用 [Sanio 的“角色外观保护器”库](https://steamcommunity.com/sharedfiles/filedetails/?id=2541362255)，或者研究源代码并自己重新实现它。

范例可以参考 [Andrew the Bunny Knight](https://steamcommunity.com/sharedfiles/filedetails/?id=2531089854) MOD。

## "log.txt" 文件中的"[INFO] - [warn] item pool ran out of repicks"消息是什么意思？ {: .subHeader}

此消息表示游戏试图从道具池中获取新的随机道具，但道具池中的道具已全部用完。当一个道具池像这样耗尽时，游戏将改为从宝箱房池中随机获取一个道具，因为这是默认的道具池。如果宝箱房池本身已耗尽，则游戏将返回 `CollectibleType.COLLECTIBLE_BREAKFAST`（早餐）。

如果你的mod导致了这条消息，这可能表明你的逻辑在某个地方有问题。也许你无意中产生了大量的随机道具，这会耗尽房间的道具池。可能还需要检查 `MC_PRE_GET_COLLECTIBLE` 或 `MC_POST_GET_COLLECTIBLE` 回调中的逻辑。